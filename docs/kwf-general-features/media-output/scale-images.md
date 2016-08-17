#SCALE IMAGES KWF_MEDIA_IMAGE

This class provides a easy to use but still powerful way to scale images.

`Kwf_Media_Image::calculateScaleDimensions($source, $targetSize)`: returns the size of the scaled image

`Kwf_Media_Image::scale($source, $targetSize)`: returns the contents of the scaled image

`Kwf_Media_Image` also correctly converts CMYK images to RGB, strips unneded data and rotates image according to exif data.


`$targetSize` parameter must be an array with the following entries:

* ` cover`: the used scaling method, see below
* ` width / height`: the desired target size
* `aspectRatio`: (optional) the desired aspect ratio, if width or height is 0

if width or height is 0 and aspectRatio not used the target size will be calculated using the ratio of the original image.
possible scaling methods:

* `cover=true`: The resulting image will always cover the specified width and height, the image will be cropped if necessary (similar to css background-size: cover)
* `cover=false`: The resulting image size will be inside the given width & height constraints