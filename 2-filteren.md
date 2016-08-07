## Overpass Turbo
Overpass API is een service voor het bevragen van de OpenStreetMap database. [Overpass Turbo](http://overpass-turbo.eu/) is een interface voor deze service. Overpass Turbo helpt je bij het samenstellen van je query en visualiseert de query-resultaten. 

## Hello World!
We beginnen met een simpel voorbeeld: selecteer alle nodes die getagt zijn als brievenbus in het gebied tussen 53.18&deg; N en 53.25&deg; N, en tussen 6.52&deg; E en 6.62&deg; E.
 
Voer onderstaande code uit in Overpass Turbo en zoom in op de stad Groningen voor een overzicht van de resultaten.

`
node[amenity=post_box ](53.18, 6.52, 53.25, 6.62);

out;
`

