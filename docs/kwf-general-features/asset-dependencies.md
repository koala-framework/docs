#ASSETS AND DEPENDENCIES

In Koala Framework JavaScript files and Css files are loaded through dependencies.

For better performance all individual files are combined in a single one, large, file - 
that contains all JavaScript or Css code required. (one for JS, one for Css)

##Add dependencies

`dependencies.ini `:

    [dependencies]
    Frontend.files[] = kwf/css/web.css
    Frontend.files[] = kwf/css/web.printcss
    Frontend.files[] = web/css/master.css
    Frontend.files[] = web/css/web.css
     
    Frontend.dep[] = Components
     
    Admin.dep[] = Frontend
    Admin.dep[] = ComponentsAdmin
    Admin.dep[] = KwfComponent
    
    
It's important to add the default values if you want to add additional dependencies because the default value 
gets resetted if you just add another one. You can find them on the last few lines in kwf/dependencies.ini.

Frontend.XXX is used for dependencies only needed for frontend and Admin.XXX for backend.

The line Admin.dep[] = Frontend enables everything from frontend also in backend because it will probably be shown 
in backend-preview.

XXX.files[] is used to relate files to dependency XXX

XXX.dep[] is used to relate dependencies to dependency XXX    

