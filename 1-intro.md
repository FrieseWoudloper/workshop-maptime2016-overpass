## Wat je vooraf moeten weten over OpenStreetMap
- OpenStreetMap kent drie soorten objecten: nodes, ways and relations.
- Een [node](http://wiki.openstreetmap.org/wiki/Node) is een punt. Een node heeft een id, latitude en longitude.
- Een [way](http://wiki.openstreetmap.org/wiki/Way) is een geordende lijst van nodes. Een way kan een lijn of vlak voorstellen.
- Een [relation](http://wiki.openstreetmap.org/wiki/Relation) is een geordende lijst van nodes, ways of relations. Een relation wordt gebruikt om een logische of geografische relatie aan te geven, bijvoorbeeld een bestuurlijke grens, buslijn of wandelroute.
- Aan een node, way of relation zijn tags gekoppeld. Met een [tag](http://wiki.openstreetmap.org/wiki/Tags) voeg je betekenis toe. Een tag bestaat uit een sleutel en bijbehorende waarde, bijvoorbeeld `amenity = post_box`.
- Welke tags er al zijn en hoe je ze het beste gebruikt, kun je opzoeken in de [OpenStreetMap Wiki](http://wiki.openstreetmap.org/wiki/Main_Page) of op [Taginfo](http://taginfo.openstreetmap.org/). 

## Wat is Overpass API?
* Overpass API is een interface voor het bevragen van de OpenStreetMap database.
* Je hoeft geen software te installeren of OSM-bestanden te downloaden. Je stelt je vraag en krijgt het antwoord via het web.
* Het is alleen mogelijk om gegevens in OpenStreetMap te lezen, niet om ze te wijzigen.
* Overpass API is vooral handig als je gegevens wilt filteren, bijvoorbeeld op objecttype, locatie of tag.
* Voor het bevragen heb je de keuze uit twee query-talen: [Overpass XML](http://wiki.openstreetmap.org/wiki/Overpass_API/Language_Guide) en [Overpass QL](http://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL). In deze workshop gebruiken we Overpass QL.
* Ontwikkelaars maken gebruik van het API endpoint: http://overpass-api.de/api/
* In de workshop gebruiken we de Overpass turbo IDE: http://overpass-turbo.eu/

![overpass api logo](images/logo-overpass-api.png)

[Volgende](2-filteren.md)

