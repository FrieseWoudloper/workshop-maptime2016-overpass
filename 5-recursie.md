Een way is een geordende lijst met nodes. Nodes hebben coördinaten, ways niet.  
Voer ter illustratie onderstaande zoekopdracht uit. De zoekopdracht vraagt aan Overpass API om alle [parken](http://wiki.openstreetmap.org/wiki/Tag:leisure%3Dpark) in de stad Groningen die als vlak zijn ingetekend.

```
area["name"="Groningen"]["admin_level"="10"]; 
way[leisure=park](area);
out;
```

Je krijgt de volgende melding:
```This query returned no nodes. In OSM, only nodes contain coordinates. For example, a way cannot be displayed without its nodes.```  
Kies voor de optie ```Gegevens weergeven```.