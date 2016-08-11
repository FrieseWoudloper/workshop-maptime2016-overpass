## GeoJSON-exportbestand
Het is mogelijk om in Overpass Turbo het zoekresultaat te exporteren naar GeoJSON. Kies in het menu voor _Exporteren_ - _Data_ - _as GeoJSON_.  
Het GeoJSON bestand kun je vervolgens bijvoorbeeld in QGIS of op [www.geojson.io](http://www.geojson.io) bekijken.

## QuickOSM plugin voor QGIS
Als je de zoekresultaten verder wilt analyseren of visualiseren in QGIS kun je zoals gezegd gebruik maken van een GeoJSON-exportbestand.  
Je kunt er echter ook voor kiezen om de [QuickOSM plugin](https://plugins.qgis.org/plugins/QuickOSM/) te installeren in QGIS. QuickOSM is net als Overpass Turbo een frontend voor de Overpass API. De plugin is – in tegenstelling tot Overpass Turbo – volledig geïntegreerd in QGIS.  

## Up-to-date gegevens tonen in Leaflet
[Alex Morega](https://github.com/mgax) laat in [cafes.html](https://github.com/mgax/workshop-geocj2015-overpass/blob/master/cafes.html) zien hoe je met behulp van de [Leaflet](http://leafletjs.com/) en [osmtogeojson](http://tyrasd.github.io/osmtogeojson/) JavaScript libraries zoekresultaten van Overpass API in een viewer kunt tonen. Iedere keer als de kaartlaag wordt ingeladen, worden de gegevens opnieuw opgevraagd bij Overpass API. Dit betekent dat de gegevens in de viewer altijd up-to-date zijn. Bekijk Alex' viewer [hier](https://rawgit.com/mgax/workshop-geocj2015-overpass/master/cafes.html).

## Zoeken vanaf de command line
Het is mogelijk om met tools als [```wget```]() of [```curl```]() vanaf de command line een zoekopdracht uit te voeren en de resultaten automatisch te downloaden. Hiervoor moet je de zoekopdracht converteren naar _compact Overpass QL_. Dat kan eenvoudig door in Overpass Turbo in het menu te kiezen voor _Exporteren_ - _Bevraging_ - _convert to (compact) Overpass QL_.  

In onderstaand voorbeeld worden café's in de stad Groningen opgevraagd en weggeschreven naar het bestand cafes-in-groningen-stad.osm.
Let op: omdat de aanroep van de Overpass API tussen aanhalingstekens staat, moet je voor de aanhalingstekens _binnen_ de aanroep een escape character (```\```) zetten.

```
wget -O cafes-in-groningen-stad.osm "http://overpass-api.de/api/interpreter?data=area[\"name\"=\"Groningen\"][\"admin_level\"=\"10\"];node[\"amenity\"=\"cafe\"](area);out body;"
```

Meer informatie over het uitvoeren van zoekopdrachten vanaf de command line vind je [hier](http://www.overpass-api.de/command_line.html)  

## Meer Overpass QL voorbeelden
Op de pagina []Overpass API by Example](http://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_API_by_Example) in de OpenStreetMap wiki vind je meer voorbeelden van zoekopdrachten in Overpass QL.