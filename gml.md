# Geometrie in GML - Nederlands profiel

Het Nederlands Basismodel Geo-informatie (NEN 3610) specificeert in overeenstemming met de ISO-geo-informatiestandaarden GML (Geography Markup Language) als uitwisselingsformaat voor geo-informatie. De actuele standaard voor GML wordt gehanteerd. Op dit moment is dat GML 3.2.1, waarbij ook GML 3.1.1 nog ondersteund wordt. Omdat GML 3.2.1 een zeer uitgebreide standaard is wordt er een profiel, een subset gehanteerd.

GML 3.2.1 is een uitgebreide standaard, ontwikkeld door het Open Geospatial Consortium (OGC) en biedt oplossingen voor een groot aantal situaties en variaties voor het uitwisselen van geo-informatie. Variaties zijn er in geometrietypen maar ook in complexiteit van datastructuren. Om verschillende niveaus van toepassing van GML 3.2.1 mogelijk te maken zijn er door OGC zogenaamde profielen gemaakt. De ontwikkeling van de profielen is voortgekomen uit een behoefte van onder meer softwareleveranciers om verschillende niveaus van complexiteit te ondersteunen. Operabiliteit kan daarmee beter gegarandeerd worden. De profielen omvatten elk een subset van de totale GML 3.2.1 standaard. De standaardprofielen zijn Simple Features Profile 0, Simple Features Profile 1 en Simple Features Profile 2 (afgekort tot respectievelijk SF0, SF1, en SF2). Deze profielen hebben een toenemende complexiteit en bieden ook een toenemende functionaliteit. SF0 is dus het eenvoudigst, en SF2 het meest uitgebreid. Het OGC Simple Features profile moet niet verward worden met de ISO 19125 - Simple feature access standaard. De eerste gaat over implementatie van geometrie in GML de tweede over definities van 2 dimensionale geometrietypen.

Een profiel dat meer complexiteit en functionaliteit toestaat, biedt meer mogelijkheden voor datamodellering of geometriebeschrijvingen, maar is ook moeilijker toe te passen in software. Deze complexiteit kan de uitwisseling tussen verschillende softwareplatforms bemoeilijken. Een eenvoudig profiel daarentegen biedt minder mogelijkheden voor datamodellering maar is wel eenvoudiger toe te passen in generieke software. Het is daarom van belang voor- en nadelen tegen elkaar af te wegen. 

In Nederland is het SF2 profiel op GML van toepassing verklaard.

## Totstandkoming SF2 als Nederlands profiel op GML
Bij het tot stand komen van het Nederlandse GML profiel zijn een aantal beginselen leidend geweest:
- het profiel moet de eisen van het geo-informatie werkveld weerspiegelen;
- het profiel is gekoppeld aan (toepassingen van) NEN 3610;
- het profiel is een basisprofiel dat basiseisen die door de sectorale informatiemodellen gesteld worden omvat;
- een sectoraal informatiemodel kan uitbreidingen op het basisprofiel formuleren;
- het profiel moet afgestemd zijn op de actuele technische mogelijkheden die software biedt.

Door deze beginselen geeft het profiel voldoende richting voor standaardisering van algemene functionaliteit maar ook flexibiliteit voor toepassingen die specifieke oplossingen nodig hebben. Het profiel geeft richting aan de aanbodkant van geo-informatie en aan de modelleurs van informatiemodellen voor de oplossingen en mogelijkheden voor datamodellering. Voor softwaretoepassingen biedt het profiel een basis waar functionaliteit en toepassingen op afgestemd kunnen worden.

Om een uitspraak te kunnen doen over de eisen die in Nederland gesteld worden aan GML als uitwisselingsstandaard is een enquête gehouden onder de beheerders van aan NEN 3610 gerelateerde informatiemodellen. De volgende informatiemodellen en hun respectievelijke sectoren zijn hier bij betrokken: BAG (adressen en gebouwen), IMGeo (geografie), IMWA, UM Aquo-m, UM Aquo-krw (water), TOP10NL/IMTOP (topografie), GBR (grootschalig weg, water en waterwegen), IMWE (welstand), IMRO (ruimtelijke ordening), IMKICH (cultuurhistorie), IMKAD (kadaster), IMKL, BMKL (kabels en leidingen), IMBOD (bodem). Op basis van deze eisen is een eerste concept profiel voor GML ontwikkeld.

