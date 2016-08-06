## Wat is Overpass API?

* Overpass API is een interface voor het bevragen van de OpenStreetMap database.
* Je hoeft geen software te installeren of OSM-bestanden te downloaden. Je stelt je vraag en krijgt het antwoord via het web.
* Het is alleen mogelijk om gegevens in OpenStreetMap te lezen, niet om ze te wijzigen.
* Overpass API is vooral handig als je gegevens wilt filteren, bijvoorbeeld op objecttype, locatie of tag.
* Voor het bevragen heb je de keuze uit twee query-talen: [Overpass XML](http://wiki.openstreetmap.org/wiki/Overpass_API/Language_Guide) en [Overpass QL](http://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL). In deze workshop gebruiken we Overpass QL.
* Ontwikkelaars maken gebruik van het API endpoint: http://overpass-api.de/api/
* In de workshop gebruiken we de Overpass turbo IDE: http://overpass-turbo.eu/

![overpass api logo](images/logo-overpass-api.png)

## Wat je vooraf moeten weten over het OpenStreetMap datamodel
- OpenStreetMap kent drie soorten objecten: nodes, ways and relations.
- Een node is een punt (coördinaten).
- Een way is een lijst met nodes (zonder coördinaten). Een way kan een lijn of vlak voorstellen.
- Een relation is een lijst met nodes, ways of relations en wordt gebruikt om een onderlinge samenhang te modelleren. 
- Aan een node, way of relation zijn tags gekoppeld. 


	
Mapping The OpenStreetMap data model
The OpenStreetMap data model

In OpenStreetMap, each feature is described as one or more geometries (think for instance of a river’s shape) with attached attribute data (think of the river’s name). Geometries are described with three different elements: nodes, ways and relations. Attributes are described as tags that can be part of a node, a way or a relation.
	
	

[Volgende](2-filteren.md)

