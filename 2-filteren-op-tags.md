## Filteren op een tag
Een tag-filter is als volgt gedefinieerd: ```["sleutel"="waarde"]```. In onderstaand voorbeeld worden alle (café's)[http://wiki.openstreetmap.org/wiki/Tag:amenity%3Dcafe] binnen de bouding box van Overpass Turbo opgevraagd. Zorg er voor dat je bent ingezoomd op een dichtbevolkt gebied, anders krijg je misschien geen resultaten.

```
node["amenity"="cafe"]({{bbox}});
out;
```

## Doorsnede
Filteren op twee of meer tags is eenvoudig: je plaatst de tag-filters achter elkaar. Je krijgt als resultaat de elementen die aan alle filtercriteria voldoen. Met andere woorden: de doorsnede van de samenstellende verzamelingen. Zo is het bijvoorbeeld eenvoudig om alle café's op te vragen die toegankelijk zijn voor [rolstoelgebruikers](http://wiki.openstreetmap.org/wiki/Key:wheelchair).

```
node["amenity"="cafe"]["wheelchair"="yes"]({{bbox}});
out;
```

## Vereniging
Hoe pak je het aan als je een lijst wilt van alle café en (restaurants)[[http://wiki.openstreetmap.org/wiki/Tag:amenity%3Drestaurant]] in een gebied? Dan vraag je om een vereniging (of _union_) van twee verzamelingen. Dat doe je als volgt:

```
(
	node["amenity"="cafe"]({{bbox}});
	node["amenity"="restaurant"]({{bbox}});
);
out;
```

In bovenstaande voorbeelden zijn we er vanuit gegaan dat café's en restaurants in OpenStreetMap zijn opgenomen als nodes, maar dat hoeft niet. Het kunnen ook ways of relations zijn! 
Ter illustratie het voorbeeld van natuurijsbanen in Nederland. De meeste natuurijsbanen zijn nodes.

```
area["name"="Nederland"]["admin_level"="2"];
node["leisure"="ice_rink"]["seasonal"="yes"];
out;
```

Maar er zijn ook ways getagt als natuurijsbanen.

```
area["name"="Nederland"]["admin_level"="2"];
way["leisure"="ice_rink"]["seasonal"="yes"];
out;
```

Volgende 