Het conceptprofiel is gepresenteerd aan en voor commentaar uitgebracht naar het hele geo-informatie werkveld. Een belangrijke rol was hierin voor softwareleveranciers en –ontwikkelaars om eisen vanuit de toepassingen in het profiel te verwerken. Het conceptprofiel is gepubliceerd onder de werknaam gml4nl en was op het moment van publicatie gebaseerd op GML 3.1.1.

Bij de ISO publicatie van GML 3.2.1 is ook het Nederlandse profiel vernieuwd. Het Nederlandse profiel bleek daarbij zo weinig van het GML SF2 profiel te verschillen dat besloten is om geen apart Nederlands profiel te publiceren maar SF2 als officieel Nederlandse profiel op GML 3.2.1 te volgen. Belangrijk was daarin dat het huidige SF2 profiel, in tegenstelling tot 3.1.1 SF2, ook cirkels en bogen opgenomen heeft als geometrievormen.

##  GML Simple Features profielen en data complexiteit

De GML standaard is een omvangrijke verzameling van XML elementen en attributen waarmee van alles mogelijk is. De GML standaard bevat bijvoorbeeld definities voor dynamische (voortdurend veranderende) objecten, topologie, complexe geometrische typen, en rasters. Dit maakt GML tot een rijke standaard die veel te bieden heeft, maar maakt het ook moeilijker voor software aanbieders om de hele standaard te ondersteunen.

Om dit probleem te adresseren zijn er verschillende profielen op GML gedefinieerd door de OGC. Een GML profiel is een subset van de complete GML set. De subset is wel zodanig dat het profiel niet in tegenspraak is met de complete set. Voor GML 3.2.1 zijn er drie profielen met toenemende complexiteit, de zogenaamde Simple Features profielen. Softwareleveranciers kunnen ervoor kiezen hun ondersteuning van GML te beperken tot een van deze profielen, of uiteraard om de hele standaard te ondersteunen.

Wat is nu een “simple feature”? Een feature is in de context van GML een equivalent van een instantie van een objecttype zoals bijvoorbeeld een gebouw, een boom, een persoon, een ding. Deze instanties hoeven niet noodzakelijkerwijs een geometrie, of locatie-informatie te hebben. Met ‘simple’ wordt in deze context bedoeld dat de features:

- Een eenvoudige datastructuur hebben.

- Als het ruimtelijke objecten zijn, een eenvoudige geometrische vorm hebben.

De GML standaard is gebaseerd op de algemene XML standaard XML Schema [[xmlschema-0]]. Een deel van de regels uit de simple features profielen hebben hier betrekking op. SF0 beperkt bijvoorbeeld de datatypen uit XML Schema die gebruikt mogen worden
(string, boolean, etc) en definieert daarmee in feite ook een subset van XML Schema. Dit geldt voor de meeste regels die betrekking hebben op de eenvoud van de datastructuur.

Wat er precies wordt beschouwd als ‘eenvoudig’, oftewel wat er wel en niet is toegestaan, wordt gespecificeerd in de GML Simple Features Profile standaard [[GML-SF]].

## Regels voor alle Simple Features profile levels

De volgende tabel uit het OGC document Geography Markup Language (GML) simple
features profile, geeft een overzicht van de inhoud van de verschillende
profielen.

### Inhoud SF niveau’s

