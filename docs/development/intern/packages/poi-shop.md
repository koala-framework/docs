#POI-SHOP

Besteht aus Zubehör (PoiShop_Kwc_Accessories_Component) und E-Shop (PoiShop_Kwc_EShop_Component). Beide Komponenten sind durch hinzufügen als Seitentyp einsatzbereit, in der config muss noch poi.autoZ.brand gesetzt werden. Die Daten werden fast ausnahmslos bei jedem Aufruf live von der POI geholt.

Beim Zubehör kann man sich nach Auswahl des Modells das verfügbare Zubehör ansehen und beim Händler vormerken lassen.

Der E-Shop stellt einen Shop mit Bestellvorgang zur Verfügung (der Bestellvorgang wird auch über die POI abgewickelt).

Das Setting poi.autoZ.domain überprüfen, bei prod gehen Bestellungen tatsächlich raus, bei qa sind die Testdaten meist ohne Bilder und lückenhaft.


##Changelogs

###2.0

* Alle Templates mit Twig und BEM gemacht
* Bilder zu Kategorien und Kollektionen über Admin wartbar

###1.0