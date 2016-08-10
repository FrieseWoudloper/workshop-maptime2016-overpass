## Recurse down
Een way is een geordende lijst met nodes. Nodes hebben coördinaten, ways niet.  
Voer ter illustratie onderstaande zoekopdracht uit. De zoekopdracht vraagt aan Overpass API om alle [parken](http://wiki.openstreetmap.org/wiki/Tag:leisure%3Dpark) in de stad Groningen die als vlak zijn ingetekend.

```
area["name"="Groningen"]["admin_level"="10"]; 
way["leisure"="park"](area);
out;
```

Je krijgt de volgende melding:  
```This query returned no nodes. In OSM, only nodes contain coordinates. For example, a way cannot be displayed without its nodes.```  
Kies voor de optie ```Gegevens weergeven```.  

Het resultaat van de zoekopdracht wordt nu getoond in het tabblad _Gegevens_, want zonder coördinaten kan er immers niets op de kaart worden weergegeven. In onderstaand screenshot zie je dat een way slechts een lijst is met verwijzingen naar nodes. 

![way is lijst met nodes](images/way-is-lijst-met-nodes.png)  

Met ```out center;``` vraag je voor iedere way het middelpunt van de bounding box op.

```
area["name"="Groningen"]["admin_level"="10"]; 
way["leisure"="park"](area);
out center;
```

Als je in het voorbeeld toch de vlakken van de parken nodig hebt, moet je gebruik maken van een _recurse down_. Hiervoor bestaat de ```>``` syntax.  Met een recurse down vraag je alle onderliggende nodes op.  

```
area["name"="Groningen"]["admin_level"="10"];
(
	way["leisure"="park"](area);
	>;
) 
out;
```



