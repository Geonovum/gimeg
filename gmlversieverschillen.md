# GML 3.2.1 en GML 3.1.1

<aside class="issue">De formatting in dit hoofdstuk moet nog gecorrigeerd wroden hier en daar (bv geneste lijsten gaan niet goed)</aside>

In deze bijlage wordt ingegaan op de verschillen tussen de GML versies 3.2.1 en 3.1.1.

## Inleiding
In de praktijk zijn er momenteel drie versies van GML in gebruik:
- GML 2.1.2 (2002)
- GML 3.1.1 (2004/2005)
- GML 3.2.1 (2007)

GML 3.3 is op het moment van schrijven net uitgekomen (begin 2012). Deze versie is volledig backwards compatible met GML 3.2.1 en bestaat uit enkele uitbreidingen die in nieuwe namespaces zijn gedefinieerd. GML 3.3 wordt hier verder buiten beschouwing gelaten.

In Nederland is tot nu toe met name gestandaardiseerd op GML 3.1.1. De  overstap naar GML 3.2.1 wordt pas de laatste tijd gemaakt, omdat eerder deze versie nog niet altijd ondersteund werd door software applicaties. Sommige nieuwe standaarden maken nog steeds gebruik van GML 3.1.1: dit geldt bijvoorbeeld voor IMGeo 2.0 vanwege de aansluiting met [CityGML](http://www.opengeospatial.org/standards/citygml) (een OGC standaard voor 3D geo-informatie), waarin een afhankelijkheid met GML 3.1.1 zit.

Dit appendix beschrijft de verschillen tussen 3.1.1 en 3.2.1, zodat:
- De afweging tussen beide versies goed gemaakt kan worden;
- De impact duidelijk wordt voor zij die de overstap van 3.1.1 naar 3.2.1 overwegen;
- Gebruikers van GML 3.1.1 de standaard zo kunnen toepassen dat de stap naar 3.2.1 als het moment daar is zo klein mogelijk wordt.

Alleen de verschillen die GML onderdelen raken die in Nederland waarschijnlijk of mogelijk gebruikt worden, zijn hier opgesomd. Een volledige beschrijving van de verschillen is te vinden in de officiële [Revision Notes voor GML 3.2.1](http://portal.opengeospatial.org/files/?artifact_id=26765) (OGC documentnummer 07-061) , of in het hierop gebaseerde document Analysis of changes between GML 3.1.1 and GML 3.2.1, te vinden op de website van Geonovum.

Hieronder volgt een opsomming en beschrijving van de belangrijkste verschillen.

## Waar iedereen mee te maken krijgt

### Importeren van het GML schema en GML profielen
Vanaf GML 3.2.1 moet een GML application schema het volledige GML schema importeren. In GML 3.1.1 was het nog toegestaan een gestript GML schema te importeren. Dit onderwerp  is al behandeld in paragraaf 3.7.

### XML namespace
De XML namespace van het GML schema ("`http://www.opengis.net/gml`") is gewijzigd naar "`http://www.opengis.net/gml/3.2`".

Dit betekent dat alle componenten van GML nu in een andere namespace staan en dus andere componenten zijn.
- Dit heeft een kleine of grote impact op software applicaties die GML 3.1.1 ondersteunen, afhankelijk van de wijze van implementeren.
- GML bestanden in 3.1.1 kunnen eenvoudig handmatig worden aangepast als de namespace declaratie op één plek in de header staat. Als de wijziging op meer plekken moet worden doorgevoerd kan dit geautomatiseerd gebeuren.
- GML application schemas moeten (uiteraard) het GML 3.2.1 schema met de nieuwe namespace importeren in plaats van het GML 3.1.1 schema met de oude namespace. Dit heeft alleen impact op de header van het schema.

### Abstracte elementen hernoemd
De "_" (underscore) in element namen om aan te geven dat ze abstract zijn, is vervangen door het beginnen van de naam met "Abstract".

Dit betekent dat bijvoorbeeld het GML element _Feature is hernoemd naar AbstractFeature.
- In GML application schemas die handmatig van 3.1.1 naar 3.2.1 gemigreerd worden, moet bij alle elementen die afgeleid zijn van een abstract GML element, de naam van het abstracte GML element worden gewijzigd.
- Kan impact hebben op software.
- Geen impact op GML documenten.

### gml:id verplicht
GML objecten hebben identiteit en daarom is het attribuut gml:id verplicht geworden. Ook geometrieën zoals gml:Point, gml:Curve en gml:Surface worden in GML gezien als objecten en krijgen nu een verplicht gml:id.

Gevolgen:
- Software die wordt gebruikt om GML documenten te maken, moet nu een gml:id aanmaken, met een binnen het document unieke waarde, voor elk GML object. In GML 3.1.1 hoefde dit niet en vaak werd dit dan ook niet gedaan voor objecten waarnaar niet werd verwezen, bijvoorbeeld voor een geometrie object binnen een feature.
- GML documenten die van 3.1.1 naar 3.2.1 worden gemigreerd, moeten bij elk object dat nog geen gml:id had, er een toevoegen met een unieke waarde. Dit kan geautomatiseerd gedaan worden.
- Geen gevolgen voor GML application schemas.

**Aanbeveling**: wie nu nog GML 3.1.1 gebruikt maar binnen afzienbare tijd naar GML 3.2.1 (of GML 3.3) wil overstappen, kan het beste vast beginnen het gml:id overal op te nemen waar dit in GML 3.2.1 verplicht wordt. 

### Feature collection en andere collection types geschrapt
Alle in GML 3.1.1 aanwezige collection typen, inclusief die voor feature collections, zijn geschrapt. Het is nu de bedoeling date en GML application schema zelf een collection definieert als dit nodig is, met als basis de nieuwe typen gml:AbstractMemberType en gml:AbstractFeatureMemberType. 

Dit heeft gevolgen voor alle GML toepassingen die collecties gebruiken. Zowel de software die collecties maakt of leest, als het GML applicatie schema en GML documenten moeten worden aangepast.

## Andere verschillen met mogelijke gevolgen

### Normatieve referenties naar andere standaarden
Een aantal van de normatieve verwijzingen naar aan GML gerelateerde standaard documenten verwijzen nu naar een nieuwere versie daarvan. Hiervan zijn er slechts drie mogelijk relevant voor NEN 3610 gebruikers:
- ISO 19111:2007, Geographic Information — Spatial referencing by coordinates. De 2007 revisie van deze standaard is significant gewijzigd.
- ISO/TS 19139:2007, Geographic Information — Metadata — XML schema implementation: Metadata elementen uit ISO 19115 worden nu geïmplementeerd door gebruik te maken van ISO/TS 19139.
- ISO/IEC 19757-3:2006, Document Schema Definition Languages (DSDL) — Part 3: Rule-based validation — Schematron. Er zijn verschillen tussen de hiervoor gebruikte versie en de in GML 3.2.1 gebruikte door ISO goedgekeurde versie.

### Metadata eigenschappen
gml:_MetaData en gml:metaDataProperty zijn geschrapt en vervangen door een abstract property type als basis waarop men eigen metadata eigenschappen kan definiëren. Men kan nu daardoor in het eigen GML applicatie schema afdwingen dat metadata wordt ingevuld. Door het eigen metadata element af te leiden van het daarvoor bestemde abstracte GML element kan software de metadata herkennen.

Gevolgen als deze GML 3.1.1 elementen gebruikt werden:
- GML applicatie schema moet worden aangepast door het definiëren van een eigen metadata element dat volgens de GML 3.2.1 voorschriften is afgeleid van het abstracte GML type;
- De GML 3.1.1 metadata property moet waar deze is gebruikt in GML documenten worden vervangen door het zelf gedefinieerde metadata element;
- Software die van het GML 3.1.1 metadata element gebruik maakte moet gewijzigd worden om het zelf gedefinieerde metadata element te ondersteunen.

### Hernoemde / vervangen eigenschappen
- Alle “*Name” elementen in het coordinate reference system schema zijn vervangen door gml:name en gebruiken nu dus gml:CodeType als type.
  - gml:axisName >gml:axisLabel
  - gml:fileName >gml:fileReference
  - gml:SequenceRulesNames >gml:SequenceRuleEnumeration.
- gml:StringOrRefType is geschrapt. Eigenschappen die een string of een verwijzing als inhoud hebben worden nu gecodeerd als twee aparte eigenschappen in plaats van één.

### Wijzigingen in geometrietypen
- Een aantal technische correcties zijn uitgevoerd op geometrietypen. Deze kunnen mogelijk gevolgen hebben voor software:
  - Gml:Envelope is expliciet gedefinieerd als zijnde geen geometrie door het in de substitutionGroup AbstractObject te zetten.
  - gml:CircleByCenterPointType is nu gedefinieerd als een restriction van
ArcByCenterPointType.
  - gml:Shell is toegevoegd als implementatie van ISO geometrietype GM_Shell.
  - Het interpolationType attribuut ontbrak op sommige segment typen en is daar toegevoegd.

### Wijziging in coordinate reference system dictionaries
De verwijzing in GML naar het gebruikte coördinaatreferentiesysteem (CRS) wordt meestal gedaan door de URN of EPSG code te gebruiken waaronder het bekend staat. Het is echter ook mogelijk de CRS expliciet te definiëren in een GML dictionary. Wie dit in GML 3.1.1 heeft gedaan, krijgt te maken met een wijziging die niet backwards compatible is.

De encoding is ingrijpend gewijzigd om te voldoen aan ISO 19111:2007 en de GML coderingsconventies.

### Ondersteuning voor Void (ISO/IEC 11404)
Het weglaten van een kenmerk (middels minOccurs=”0” in het schema) is niet hetzelfde als Void zoals gedefinieerd in ISO/IEC 11404:1996. GML 3.2.1 is aangepast om Void correct te implementeren:
- GML 3.2.1 is uitgebreid met een uitleg hoe xsi:nil moet worden gebruikt als implementatie van Void.
- Gml:Null is geschrapt.
- Het type gml:NilReasonType is toegevoegd voor het kunnen opnemen van metadata over de reden van een ontbrekende waarde.

Dit heeft gevolgen voor GML application schemas die gebruik maakten van gml:Null of een eigen implementatie van Void hanteerden. Het GML application schema, GML documenten en software die het GML application schema ondersteunt, moeten aangepast worden.