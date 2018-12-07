# Google Maps
If you want to make it configurable through the backend use `Kwc_Advanced_GoogleMap_Component`, else you can use  `Kwc_Advanced_GoogleMapView_Component`.

## Available Configuration
`mapContainer` and either `coordinates` or `latitude` and `longitude` must be specified. All other properties are optional. 

| Variable | Description |
|----------|-------------|
| `mapContainer` | The wrapper element of the map (id, dom-element or jquery-element). Must contain a div with class 'container', where the google map itself will be put into. |
| `width` | The width of the map container in pixel. If not set, full width is used. |
| `height` | The height of the map container in pixel. |
| `longitude` | The longitude of the initial center point |
| `latitude` | The latitude of the initial center point |
| `coordinates` | The longitude and latitude of the initial center point. E.g.: '47.802594,13.0433173'|
| `markers` | An object of one marker, an array of markers or a an url (string) to load markers on demand. Longitude and latitude, or coordinates are mandatory. See the following example: `[ { longitude: 47.802594, latitude: 13.0433173, infoHtml: 'Text 1' }, { coordinates: '46.1234,12.321', infoHtml: 'Text 2' } ]`|
| `markerSrc` | An url to an image that should be used as marker |
| `lightMarkers` | An object of one marker or an array of markers. Markers at these positions will have another marker color. |
| `lightMarkerSrc` | An url to an image that should be used as light marker. |
| `singleMarkerZoom` | Zoom if only one marker is set. Defaults to 15. |
| `zoomControl` | boolean: true to show large zoom controls. Defaults to true. |
| `zoomControlPosition` | Identifiers used to specify the placement of controls on the map. See [API-Ref](https://developers.google.com/maps/documentation/javascript/reference/control#ZoomControlOptions). |
| `zoom` | The initial zoom value. Either an integer, an array of longitude / latitude values that should be visible in the map or null. If null all existing markers are centered. Default value for zoom is 13. Example for array usage: [ top, right, bottom, left ] |
| `mapTypeControl` | boolean: true to show the [MapTypeControl](https://developers.google.com/maps/documentation/javascript/reference/map#MapOptions.streetViewControl).|
| `mapType` | [Map-Type](https://developers.google.com/maps/documentation/javascript/reference/map#MapOptions.mapTypeId), defaults to `roadmap`. |
| `streetViewControl` | boolean: true if StreetViewControl should be enabled. See: [API-Ref](https://developers.google.com/maps/documentation/javascript/reference/map#MapOptions.streetViewControl)|
| `clickableIcons` | boolean: true if POIs should be clickable. See: [API-Ref](https://developers.google.com/maps/documentation/javascript/reference/map#MapOptions.clickableIcons)|
| `scrollwheel` | boolean: If false, disables zooming on the map using a mouse scroll wheel.|

## Recommended Usage
* Consider using a [Static Map](https://developers.google.com/maps/documentation/maps-static/intro) if the map is used as an image or [Embedded Maps](https://developers.google.com/maps/documentation/embed/start) if only location information is displayed as they are free of charge.
* Disable StreetView with `streetViewControl=false` and POI-Information with `clickableIcons=false`.
* Set [API-Key restrictions](https://developers.google.com/maps/documentation/javascript/get-api-key#key-restrictions) to prevent abuse.
* Set [billing limits and alerts](https://cloud.google.com/billing/docs/how-to/budgets).
* Limit the information returned by the API with e.g. setting the [fields](https://developers.google.com/places/web-service/details#fields) parameter.
* Use [sessionToken](https://developers.google.com/places/web-service/details#session_tokens) if possible.
* Prefer the usage of [Autocomplete](https://developers.google.com/maps/documentation/javascript/places-autocomplete#video) over [SearchBox](https://developers.google.com/maps/documentation/javascript/reference/places-widget#SearchBox) as SearchBox does not allow to restrict the information requested.

## Sample Implementation
This implemenation is using a GooogleMap along Autocomplete for searching. Furthermore AutocompleteService and PlacesService are used to catch a user pressing enter and selecting the first recommendation and getting its location. 

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