|                                                    | **SF-0**                                                       | **SF-1**                                                       | **SF-2**                                               |
|----------------------------------------------------|----------------------------------------------------------------|----------------------------------------------------------------|--------------------------------------------------------|
| Beperkte set van ingebouwde niet ruimtelijke typen | String, integer, measurement, date, real, binary, boolean, URI | String, integer, measurement, date, real, binary, boolean, URI | Geen beperking                                         |
| Beperkte set van geometrietypen[^3]                | (multi)Punt, (multi)lijn, (multi)vlak,(multi) geometry         | (multi)Punt, (multi)lijn, (multi)vlak,(multi) geometry         | (multi)Punt, (multi)lijn, (multi)vlak,(multi) geometry |
| Zelf ontwikkelde datatypen                         | nee                                                            | ja                                                             | ja                                                     |
| Gebruik van nillable en xsi:nil                    | nee                                                            | ja                                                             | ja                                                     |
| Cardinaliteit(multipliciteit)                      | 0 of 1                                                         | 0 tot onbeperkt                                                | 0 tot onbeperkt                                        |
| Niet-ruimtelijke referenties                       | Ja, Alleen by reference (gml:ReferenceType)                    | Ja By reference (gml:ReferenceType) of inline                  | Ja By reference en inline in combinatie is mogelijk.   |
| Ruimtelijke referenties                            | Ja, Alleen by reference (gml:ReferenceType)                    | Ja Alleen by reference (gml:ReferenceType)                     | Ja By reference en inline in combinatie is mogelijk.   |

<a href="#geometrietypen">Tabel 2</a> geeft meer detail over de toegestane geometrietypen.

Het is toegestaan samengestelde (geaggregeerde) geometrie te gebruiken, te weten MultiPoint, MultiCurve, MultiSurface, en MultiGeometry. Hierbinnen geldt dat alleen de enkelvoudige container elementen mogen worden gebruikt. Dus wel: `gml:pointMember` maar niet: `gml:pointMembers` enzovoort.

Voor **alle niveau’s (SF0, SF1 en SF2)** geldt bovendien dat de volgende GML onderdelen in het Simple Features profile **niet** worden ondersteund:

- Rasters (coverages)
- Topologie
- Tijd en dynamische features
- Observaties/metingen

Verder geldt:

