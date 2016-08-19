#ELEMENT FÜR DESKTOP MIT ELEMENT IN MOBIL ERSETZEN

Beispiel mit **DesktopBtn** und **MobileBtn**

###Desktop Btn:

Klasse "onlyHideOnMobile" geben

    <td class="onlyHideOnMobile" width="100%">
        <?=$this->component($this->desktopBtn);?>
    </td>


###MobileBtn:

auf MobileBtn die Klasse onlyShowOnMobile setzen. Hierzu kommt noch ein inline-style damit Gmail und lotus notes den MobileBtn in Desktop ausblenden. Wobei hier für lotus notes und gmail mit width 0, height 0, overflow hidden und display block der Button ausgeblendet werden muss (Gmail entfernt display none). Weiters kommt ein if mso für ältere Outlooks dazu was den Button ebenfalls entfernt da hier beide Varianten zum ausblenden nicht funktionieren.

    <!--[if mso]><!-->
    <tr>
        <td class="responsiveButton onlyShowOnMobile" valign="top" align="left" style="width: 0px; height: 0px; overflow: hidden; display: block; display: none;">
            <? if ($this->hasContent($this->mobileBtn)) { ?>
            <?=$this->component($this->mobileBtn);?>
            <? } ?>
        </td>
    </tr>
    <!--<![endif]-->
    
    
    
Dann noch das CSS dazu:

    @media (max-width: 490px) {
        .responsiveButton {
            overflow: visible !important;
            height: auto !important;
            width: auto !important;
        }
     
        .onlyShowOnMobile {
            display: block !important;
            width: 100% !important;
        }
     
        .onlyHideOnMobile {
            display: none !important;
        }
    }