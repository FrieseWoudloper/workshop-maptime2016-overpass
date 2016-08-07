## Overpass Turbo
Overpass API is een service voor het bevragen van de OpenStreetMap database. [Overpass Turbo](http://overpass-turbo.eu/) is een interface voor deze service. Overpass Turbo helpt je bij het samenstellen van je query en visualiseert de query-resultaten. 


## Hello World!
We beginnen met een simpel voorbeeld: het opvragen van alle nodes die getagt zijn als brievenbus in de stad Groningen en directe omgeving.
Voer onderstaande code uit in Overpass Turbo en zoom in op Groningen.

```
node["amenity"="post_box"](53.18, 6.52, 53.25, 6.62);
out;
```

Bij het opstellen van een query moet je met het volgende rekening houden:
* Een query bestaat uit regels die na elkaar worden uitgevoerd.
* Regels eindigen met een puntkomma.
* Een filter op basis van een tag definieer je tussen blokhaken.
* Een filter op basis van locatie definieer je tussen ronde haken.
* Een bounding box definieer je als volgt: `(min lat, min lon, max lat, max lon)`

Oefening: Maak een query voor het opvragen van alle nodes in Groningen die getagt zijn als [pinautomaat](http://wiki.openstreetmap.org/wiki/Tag:amenity%3Datm.

## Filteren op locatie met behulp van een macro
Als je in Overpass Turbo al bent ingezoomd op het gebied waarvan je gegevens wilt opvragen, dan kun je volstaan met onderstaande code:

```
node["amenity"="post_box"]({{bbox}});
out;
```

Let op: `{{bbox}}` is een Turbo Overpass macro en werkt niet als je via een andere front end of rechtstreeks de Overpass API bevraagt.


## Filteren op locatie met behulp van `area`

```
area["name"="Groningen"]
node["amenity"="post_box"](area);
out;
```