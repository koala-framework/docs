#CONFIGURE MASTER LAYOUT

`themes/Theme/Component.php:`

     $ret['masterLayout'] = array(
                'class' => 'Susy_MasterLayout',
                'layoutConfig' => 'web/themes/Theme/layout.config.scss',
                'layoutName' => 'default',
            );
            
`themes/Theme/layout.config.scss `     
     
     $master-layouts: (
         default: (
             sm: (
                 layout: (
                     container: auto,
                     columns: 12,
                     gutter: 0.5
                 ),
                 content-spans: 12,
                 box-spans: (
                     mainMenu: 12
                 )
             ),
             md: (
                 layout: (
                     container: auto,
                     columns: 12,
                     gutter: 0.2
                 ),
                 breakpoint: 640px,
                 no-mediaqueries: true,
                 content-spans: 12,
                 box-spans: (
                     mainMenu: 6
                 )
             ),
             lg: (
                 layout: (
                     container: 1280px,
                     columns: 12,
                     gutter: 0.3
                 ),
                 breakpoint: 1024px,
                 no-mediaqueries: true,
                 content-spans: 12,
                 box-spans: (
                     logo: 6
                 )
             )
         )
     );