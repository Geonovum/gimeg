# Algemene coderingsregels GML

Hoe uit een UML informatiemodel uiteindelijk een XML Schema wordt gemaakt is aan regels gebonden die in ISO 19118 en in annex E van de OGC standaard GML beschreven zijn. Dit hoofdstuk geeft een overzicht van de belangrijkste van deze regels.

## Van UML naar GML

In ISO/TC 211 en OGC en daarom ook in NEN3610, wordt het semantisch model in UML vastgelegd. Vervolgens wordt via een geautomatiseerde procedure een XML/GML Schema uit het UML model gegenereerd. Op deze wijze wordt geborgd dat er geen verschillen ontstaan tussen het semantisch model in UML en het technisch model in het uitwisselformaat XML/GML. Het is ook toegestaan om handmatig een GML-conform XML Schema te maken.

Het semantisch model, vastgelegd in UML, wordt een UML Application Schema genoemd. Het bijbehorende XML Schema wordt een GML Application Schema genoemd. De term 'application' duidt er daarbij op dat het om een *toepassing* van GML gaat voor een specifiek domein/sector.

Het informatiemodel wordt gemodelleerd middels één of meer UML klassendiagrammen. De klassen worden gegroepeerd in UML packages, één voor elk te genereren schema bestand. Aan de packages en klassen kan extra informatie worden toegekend die gebruikt wordt om het genereren van het schema te sturen. Dit wordt gedaan door een stereotype toe te kennen aan het package of de klasse. GML definieert een standaard set aan stereotypen (GML 3.2.1 Annex E).

Bij een package kan bijvoorbeeld worden aangegeven dat het van het stereotype `<<ApplicationSchema>>` is waarna kan worden aangegeven wat de gewenste target namespace, namespace prefix en bestandsnaam zijn van het te genereren XML Schema. Bij een klasse kan men aangeven dat het een `<<FeatureType>>` is (geo-object) waarna bij de klasse metadata specifiek voor FeatureTypes kan worden ingevuld. Een klasse kan echter ook bijvoorbeeld van het stereotype `<<Union>>` zijn.

Een klasse waarvan is aangegeven dat het een FeatureType is, zal volgens de GML encoding rules voor Features worden opgenomen in het te genereren XML Schema als een globaal XML element in de substitutionGroup van `gml:AbstractFeature` met een
globaal complexType dat een extensie is van `gml:AbstractFeatureType`. Een klasse waarvan is aangegeven dat het een Union is, zal heel anders naar het XML Schema vertaald worden, namelijk als een `complexType` met een `choice`.

Voor het genereren van het XML Schema wordt een tool gebruikt, <a href="https://shapechange.net">ShapeChange</a> van interactive instruments, die op basis van een UML model een of meer GML Application Schema's genereert volgens de door de GML standaard gestelde eisen. Wie deze tool gebruikt voor het genereren van het GML application schema hoeft zich dus geen zorgen meer te maken over de GML encoding rules.

## GML encoding rules

Het XML Schema moet voldoen aan de eisen die GML eraan stelt (GML 3.2.1 clause 21 en delen van clause 7), en, indien uit UML gegenereerd, aan de eisen die GML stelt aan het vertalen van UML model naar XML Schema (GML 3.2.1 Annex E, ISO 19118).

Het GML XML Schema bevat abstracte typen, die in een GML Application Schema worden uitgebreid, en concrete typen die direct kunnen worden gebruikt.

De belangrijkste eisen aan GML Application schema's zijn:
<ul>
  <li>Clause 21.2.2: Het GML application schema definieert eigen uitbreidingen op het GML XML Schema in een eigen targetNamespace.</li>
  <li>Clause 21.2.3: Het GML application schema importeert het GML XML Schema.</li>
  <li>Clause 21.3.3:
  <ul><li>Voor elke klasse die een geo-object vertegenwoordigt moet een globaal complexType en een globaal element gedefinieerd zijn.</li>
      <li>Elk complexType voor een geo-object moet direct of indirect een extensie zijn van het type <code>gml:AbstractFeatureType</code>. <code>gml:AbstractFeatureType</code> is op zijn beurt een extensie van <code>gml:AbstractFeatureType</code>. Van dit type erven alle objecten het verplichte <code>gml:id</code> attribuut.</li>
      <li>Elk element in het schema voor een geo-object moet lid zijn van de substitutionGroup voor het element <code>gml:AbstractFeature</code> (dat wil zeggen: moet zich direct of indirect in de <code>substitutionGroup=”gml:AbstractFeature”</code> bevinden).</li>
      <li>Elk identificeerbaar object dat geen geo-object is, moet lid zijn van de substitutionGroup voor het element <code>gml:AbstractGML</code>.</li></ul></li>
  <li>Clause 21.3.4: Alle eigenschappen van een entiteit en alle relaties naar andere entiteiten worden opgenomen als child XML element.</li>
  <li>Clause 21.2.7: Als de waarde van een eigenschap een enkelvoudige waarde is, moet deze als literal value worden opgenomen in het eigenschap element zonder verdere markup. Zie ook 7.2.3.10.
  <pre class="example">
GOED:  
&lt;gml:Integer>5&lt;/gml:Integer>
FOUT:
&lt;gml:Integer>  
&lt;gml:value>5&lt;/gml:value>
&lt;/gml:Integer>
  </pre></li>
  <li>Clause 21.2.6: Het object property model moet gevolgd worden. Toelichting: GML is een objectenmodel. Dat wil zeggen dat alles is gemodelleerd als ofwel een object, ofwel een eigenschap van een object. Een relatie naar een ander object wordt ook gezien als eigenschap. Een object kan niet direct een ander object bevatten, maar een eigenschap kan wel een object bevatten. Dit wordt het object-property model genoemd. Als een eigenschap dus een complexe waarde heeft (structuur bezit) moet deze complexe waarde als apart object worden gedefinieerd. Een eigenschap mag zelf geen verdere structuur hebben. Het eigenschap element kan een verwijzing naar dit object bevatten of kan het als geneste structuur opnemen. Zie ook Clause 7.2.3.</li>
  <li>Clause 21.2.1/21.3.4: Het gebruik van XML attributen is toegestaan (maar niet voor het opnemen van eigenschappen van objecten). Attributen worden niet in een namespace gedeclareerd met uitzondering van <code>gml:id</code>. Zie ook clause 7.1.3.</li>
</ul>