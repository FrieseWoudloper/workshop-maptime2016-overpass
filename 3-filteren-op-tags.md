## 3.1 Tag filter
Een tag filter is als volgt gedefinieerd: ```["sleutel"="waarde"]```. In onderstaand voorbeeld worden alle [café's](http://wiki.openstreetmap.org/wiki/Tag:amenity%3Dcafe) in de stad Groningen opgevraagd.

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"](area);
out;
```

## 3.2 Reguliere expressies
Je kunt in tag filters ook gebruik maken van [reguliere expressies](https://nl.wikipedia.org/wiki/Reguliere_expressie). In onderstaand voorbeeld worden café's opgevraagd met in de naam het woord 'Coffee'.

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"]["name"~"Coffee"](area);
out;
```

Je kunt je zoekopdracht ook hoofdletterongevoelig maken. Onderstaande zoekopdracht retourneert -in tegenstelling tot de vorige- ook het café met de naam 'coffeecompany' (zonder hoofdletter).

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"]["name"~"Coffee",i];
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

Je kunt ook nodes opvragen met een ```name```-tag die leeg is. Gelukkig zijn die er niet zoveel. Vandaar dat we in deze zoekopdracht niet filteren op gebied, maar de hele OpenStreetMap-database doorzoeken.

```
node["amenity"="cafe"]["name"~"^$"];
out;
```

Oefening: selecteer alle nodes in de stad Groningen die getagt zijn als [winkel](http://wiki.openstreetmap.org/wiki/Key:shop) met ```'bakker'``` in de ```name```-tag, ongeacht of het in kleine of hoofdletters geschreven is.

Meer informatie over het gebruik van reguliere expressie in combinatie met Overpass API vind je [hier](http://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL#Value_matches_regular_expression_.28.7E.2C_.21.7E.29).

[Volgende](4-verzamelingen.md)