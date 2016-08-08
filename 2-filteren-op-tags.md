## Filteren op een tag
Een tag-filter is als volgt gedefinieerd: ```["sleutel"="waarde"]```. In onderstaand voorbeeld worden alle [café's](http://wiki.openstreetmap.org/wiki/Tag:amenity%3Dcafe) in de stad Groningen opgevraagd.

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"](area);
out;
```

## Doorsnede
Filteren op twee of meer tags is eenvoudig: je plaatst de tag-filters achter elkaar. Je krijgt als resultaat de elementen die aan alle filtercriteria voldoen. Met andere woorden: de doorsnede van de samenstellende verzamelingen. Zo is het bijvoorbeeld eenvoudig om alle café's op te vragen die toegankelijk zijn voor [rolstoelgebruikers](http://wiki.openstreetmap.org/wiki/Key:wheelchair).

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"]["wheelchair"="yes"](area);
out;
```

Oefening: Vraag alle pinautomaten op in de stad Groningen die getagt zijn als [```"name"="ING"```](http://wiki.openstreetmap.org/wiki/Key:name).

## Vereniging
Hoe pak je het aan als je een lijst wilt van alle café en [restaurants](http://wiki.openstreetmap.org/wiki/Tag:amenity%3Drestaurant]) in een gebied? Dan vraag je om een vereniging (of _union_) van twee verzamelingen. Dat doe je als volgt:

```
area["name"="Groningen"]["admin_level"="10"] -> .a;
( 
	node["amenity"="cafe"](area.a);
  	node["amenity"="restaurant"](area.a);
);
out;
```

Oefening: Vraag alle pinautomaten op in de stad Groningen die getagt zijn als ```"name"="ING"``` en/of [```"operator"="ING"```](http://wiki.openstreetmap.org/wiki/Key:operator).

## Reguliere expressies
Je kunt in tag-filters ook gebruik maken van [reguliere expressies](https://nl.wikipedia.org/wiki/Reguliere_expressie). In onderstaand voorbeeld worden nodes geselecteerd met _ING_ in de ```operator```-tag.
Voer onderstaande query uit en check in het tabblad _Gegevens_ dat nu ook de nodes worden geselecteerd met ```"operator"="ING Bank"```.

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="atm"]["operator"~"ING"](area);
out;
```