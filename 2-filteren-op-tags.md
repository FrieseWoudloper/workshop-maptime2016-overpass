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

Als je alleen maar wilt weten òf er een ```wheelchair```-tag is, ongeacht de bijbehorende waarde, dan voer je onderstaande zoekopdracht uit. Je krijgt dan dus ook de café's waarvan expliciet is aangegeven dat ze níet toegankelijk zijn voor rolstoelgebruikers.

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"]["wheelchair"](area);
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
Je kunt in tag-filters ook gebruik maken van [reguliere expressies](https://nl.wikipedia.org/wiki/Reguliere_expressie). In onderstaand voorbeeld worden nodes geselecteerd met de afkorting ING in de ```operator```-tag.
Voer onderstaande code uit en check in het tabblad _Gegevens_ dat nu ook de nodes worden geselecteerd met ```"operator"="ING Bank"```.

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="atm"]["operator"~"ING"](area);
out;
```

Met behulp van een reguliere expressie kun je in één regel filteren op café, bar of restaurant: 

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"~"cafe|bar|restaurant"](area);
out;
```

Je kunt ook controleren of er café's zijn zonder ```name```-tag:

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"]["name"!~"."](area);
out;
```

Met een reguliere expressie kun je je zoekopdracht ook hoofdletterongevoelig maken. Onderstaande query retourneert nodes met een ```name```-tag met de waarde ```"ING"```, ```"Ing"```, ```"ing"```, ```"inG"```, enzovoorts.

```
area["name"="Groningen"]["admin_level"="10"];
node["name"~"^ING$",i];
out;
```

Je kunt ook nodes opvragen met een ```name```-tag die leeg is. Gelukkig zijn die er niet zoveel. Vandaar dat we in deze zoekopdracht niet filteren op gebied, maar de hele OpenStreetMap-database doorzoeken.

```
node["amenity"="cafe"]["name"~"^$"];
out;
```

Oefening: selecteer alle nodes in de stad Groningen die getagt zijn als [winkel](http://wiki.openstreetmap.org/wiki/Key:shop) met ```"bakker"``` in de ```name```-tag, ongeacht of het in kleine of hoofdletters geschreven is.
Let op: niet alle nodes in het zoekresultaat zijn getagt als ```"shop"= "bakery"```!

Meer informatie over het gebruik van reguliere expressie in combinatie met Overpass API vind je [hier](http://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL#Value_matches_regular_expression_.28.7E.2C_.21.7E.29).

[Volgende]()