
# Inleiding
Deze handreiking beschrijft de toepassing van geometrie in informatiemodellering en de
implementatie daarvan in GML. Het is daarmee een ondersteuning voor de toepassing van de
norm NEN 3610:2011 – Basismodel geo-informatie [[NEN3610]]. NEN 3610 gaat hierin niet verder dan
verwijzing naar de relevante geo-informatie (ISO) normen. Voor het werkveld zijn deze normen
niet toegankelijk genoeg om te kunnen toepassen. Middels deze handreiking wordt de brug
gelegd. Dit document kan als een zelfstandig document worden gelezen. De inhoud is
grotendeels gebaseerd op originele normen. Voor de toegankelijkheid is de tekst vertaald naar
het Nederlands en bovendien vereenvoudigd. Deze handreiking kan daarom niet de normen
vervangen, maar bijvoorbeeld als introductie worden gebruikt. Voor de normatieve referentie
wordt in alle gevallen naar de originele documenten verwezen. 

## Inhoud van de handreiking
In eerste instantie komt geometrie voor in informatiemodellen in de vorm van geometrietypen populair
bekend als punten, lijnen, vlakken. ISO 19107 [[iso-19107-2003]] beschrijft middels een ruimtelijk schema (spatial schema)
deze geometrische primitieven, de uitbreidingen daarop en de relaties daartussen. De toepassing in dat
ruimtelijk schema is ook bepalend voor toepassing in informatiemodellen. De relatie tussen het ruimtelijk
schema en de toepassing in informatiemodellen wordt beschreven.

Het ruimtelijk schema kent geometrietypen met een toenemende complexiteit. Niet alle typen zijn
gegeven de stand van techniek even inter-operabel toepasbaar. Er is daarom een keuze gemaakt tot
welke typen we ons in Nederland (in de regel) beperken. Deze inperking wordt beschreven in een profiel.

Uitwisseling van geo-informatie (bestanden) gebeurt middels GML [[iso-19136-2007]]. Dat betekent dat de conceptuele
informatiemodellen toegepast worden in GML. Beschreven wordt hoe het ruimtelijke schema vertaald
wordt naar de GML implementatie omgeving. Ook hier wordt er uitgegaan van een Nederlands profiel op
de complete GML implementatie. Afgesproken is dat het Nederlands profiel het GML Simple Features
profile level 2 volgt. Dit profiel wordt in de annex door middel van business rules in schematron
vastgelegd. Met de schematron regels is een GML bestand te controleren op conformiteit met het
Nederlandse profiel.

Voor de implementatie in services is het soms nodig om vanwege de interoperabiliteit de complexiteit van
het GML bestand te reduceren tot Simple Features profile 0. Dat betekent dat het informatiemodel ook
gesimplificeerd moet worden. In hoofdstuk 5 zijn een aantal basisregels opgenomen voor het
transformeren van een SF2 model naar een SF0 model.

## Leeswijzer
[Hoofdstuk 2](#model) van dit document bevat een uitleg van het ruimtelijk schema zoals beschreven in ISO 19107
en gehanteerd in de GML standaard.

[Hoofdstuk 3](#gml) bevat een uitleg van het Simple Features profile for GML.

[Hoofdstuk 4](#gmlsf2) beschrijft de Nederlandse toepassing van GML en het Simple Features profile en de regels die
daaruit voortvloeien.

In [Hoofdstuk 5](#sf2tosf0) wordt tenslotte uitgelegd hoe, indien nodig, een aan Simple features level 2 voldoend
informatiemodel kan worden omgezet naar een vereenvoudigd model dat voldoet aan level 0.

De belangrijkste algemene GML coderingsregels staan beschreven in [Appendix 1](#coderingsregels), een uitgewerkt
voorbeeld van de in dit document beschreven regels en werkwijze in [Appendix 2](#voorbeeld), en een overzicht van de
verschillen tussen GML 3.1.1 en 3.2.1 in [Appendix 3](#gmlversieverschillen).