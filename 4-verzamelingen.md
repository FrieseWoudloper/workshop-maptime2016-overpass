## 4.1 Sets

## 4.2 Doorsnede
Filteren op twee of meer tags is eenvoudig: je plaatst de tag-filters achter elkaar. Je krijgt als resultaat de elementen die aan alle filtercriteria voldoen. Met andere woorden: de doorsnede van de samenstellende verzamelingen. Zo is het bijvoorbeeld eenvoudig om alle café's op te vragen die toegankelijk zijn voor [rolstoelgebruikers](http://wiki.openstreetmap.org/wiki/Key:wheelchair).

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"]["wheelchair"="yes"](area);
out;
```

Oefening: Vraag alle pinautomaten op in de stad Groningen die getagt zijn als [```"name"="ING"```](http://wiki.openstreetmap.org/wiki/Key:name).

Als je alleen maar wilt weten òf er een ```wheelchair```-tag is, ongeacht de bijbehorende waarde, dan voer je onderstaande zoekopdracht uit. Je krijgt dan dus ook de café's waarvan expliciet is aangegeven dat ze níet toegankelijk zijn voor rolstoelgebruikers.

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"]["wheelchair"](area);
out;
```

## 4.3 Vereniging
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

[Volgende]()