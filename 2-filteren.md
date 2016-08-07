## Overpass Turbo
Overpass API is een service voor het bevragen van de OpenStreetMap database. [Overpass Turbo](http://overpass-turbo.eu/) is een interface voor deze service. Overpass Turbo helpt je bij het samenstellen van je query en visualiseert de query-resultaten. 

## Hello World!
We beginnen met een simpel voorbeeld: het opvragen van alle nodes die getagt zijn als brievenbus in de stad Groningen en directe omgeving.
Voer onderstaande code uit in Overpass Turbo en zoom in op Groningen.

```
node[amenity=post_box ](53.18, 6.52, 53.25, 6.62);
out;
```

* Een query bestaat uit regels die na elkaar worden uitgevoerd.
* Regels eindigen met een puntkomma.
* Als je wilt filteren op een tag, geef je dat aan tussen blokhaken.
* Als je wilt filteren op locatie, geef je dat aan tussen ronde haken.
* Een bouding box specificeer je als volgt: `(min lat, min lon, max lat, max lon)`

## Filteren op locatie met behulp van een macro
Als je in Overpass Turbo al bent ingezoomd op het gebied, dan kun je volstaan met onderstaande code:

```
node[amenity=post_box ]({{bbox}});
out;
```

Let op: `{{bbox}}` is een Turbo Overpass macro en werkt niet als je via een andere front end of rechtstreeks de Overpass API bevraagt.