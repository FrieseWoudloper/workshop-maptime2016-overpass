## ```timeout```

Met de ```timeout``` setting geeft je aan hoe lang een zoekopdracht maximaal mag duren in seconden. Als de tijdsduur is verstreken, mag de server de zoekopdracht afbreken. De default waarde is 180 seconden. Bij een ingewikkelde zoekopdracht kan het nodig zijn om deze waarde te verhogen.  
Voorbeeld:
```
[timeout:180]
 ```
 
## ```out```
De ```out``` parameter definieert het formaat waarin het resultaat van de zoekopdracht wordt teruggegeven. Overpass API ondersteunt onder andere ```xml```, ```json``` en ```csv```. Het default formaat is XML. Let op: JSON is niet hetzelfde als GeoJSON!  
Voorbeeld:
```
[out:json]
```

Wanneer het resultaat is opgeslagen als ```csv```-bestand, kun je het eenvoudig openen in een teksteditor of spreadsheet. Bij het specificeren van ````csv``` als output formaat, moet je ook aangeven welke OpenStreetMap velden (sleutels) je wilt opnemen.   
Formaat:
```
[out:csv( fieldname_1 [,fieldname_n ...] [; csv-headerline [; csv-separator-character ] ] )]
```

Voorbeeld:
```
[timeout:500][out:csv(::"id", amenity, name; true; ";")];
area["name"="Groningen"]["admin_level"="10"];
node["amenity"="cafe"](area);
out;
```

```::"id"``` is een speciaal veld en bevat het OpenStreetMap object id.

## ```diff``` en ```adiff```

Het is mogelijk om wijzigingen in bepaalde periode op te vragen door een ```diff``` setting op te geven. In het resultaat van onderstaande zoekopdracht kun je zien dat studenten en medewerkers van de [Geodienst](http://www.rug.nl/society-business/centre-for-information-technology/research/services/gis/) van de Rijksuniversiteit Groningen de afgelopen tijd druk bezig zijn geweest met het bijwerken van de Groninger binnenstad in OpenStreetMap.

```
[diff:"2016-06-01T00:00:00Z","2016-07-31T24:00:00Z"];
area["name"="Groningen"]["admin_level"="10"];
node["shop"](area);
out;
```

Als je het zoekresultaat bekijkt in het tabblad _Gegevens_ kun je precies zien welke winkels zijn aangemaakt, gewijzigd of verwijderd in juni en juli van dit jaar.  

[Volgende](7-bonusmateriaal.md)