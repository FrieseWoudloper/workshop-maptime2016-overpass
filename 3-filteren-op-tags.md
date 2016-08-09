## 3.1 Tag filter
Een tag filter is als volgt gedefinieerd: ```["sleutel"="waarde"]```. In onderstaand voorbeeld worden alle [café's](http://wiki.openstreetmap.org/wiki/Tag:amenity%3Dcafe) in de stad Groningen opgevraagd.

```
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"](area);
out;
```

## 3.2 Reguliere expressies
Je kunt in tag filters ook gebruik maken van [reguliere expressies](https://nl.wikipedia.org/wiki/Reguliere_expressie). In onderstaand voorbeeld worden nodes geselecteerd met de afkorting ING in de ```operator```-tag.
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

Met een reguliere expressie kun je je zoekopdracht ook hoofdletterongevoelig maken. Onderstaande zoekopdracht retourneert nodes met een ```name```-tag met de waarde ```"ING"```, ```"Ing"```, ```"ing"```, ```"inG"```, enzovoorts.

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

[Volgende](4-verzamelingen.md)