- Het gebruik van Gml:metadataProperty is niet toegestaan. Men moet indien nodig zelf metadata elementen definiëren in een GML application schema.
- In het GML application schema moet het compliance level op de voorgeschreven manier (zie <a href="#schema-compliance-data-levering-data-ontvangen"></a>) worden aangegeven.
- In het GML application schema moet het volledige GML schema geïmporteerd worden (gml.xsd).
- Een GML application schema mag maximaal één feature collection op de voorgeschreven manier (zie <a href="#feature-collecties"></a> definiëren.

### Feature collecties

Een GML document is gedefinieerd als één feature collectie, een verzameling van geo-objecten. Deze collectie krijgt een eigen naam gedefinieerd in het XML-Schema. Een GML document begint met de declaratie van deze collectie in het root element. Er wordt geen gebruik gemaakt van de container `gml:featureMembers` en de individuele `gml:featureMember`. Deze elementen zijn komen te vervallen vanaf GML versie 3.2.

Voorbeeld XSD fragment:

<pre class="example">
&lt;element name="FeatureCollectionIMRO" type="imro:FeatureCollectionIMROType" 
            substitutionGroup="gml:AbstractGML"/>
&lt;complexType name="FeatureCollectionIMROType">
  &lt;complexContent>
    &lt;extension base="gml:AbstractFeatureType">
      &lt;sequence minOccurs="0" maxOccurs="unbounded">
        &lt;element name="featureMember">
          &lt;complexType>
            &lt;complexContent>
              &lt;extension base="gml:AbstractFeatureMemberType">
                &lt;sequence>
                  &lt;element ref="gml:AbstractFeature"/>
                &lt;/sequence>
              &lt;/extension>
            &lt;/complexContent>
          &lt;/complexType>
        &lt;/element>
      &lt;/sequence>
    &lt;/extension>
  &lt;/complexContent>
&lt;/complexType>
</pre>

Voorbeeld GML fragment:

<pre class="example">
&lt;imro:FeatureCollectionIMRO gml:id="Collectie"
    xmlns:imro="http://www.geonovum.nl/imro2012"  
    xmlns:xlink=<http://www.w3.org/1999/xlink>xmlns:gml="http://www.opengis.net/gml/3.2"  
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
    xsi:schemaLocation="http://www.geonovum.nl/imro2012 IMRO2012.xsd"\>
  &lt;imro:featureMember>
    &lt;imro:Bestemmingsplangebied gml:id="NL.IMRO.0999.BP2008000001-0005">
         ...
    &lt;/imro:Bestemmingsplangebied>
  &lt;/imro:featureMember>
  &lt;imro:featureMember>
    &lt;imro:Enkelbestemming gml:id="NL.IMRO.135">
         ...
    &lt;/imro:Enkelbestemming>
  &lt;/imro:featureMember>
  ...
&lt;/imro:FeatureCollectionIMRO>
</pre>

### Geometrietypen

GML Simple Feature Profile staat een beperkte subset van geometrietypen uit GML toe. Deze subset is voor SF0, SF1, en SF2 gelijk.

<em>Tabel 2: Geometrietypen</em>. Van elk type is ook het equivalent in UML gegeven (Spatial Schema):

| **In GML**        | **UML equivalent** | **Restricties**                                                                                                                                                                                                                                    | **Welk GML Schema document**                 |
|-------------------|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------|
| `gml:Point`         | GM_Point           | geen                                                                                                                                                                                                                                               | geometryBasic0d1d.xsd                        |
| `gml:Curve`         | GM_Curve           | `gml:LineString` of `gml:Curve` met `gml:LineStringSegment`, `gml:Arc`, `gml:Circle` of `gml:CircleByCenterPoint`                                                                                                                                              |                                              |
| `gml:Surface`       | GM_Surface         | ondersteund wordt: `gml:Polygon` of `gml:Surface` met `gml:PolygonPatch` patches. Surface grenzen kunnen beschreven worden met `gml:LinearRing` of `gml:Ring` met enkele `gml:Curve` met `gml:LineStringSegment`, `gml:Arc`, `gml:Circle` of `gml:CircleByCenterPoint` | geometryBasic0d1d.xsd geometryPrimitives.xsd |
| `gml:Geometry`      |                    | ondersteund wordt: `gml:Point`, `gml:LineString`, `gml:Curve`, `gml:Polygon`, `gml:Surface`, `gml:MultiPoint`, `gml:MultiCurve`, `gml:MultiSurface`                                                                                                                 | geometryBasic0d1d.xsd                        |
| `gml:MultiPoint`    |                    | geen                                                                                                                                                                                                                                               | geometryAggregates.xsd                       |
| `gml:MultiCurve`    |                    | zelfde als `gml:Curve`                                                                                                                                                                                                                               | geometryAggregates.xsd                       |
| `gml:MultiSurface`  |                    | zelfde als `gml:Surface`                                                                                                                                                                                                                             | geometryAggregates.xsd                       |
| `gml:MultiGeometry` |                    | zelfde als `gml:Geometry`                                                                                                                                                                                                                            | geometryAggregates.xsd                       |

Specificatie van coördinaten:

Voor `gml:point` en `gml:CircleByCenterPoint` is dit middels het `gml:pos` element. Voor alle ander typen is het de `gml:posList`.

### Coördinaatreferentiesysteem

In het Simple Features profiel wordt aanbevolen om het coördinaatreferentiesysteem (CRS) van de in een GML document aanwezige
coördinaten in het GML document op te nemen. In clausule 9 van NEN 3610:2011 wordt dit zelfs verplicht gesteld.

In het GML bestand dient het coördinaatreferentiesysteem opgenomen te worden als waarde van het in GML gedefinieerde attribuut `srsName`. Aangeraden wordt om dit zo generiek mogelijk te doen. Als alle coördinaten in het document hetzelfde CRS hebben, zou het `srsName` attribuut op het niveau van de feature collection moeten worden opgenomen. Anders kan `srsName` worden opgenomen op feature member niveau of op geometrie niveau.

Voor het definiëren van het coördinaatreferentiesysteem kunnen <a href="http://www.epsg.org/">EPSG (European Petroleum Survey Group)</a> codes worden gebruikt.

<pre class="example">
&lt;wfs:FeatureCollection>
  &lt;gml:boundedBy>
    &lt;gml:Envelope srsName="urn:opengis:def:crs:EPSG::28992">...&lt;/gml:Envelope>
  &lt;/gml:boundedBy>
  &lt;!-- feature instances go here -->
  &lt;wfs:member>
    &lt;myns:MyFeature>
      &lt;gml:boundedBy>
        &lt;gml:Envelope srsName="...">...&lt;/gml:Envelope>
      &lt;/gml:boundedBy>
      &lt;!-- zero or more property values go here -->
      &lt;myns:geomProperty>
        &lt;gml:Polygon srsName="...">...&lt;/gml:Polygon>
      &lt;/myns:geomProperty>
      &lt;!-- zero or more property values go here -->
    &lt;/myns:MyFeature>
  &lt;/wfs:member>
  &lt;!-- more feature instances go here -->
&lt;/wfs:FeatureCollection>
</pre>

### Container elementen voor samengestelde geometrietypen

Geometrietypen die zijn samengesteld fungeren als een container (aggregatie) voor de verschillende individuele geometrie elementen. De volgende container elementen zijn toegestaan.

<em>Tabel 3: Samengestelde geometrietypen</em>

| Samengesteld geometrie type   | Container element    |
|-------------------------------|----------------------|
| `gml:MultiPoint`              | `gml:pointMember`    |
| `gml:MultiCurve`              | `gml:curveMember`    |
| `gml:MultiSurface`            | `gml:surfaceMember`  |
| `gml:MultiGeometry`           | `gml:geometryMember` |

### Lijninterpolaties

Het type lijninterpolatie beschrijft hoe de verbinding tussen twee coördinaatparen (punten) is beschreven. In de GML standaard is hiervoor een uitgebreid aantal mogelijkheden. Het Simple Features profiel ondersteunt hiervan maar twee:lineaire interpolatie en interpolatie door middel van cirkelbogen. Deze laatste niet lineaire interpolatie was geen onderdeel van het SF profiel van de vorige GML versie (3.1). Vanwege het toegenomen gebruik in applicaties zijn ze nu wel toegevoegd.

In de tabel in paragraaf 3.3.2 is precies te zien welke typen lijninterpolatie zijn toegestaan door te kijken naar de restricties bij `gml:Curve` en `gml:Surface`. Toegestaan voor het opnemen van rechte lijnen zijn alleen gml:LineString en `gml:Curve` met `gml:lineStringSegments`. Voor het opnemen van bogen zijn alleen `gml:Arc`, `gml:Circle` en `gml:CircleByCenterPoint` toegestaan. `gml:Arc` is de GML implementatie van de cirulaire boog met drie punten (beginpunt, eindpunt en punt waar de boog doorheen loopt).

De overige typen lijninterpolatie, zoals `gml:CubicSpline`, `gml:ArcByBulge`, etc, zijn niet toegestaan.

## Simple features profile 0 (SF0)

SF0 is het meest eenvoudige profiel op GML, m.a.w. het profiel met de meeste restricties op GML en XML Schema.

Regels:

<ul>
    <li>Waarden van een eigenschap mogen inline (genest) of door verwijzing worden opgenomen. Er moet wel een keuze gemaakt worden voor éen van de twee manieren: het is niet toegestaan om in een SF0 GML document de ene keer een waarde inline op te nemen en een andere keer te verwijzen. Verwijzingen mogen alleen opgenomen worden met <code>gml:ReferenceType</code>. Het <code>gml:ReferenceType</code> is de simpele GML implementatie van in UML als associaties gemodelleerde koppelingen tussen objecttypen. De naam van de gekoppelde bron (objecttype) wordt opgenomen in een appinfo element, zodat te zien is naar wat voor soort ding er gerefereerd wordt. De daadwerkelijke verwijzing naar een object instantie wordt met <code>xlink:href</code> gedaan.</li>
    <li>Beperkte set van ingebouwde niet-geometrische typen. Andere eenvoudige of samengestelde typen uit XML Schema of zelf gedefinieerd, zijn niet toegestaan, alleen de volgende:
    <ol>
        <li>String:
        <ol>
            <li>Een element dat een alfanumerieke waarde heeft moet zijn van het XML Schema type <code>string</code> of een restrictie  daarvan. De <code>maxLength</code> of <code>length</code> mogen worden gebruikt om de string verder in te perken.</li>
        2. Een element dat een alfanumerieke waarde heeft waarvan de taal moet worden aangegeven, moet hiervoor gebruik maken van het <code>xml:lang</code> attribuut waarin de taalcode is opgegeven.</li>
        </ol>
        </li>
        <li>Integer: Een element met een integer waarde moet zijn van het XML Schema-type <code>integer</code> of een restrictie daarvan. In het <code>totalDigits</code> element kan worden aangegeven hoe lang het getal mag zijn.</li>
        <li>Measurement: Een element dat een meting als waarde heeft moet van het type <code>gml:MeasureType</code> zijn of zijn afgeleid.</li>
        <li>Date: Een element dat een datum als waarde heeft, moet zijn van een van de XML Schema typen <code>date</code> of <code>dateTime</code> of een restrictie daarvan.</li>
        <li>Real: Een element dat een real waarde moet bevatten, moet zijn van een van de XML Schema typen <code>double</code> of <code>decimal</code> of een restrictie daarvan. Bij een decimal mogen de facetten <code>totalDigits</code> en <code>fractionDigits</code> worden opgegeven, bij een double niet. Meestal zullen elementen met real waarden overigens metingen zijn en dus met een <code>gml:MeasureType</code> worden opgenomen.</li>
        <li>binary: Een element dat een binaire inhoud heeft, moet dit ofwel inline in het GML bestand coderen met het XML Schema type <code>base64Binary</code> of <code>hexBinary</code>; of ernaar verwijzen met een URL. In elk geval is het opnemen van de <code>mimeType</code> verplicht.</li>
        <li>boolean: Een element dat een boolean (ja/nee) waarde heeft, moet van het XML Schema type <code>boolean</code> zijn.</li>
        <li>URI: een element dat een URI als waarde heeft, moet van het XML Schema type <code>anyURI</code> zijn.</li>
    </ol>
    </li>
    <li>De niet geometrische typen mogen qua waarde verder alleen ingeperkt worden met de XML Schema facetten <code>minInclusive</code>, <code>minExclusive</code>, <code>maxInclusive</code>, <code>maxExclusive</code>, en <code>enumeration</code>. Hiermee kan men de minimale en maximale waarden van getallen inperken en enumeraties definiëren.</li>
    <li>Een element eigenschap mag niet meerdere keren voorkomen; de kardinaliteit die mag worden opgegeven is beperkt tot 0 of 1.</li>
    <li>Het XML Schema attribuut <code>nillable</code> mag niet gebruikt worden.</li>
    <li>Het aantal toegestane GML geometrie typen is ingeperkt. Dit is dezelfde subset voor SF0, SF1, en SF2; zie <a href="#geometrietypen"></a>.</li>
    <li>Features mogen meerdere geometrische eigenschappen hebben.</li>
</ul>

## Simple features profile 1 (SF1)

SF1 kent minder restricties dan SF0 en is dan ook iets complexer.

SF1 neemt de regels van SF0 over, met uitzondering van het volgende:

- Het is toegestaan om eigen datatypen te maken met een eenvoudige waarde, maar wel gebaseerd op de set van toegestane niet-geometrische typen uit SF0.
- Het is toegestaan om samengestelde datatypen te maken die een eigen, geneste structuur hebben.
- Eigenschappen mogen meerdere keren voorkomen.
- Het XML Schema attribuut `nillable` mag gebruikt worden.

### Zelf ontwikkelde datatypen: geneste inhoud.

In SF1 en SF2 kan een geneste structuur van attributen toegepast worden. Attributen kunnen daarbij samengesteld worden uit een verzameling attributen. We noemen deze constructie het samengesteld attribuut.

Een voorbeeld is een attribuut met de naam ‘identificatie’ en een datatype ‘identifier’. Het datatype bestaat vervolgens uit drie attributen ‘identificatiecode’, ‘organisatie’, ‘versie’. Het attribuut ‘identificatie’ is in dit geval samengesteld uit drie andere attributen, verenigd in het zelfgemaakte datatype ‘identifier’.

In een GML application schema ziet die constructie als volgt uit:

<pre class="example">
&lt;complexType name="IdentifierPropertyType">
  &lt;sequence>
    &lt;element ref="fw:Identifier"/>
  &lt;/sequence>
&lt;/complexType>
&lt;element name="Identifier">
  &lt;complexType>
    &lt;sequence>
      &lt;element name="identificatiecode" type="string"/>
      &lt;element name="organisatie" type="string" minOccurs="0" maxOccurs="1"/>
      &lt;element name="versie" type="string" minOccurs="0" maxOccurs="1"/>
    &lt;/sequence>
  &lt;/complexType>
&lt;/element>
</pre>

## Simple features profile 2 (SF2)

SF2 is het minst restrictieve niveau in het profiel en is geschikt voor geavanceerde informatiemodellen. Vergeleken met SF1 vervallen in SF2 alle regels over het definiëren van niet-geometrische eigenschappen. D.w.z. alle typen uit de XML Schema standaard mogen gebruikt worden, eigen eenvoudige en samengestelde typen mogen worden gedefinieerd, er zijn geen restricties op kardinaliteit, etc.

Waarden van een eigenschap mogen in SF2 inline (genest) of door verwijzing worden opgenomen. Een mix van beide mag gebruikt worden en gebruik van `gml:ReferenceType` is niet verplicht.

Wel blijft de restrictie op de toegestane geometrietypen gelden, net als de regel over het definiëren van feature collecties.

## Schema compliance: data levering – data ontvangen

Het Simple Features profile van GML 3.1 was in technisch opzicht een gestripte versie van de volledige GML XSD. Dit bleek echter bij veel validatietools problemen op te leveren. De gestripte XSD had dezelfde namespace als de volledige GML XSD waardoor conflicten konden optreden.

Bij het Simple Features profile van GML 3.2 is daarom een andere werkwijze gekozen. Een GML applicatieschema dat voldoet aan een bepaald level van het Simple Features profile, moet hoewel de GML standaard niet volledig hoeft te worden ondersteund, de volledige GML XSD en de gmlsfLevels.xsd importeren en in de header aangeven welk SF level is toegepast. Dit dient te gebeuren door een annotation op te nemen binnen het schema element:

<pre class="example">
&lt;schema xmlns="http://www.w3.org/2001/XMLSchema"
        xmlns:gmlsf="http://www.opengis.net/gmlsf/2.0">
  &lt;import namespace="http://www.opengis.net/gml/3.2"
          schemaLocation="http://schemas.opengis.net/gml/3.2.1/gml.xsd"/>
  &lt;import namespace="http://www.opengis.net/gmlsf/2.0"
          schemaLocation="http://schemas.opengis.net/gmlsfProfile/2.0/gmlsfLevels.xsd"/>
  &lt;annotation>
    &lt;appinfo source="http://schemas.opengis.net/gmlsfProfile/2.0/gmlsfLevels.xsd">
      &lt;!--hier een 0, 1 of 2 invullen-->
      &lt;gmlsf:ComplianceLevel>2&lt;/gmlsf:ComplianceLevel>
    &lt;/appinfo>
  &lt;/annotation>
  ...
&lt;/schema>
</pre>

In plaats van een absolute URL naar de locatie van de schema’s in de schema repository van de OGC, is het ook toegestaan een absolute of relatieve URL naar een andere locatie te gebruiken, zolang het schema maar opgehaald kan worden.

Het is toegestaan om andere application schema’s te importeren, maar alleen als die voldoen aan hetzelfde Simple Features profile niveau of een lager niveau (en dus minder complex zijn) en dit op de voorgeschreven manier aangeven in de header.

Om te controleren of een GML bestand voldoet aan de regels van het Simple Features profile, kan de GML xsd niet worden gebruikt omdat er geen gestripte versie meer beschikbaar is. In plaats daarvan wordt aangeraden om een <a href="http://www.schematron.com/">Schematron</a> validatie te gebruiken. Voor SF2 is een document met Schematron regels beschikbaar in Annex E van het Simple Features profile for GML. Deze regels zijn beschreven in het volgende hoofdstuk, en zijn als validatie ook <a href="http://schemas.opengis.net/gmlsfProfile/2.0/gmlsfL2.sch">beschikbaar in de schema repository van de OGC</a> en de <a href="http://validatie.geostandaarden.nl">online validator van Geonovum</a>.
