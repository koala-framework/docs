#CREATE PDF WITH DOMPDF

Dompdf is a library to generate PDF from HTML code. Examples can be found at [http://pxd.me/dompdf/www/examples.php](http://pxd.me/dompdf/www/examples.php).

In the following example we use twig for the html template and a php-script 
that initiates the rendering of an pdf via dompdf. We also use a custom font.


##Template example

    <html>
    <head>
        <style>
            @font-face {
                font-family: yourfont;
                src: url(vendor/bower_components/yourFont-fonts/fonts/yourFont.ttf);
            }
            @page {
                margin: 2cm;
            }
            body {
                text-align: center;
                font-family: yourfont;
            }
            hr {
                page-break-after: always;
                border: 0;
            }
        </style>
    </head>
    <body>
        {% if twiglogo %}
            <img src="{{ twiglogo }}" alt="Logo"/>
        {% endif %}
        <p>{{ sometext }}</p>
    </body>
    </html>
    
    
##PHP Snippet
   
    class Pdf_RetrainingConfirmation implements Kwf_Media_Output_Interface
       {
           public static function getMediaOutput($id, $type, $className)
           {
               define("DOMPDF_ENABLE_AUTOLOAD", false);
               require_once('vendor/dompdf/dompdf/dompdf_config.inc.php');
        
               $twig = new Kwf_View_Twig_Environment();
               $imagesource = 'http://sourceurl for some image';
               $html = $twig->render('app/Pdf/RetrainingConfirmation.twig', array(
                   'twiglogo' => $imagesource,
                   'sometext' => 'sometext'
               ));
        
               $dompdf = new DOMPDF();
               $dompdf->set_paper('a4');
               $dompdf->load_html($html);
               $dompdf->render();
        
               $output = $dompdf->output();
               $filename = 'yourFileName.pdf';
               file_put_contents($filename, $output);
        
               return array (
                   'contents' =>  $output,
                   'mimeType' => 'application/pdf',
                   'lifetime' => false,
                   'downloadFilename' => $filename
               );
           }
       }   
       
       
##Custom Fonts
      
f you use a custom font, as in the example, reverence to that font with font-face in CSS as we did above. 

####How to add a font
To add a custom font, it is recommend to load it via composer. If there is no composer-package for the 
desired font but you have the fontfile, than you can make an repository for the font and load it with composer, 
[see this article](../development/intern/private-fonts-repository.md).


Not recommend but possible is to simple make an "font" folder at rootlevel and copy your fontfile into it and 
reference to that fontfile.

For other ways to add a font see dompdf documentation and/or following usefull links:

* [http://our-knowledge-base.blogspot.co.at/2012/05/how-to-change-font-family-in-dompdf.html](http://our-knowledge-base.blogspot.co.at/2012/05/how-to-change-font-family-in-dompdf.html)

* [http://pxd.me/dompdf/www/fonts.php](http://pxd.me/dompdf/www/fonts.php)


##Important to know

* Use "font" property instead of "font-family" in CSS, or it may not work.
* Don't use `$dompdf->output()` and `$dompdf->stream()` together, it may crash your font.
* to develop/debug your pdf, add `"echo $html;"` before `$dompdf->new DOMPDF();` and the browser will show the html-version 
    of the pdf.
    
#IMAGES SCALING AND CACHING

Dompdf doesn't scale images, instead it embeds the origin image into the pdf. This can generate big pdf's, 
depanding on the imagesize. To get the pdf filesize as small as possible, we have to scale it with the scale() function 
from the `Kwf_Media_Image Class`. Then we get an imageblob that we have to encode to base64 to embed it in our template.

###Example:

    $imageBlob = Kwf_Media_Image::scale($honorLogo, array('width' => 200, 'height' => 200, 'cover' => false));
     
    $imageBase64 = base64_encode($imageBlob);
     
    $mimeType = 'image/png';
     
    $src = 'data:'.$mimeType.';base64,'.$imageBase64;
    
For caching see [this link](caching/caches.md).


#GOOD TO KNOW

* After changing the Template, a "ccb" is needed. Without ccb, changes will not get recognized.
* If you use tables are used in a Template, most of the time "border-collapse: collapse;" is very usefull. 
Otherwise we get an unexpected height of the table.
* Also don't give height as percentage on elements without parents that have a fixed height, dompdf will fail 
compiling the template.