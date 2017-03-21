#MEDIA OUTPUT

_This is section about manual output of media (usually images). 
In most cases `Kwc_Basic_Image_Component` can be used. (in component based webs)_

To output resized images or other media you can use `Kwf_Media`.

As the output itself happens in a different request this is split into two parts:

###1. Generating a media Url

###2. Generating the media output (different http request)

To create your own output method implement the interface `Kwf_Media_Output_Interface` in a class - 
commonly model classes are used.

Then generate the media url using: `Kwf_Media::getUrl($class, $id, $type, $filename)`

The parameters `$id` and `$type` can contain *any* string, it will be passed unchanged to the output method. 
Usually `$id` is some a primary key of a model and `$type` the image size (as in small/large/etc). `$filename`
is just for decoration - used by the browser if you save the file.

`$class` is the class that implements `Kwf_Media_Output_Interface`.

The generated url is dispatched by `Kwf_Setup::dispatchMedia()` into the given 
`$class::getMediaOutput($id, $type, $className)` where you can then return the processed (scaled) image.

Use `Kwf_Media_Image::scale` for scaling.

A typical getMediaOutput method looks like that:

    public static function getMediaOutput($id, $type, $className)
        {
            $row = Kwf_Model_Abstract::getInstance('Products')->getRow($id);
            if ($type == 'mini') {
                $dim = array(0, 13);
            } else if ($type == 'small') {
                $dim = array(150, 150);
            }
            $uploadRow = $row->getParentRow('Image');
            if (!$uploadRow) return null;
            return array(
                'contents'=>Kwf_Media_Image::scale($uploadRow, $dim),
                'mimeType' => $uploadRow->mime_type
            );
        }
        
##Possible return values
        
You have to return an array which contains one of the following values:

* contents (a string containing the file)
* file (a path to a file)

There are several optional values:

* mtime (used for Last-Modified and 304 responses)
* etag (used for ETag and 304 responses)
* lifetime (lifetime >1 causes Cache-Control public with max-age=lifetime, defaults to 24h)
* downloadFilename (Content-Disposition: attachment, used to force a download with given filename)
* filename (Content-Disposition: inline)
* encoding (can be gzip or deflate if the contents is already encoded)   
     
     
##Caching

Scaling images can be very expensive so `Kwf_Media` caches by default. To disable caching return `'lifetime' => false`. 
To clear the cache (once it's contents changed) use `Kwf_Media::clearCache($class, $id, $type)`.

##Security

All media urls are secured by a hash that makes it impossible to fetch images koala didn't create the url for. 
(eg. by incrementing the id).

Additional security can be implemented by implementing the `Kwf_Media_Output_IsValidInterface` interface where you can 
dynamically check if the image is still valid or the current logged in user has permissions. 
Implement `isValidMediaOutput($id, $type, $className)` and return one of the following:

* `Kwf_Media_Output_IsValidInterface::VALID`: url is valid, this call is cached for one hour
* `Kwf_Media_Output_IsValidInterface::VALID_DONT_CACHE`: url is valid but don't cache it because it's eg. 
* only valid for the currently logged in user
* `Kwf_Media_Output_IsValidInterface::INVALID`: results in a 404 Not Found response
* `Kwf_Media_Output_IsValidInterface::ACCESS_DENIED`: results in a 401 Access Denied response