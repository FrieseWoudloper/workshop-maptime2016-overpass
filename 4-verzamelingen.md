## 4.1 Sets
In Overpass QL werk je met _sets_. Als je niet expliciet een set specificeert, wordt alles gelezen van en weggeschreven naar de standaard set ```_```.
Als je gegevens wilt wegschrijven naar een andere set, gebruik je de ```->``` syntax. 

```
area["name"="Groningen"]["admin_level"="10"] -> .g;
node["amenity"="cafe"](area.g);
out;
```

Wanneer je binnen één zoekopdracht meerdere malen aan dezelfde verzameling gegevens wilt refereren, kan het handig zijn om met sets te werken.

## 4.2 Vereniging
Hoe pak je het aan als je een lijst wilt van alle café plus [restaurants](http://wiki.openstreetmap.org/wiki/Tag:amenity%3Drestaurant]) in een gebied? Dan vraag je om een vereniging (of _union_) van twee verzamelingen. Dat doe je als volgt:

```
( 
	area["name"="Groningen"]["admin_level"="10"]; node["amenity"="cafe"](area);
  	area["name"="Groningen"]["admin_level"="10"]; node["amenity"="restaurant"](area);
);
out;
```

De herhaling van het ```area``` filter ziet er lelijk uit, maar is noodzakelijk. Probeer het maar eens uit.  
Om het overzichtelijk te houden, kun je in dit geval beter een set definiëren.

```
area["name"="Groningen"]["admin_level"="10"] -> .g;
( 
	node["amenity"="cafe"](area.g);
  	node["amenity"="restaurant"](area.g);
);
out;
```

Hieronder nog een voorbeeld van een zoekopdracht waarin de café's in de stad Groningen en Leeuwarden worden opgevraagd.

```
area["name"="Groningen"]["admin_level"="10"] -> .g;
area["name"="Leeuwarden"]["admin_level"="10"] -> .l;
( 
	node["amenity"="cafe"](area.g);
	node["amenity"="cafe"](area.l);
);
out;
```

## 4.3 Eén zoekopdracht voor nodes, ways en relations
Tot nu toe hebben we alleen nodes opgevraagd, maar er zijn meer soorten objecten. Een café kan bijvoorbeeld ook zijn in OpenStreetMap zijn opgenomen als way of relation.  
Om zeker te weten dat je alle café's in Groningen opvraagt, moet je dus ook ways en relations meenemen.

```
area["name"="Groningen"]["admin_level"="10"] -> .g;
( 
	node["amenity"="cafe"](area.g);
	way["amenity"="cafe"](area.g);
	relation["relation"="cafe"](area.g);
);
out center;
```

De laatste regel ```out center;``` is aangepast, zodat je voor alle café's één punt terug krijgt. Als een café in OpenStreetMap is ingetekend als een vlak, geeft de zoekopdracht alleen het middenpunt retour.

Als je inzoomt op het centrum van Groningen zie je dat café 'Goudkantoor' aan het Waagplein als enige café geen node is, maar een way.

Oefening:  
Natuurijsbanen zijn getagt als [```"leisure"="ice_rink"```](http://wiki.openstreetmap.org/wiki/Tag:leisure%3Dice_rink) en ```"seasonal"="yes"```. Natuurijsbanen in OpenStreetMap zijn ingekend als node, way of relation. Maak een zoekopdracht voor het opvragen van alle natuurijsbanen in Nederland (```"name"="Nederland"``` en ```"admin_level"="2"```). Zorg ervoor dat je voor iedere ijsbaan één punt terug krijgt.

[Volgende]()