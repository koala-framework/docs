# Google Maps
If you want to make it configurable through the backend use `Kwc_Advanced_GoogleMap_Component`, else you can use `Kwc_Advanced_GoogleMapView_Component`. To use Google Maps without a component, use the loader (`commonjs/google-map/loader.js`) and the Google Maps API directly. 

## Recommended Usage
* Consider using a [Static Map](https://developers.google.com/maps/documentation/maps-static/intro) if the map is used as an image or [Embedded Maps](https://developers.google.com/maps/documentation/embed/start) if only location information is displayed as they are free of charge.
* Disable StreetView with `streetViewControl=false` and POI-Information with `clickableIcons=false`.
* Set [API-Key restrictions](https://developers.google.com/maps/documentation/javascript/get-api-key#key-restrictions) to prevent abuse.
* Set [billing limits and alerts](https://cloud.google.com/billing/docs/how-to/budgets).
* Limit the information returned by the API by e.g. setting the [fields](https://developers.google.com/places/web-service/details#fields) parameter.
* Use [sessionToken](https://developers.google.com/places/web-service/details#session_tokens) if possible.
* Prefer the usage of [Autocomplete](https://developers.google.com/maps/documentation/javascript/places-autocomplete#video) over [SearchBox](https://developers.google.com/maps/documentation/javascript/reference/places-widget#SearchBox) as SearchBox does not allow to restrict the information requested.

## Sample Implementation
This implemenation is using the loader (commonjs/google-map/loader.js) to load the Google Maps library. Autocomplete is used for searching and AutocompleteService and PlacesService are used to catch a user pressing enter and selecting the first recommendation and getting its location. 

    gmapLoader((function() {
        var sessionToken = new google.maps.places.AutocompleteSessionToken();
        var ac = new google.maps.places.Autocomplete($queryField.get(0), {
            types: ['geocode'],
            componentRestrictions: { country: $queryField.data('country') },
            fields: ["name", "geometry.location"]
        });

        var acs = new google.maps.places.AutocompleteService();
        var ps = new google.maps.places.PlacesService($queryField.get(0));

        google.maps.event.addDomListener($queryField.get(0), 'keydown', (function(e) {
            if (e.keyCode === 13) e.preventDefault();
        }).bind(this));

        ac.addListener('place_changed', (function () {
            var place = ac.getPlace();
            if (!place || !place.name) {
                this.clearValue();
            } else if (place.geometry) {
                this.changeLocation(place.geometry.location);
            } else {
                acs.getPlacePredictions({
                    input: place.name,
                    types: ['geocode'],
                    componentRestrictions: { country: $queryField.data('country') },
                    sessionToken: sessionToken
                }, (function(predictions, status) {
                    if (status === 'OK' && predictions[0]['place_id']) {
                        ps.getDetails({ placeId: predictions[0]['place_id'], fields: ["geometry.location"], sessionToken: sessionToken }, (function(result, status) {
                            if (status === 'OK') this.changeLocation(result.geometry.location);
                        }).bind(this));
                    }
                }).bind(this));
            }
        }).bind(this));
    }).bind(this));
