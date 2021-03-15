# GML SF2: Nederlands profiel op GML 3.2

Vanwege de voordelen van voldoen aan internationale conventies en omdat het GML Simple Features profile level 2(SF2) bijna voldoet aan de eisen die er in Nederland gesteld worden is er besloten om SF2 als Nederlandse standaard voor de implementatie van GML 3.2.1 te nemen. In het vorige hoofdstuk is de inhoud van dat profiel toegelicht. In dit hoofdstuk wordt het profiel beschreven middels businessrules die van toepassing zijn op een GML document dat voldoet aan SF 2. De businessrules zijn opgesteld in Schematron, een taal ontwikkeld voor het valideren van XML documenten.

## Introductie Schematron

Schematron gaat in tegenstelling tot XML Schema niet uit van een definitie van de complete XML structuur van een set documenten, maar stelt in staat om regels op te stellen voor specifieke onderdelen van XML documenten. Schematron kan daardoor gebruikt worden om heel gericht enkele regels te controleren. Voor het opstellen van de regels zijn er veel mogelijkheden, waaronder het toetsen van onderlinge afhankelijkheden tussen onderdelen van de XML structuur, wat met XML Schema niet mogelijk is. Terwijl XML Schema te vergelijken is met UML, is Schematron verwant aan de Object Constraint Language (OCL). Beide zijn de implementatie van hun meer conceptuele equivalent.

De in Schematron opgestelde regels kunnen voor validatie van XML (GML) documenten worden gebruikt. Een deel van de bekende XML editors kan validaties tegen Schematron regels uitvoeren of de Schematron controle kan worden uitgevoerd als XSLT transformatie. Validatie tegen de Schematron implementatie van SF2 kan ook <a href="http://validatie.geostandaarden.nl/etf-webapp/testruns/create-direct?testProjectId=8089ca7a-8722-3119-9ec9-661205a743f4">via de Geonovum validator</a> worden uitgevoerd.

De nu volgende paragraaf geeft de Schematron regels die voor het valideren tegen GML SF2 zijn opgesteld. Door de toelichting bij elke regel wordt duidelijk gemaakt hoe op dat bepaalde onderwerp SF2 verschilt van de complete GML standaard.

## Schematron business rules voor Nederlands profiel

De hieronder weergegeven business rules omvatten alleen de SF2 regels. De controle beperkt zich tot met name de restricties met betrekking tot geometrietypen. De restricties op XML Schema, die voor SF0 en SF1 gelden, zijn niet opgenomen. Deze Schematron regels kunnen echter wel gebruikt worden om tenminste de geometrie restricties voor een SF0 of SF1 bestand te valideren. Deze zijn immers voor SF0, SF1 en SF2 gelijk.

Deze schematron regels zijn ontleend aan het OGC Simple Feature Profile for GML. De nieuwste versie is te vinden op
http://schemas.opengis.net/gmlsfProfile/2.0/.

**Geen gebruik van gml:metaDataProperty.**

<pre>
&lt;sch:assert test="not(gml:metaDataProperty)">
    This profile prohibits use of gml:metaDataProperty elements for referencing metadata 
    in instance documents.
&lt;/sch:assert>
</pre>

**Geen topologie elementen**

Geen voorkomens van `Node`, `Edge`, `Face`, `TopoSolid`, `TopoPoint`, `TopoCurve`, `TopoSurface`, `TopoVolume`, or `TopoComplex`.

<pre>
&lt;sch:assert test="not(
    self::gml:Node|self::gml:Edge|self::gml:Face|self::gml:TopoSolid |self::gml:TopoPoint|
    self::gml:TopoCurve|self::gml:TopoSurface |self::gml:TopoVolume|self::gml:TopoComplex)">
        Spatial properties are limited to the set of geometric types consisting of point,
        curve with linear and/or circular arc interpolation, planar surface, or aggregates
        thereof. Spatial topology is excluded.
&lt;/sch:assert>
</pre>

**Interpolatie van curve segmenten**

Toegestaan binnen een `gml:Curve` zijn `LineStringSegment`, `Arc`, `Circle`, or `CircleByCenterPoint`

<pre>
&lt;sch:assert test="not(
    self::gml:Curve) or self::gml:Curve/gml:segments[gml:LineStringSegment|gml:Arc|gml:Circle|
    gml:CircleByCenterPoint]">
        Curves (standalone or within surfaces) must have linear and/or circular arc interpolation 
        (LineString, Curve with Arc, Circle or CircleByCenterpoint segments)
&lt;/sch:assert>
</pre>

**Surface is Polygon of Surface.**

Geen voorkomens van `OrientableSurface`, `CompositeSurface`, `PolyhedralSurface`, `Tin`, of `TriangulatedSurface`.

<pre>
&lt;sch:assert test="not(
    self::gml:OrientableSurface|self::gml:CompositeSurface|self::gml:PolyhedralSurface|
    self::gml:Tin|self::gml:TriangulatedSurface)">
        Planar surface types are restricted to Polygon or Surface elements.
&lt;/sch:assert>
</pre>

**Beperkt aantal geometrytypen.**

Geen `Solid`, `MultiSolid`, `CompositeSolid`, `CompositeCurve` of `Grid`.

<pre>
&lt;sch:assert test="not(
    self::gml:Solid|self::gml:MultiSolid|self::gml:CompositeSolid|self::gml:CompositeCurve|
    self::gml:Grid)">
        Supported geometry types are restricted to point, curve with linear and/or circular arc 
        interpolation, planar surface, or aggregates thereof.
&lt;/sch:assert>
</pre>

**Punt coordinaten met gml:pos element.**

Binnen een `gml:Point` moeten de coordinaten zijn opgenomen in een `gml:pos` element.

<pre>
&lt;sch:assert test="count(self::gml:Point/gml:pos) = count(self::gml:Point/*)">
    Geometry coordinates shall only be specified using the gml:pos element for gml:Point.
&lt;/sch:assert>
</pre>

**Gml:CircleByCenterPoint gebruikt gml:pos element.**

Binnen een `gml:CircleByCenterPoint` moeten de coordinaten zijn opgenomen in een `gml:pos` element.

<pre>
&lt;sch:assert test="count(
    self::gml:CircleByCenterPoint/gml:pos|self::gml:CircleByCenterPoint/gml:radius) =
    count(self::gml:CircleByCenterPoint/*)">
        Geometry coordinates shall only be specified using the gml:pos element
        for gml:CircleByCenterPoint.
&lt;/sch:assert>
</pre>

**Gml:posList element voor coordinaten in andere dan punt geometrien.**

**Gml:LineString:**

Binnen een `gml:LineString` moeten de coordinaten zijn opgenomen in een `gml:posList` element.

<pre>
&lt;sch:assert test="count(
    self::gml:LineStringSegment/gml:posList) = count(self::gml:LineStringSegment/*)">
        Geometry coordinates shall only be specified using the gml:posList element 
        for gml:LineStringSegment.
&lt;/sch:assert>
</pre>

**Gml:LinearRing**

Binnen een `gml:LinearRing` moeten de coordinaten zijn opgenomen in een `gml:posList` element.

<pre>
&lt;sch:assert test="count(
    self::gml:LinearRing/gml:posList) = count(self::gml:LinearRing/*)">
    Geometry coordinates shall only be specified using the gml:posList element for gml:LinearRing.
&lt;/sch:assert>
</pre>

**Gml:Arc**

Binnen een `gml:Arc` moeten de coordinaten zijn opgenomen in een `gml:posList` element.

<pre>
&lt;sch:assert test="count(
    self::gml:Arc/gml:posList) = count(self::gml:Arc/*)">
        Geometry coordinates shall only be specified using the gml:posList element for 
        gml:Arc.
&lt;/sch:assert>
</pre>

**gml:Circle**

Binnen een `gml:Circle` moeten de coordinaten zijn opgenomen in een `gml:posList` element.

<pre>
&lt;sch:assert test="count(
    self::gml:Circle/gml:posList) = count(self::gml:Circle/*)">
        Geometry coordinates shall only be specified using the gml:posList element for 
        gml:Circle.
&lt;/sch:assert>
</pre>

**Toegestane container elementen:**

**gml:pointMember**

<pre>
&lt;sch:assert test="not(self::gml:MultiPoint/gml:pointMembers)">
    This profile restricts instance documents to using the property container gml:pointMember
    for the MultiPoint geometry type.
&lt;/sch:assert>
</pre>

**gml:curveMember**

<pre>
&lt;sch:assert test="not(self::gml:MultiCurve/gml:curveMembers)">
    This profile restricts instance documents to using the property container gml:curveMember 
    for the MultiCurve geometry type.
&lt;/sch:assert>
</pre>

**gml:surfaceMember**

<pre>
&lt;sch:assert test="not(self::gml:MultiSurface/gml:surfaceMembers)">
    This profile restricts instance documents to using the property container gml:surfaceMember 
    for the MultiSurface geometry type.
&lt;/sch:assert>
</pre>

**gml:geometryMember**

<pre>
&lt;sch:assert test="not(self::gml:MultiGeometry/gml:geometryMembers)">
    This profile restricts instance documents to using the property container gml:geometryMember 
    for the MultiGeometry geometry type.
&lt;/sch:assert>
</pre>

**Surface elementen zijn altijd gml:PolygonPatch**

<pre>
&lt;sch:assert test="count(
    self::gml:Surface/gml:patches/gml:PolygonPatch) = count(self::gml:Surface/gml:patches/*)">
        The content of gml:Surface elements is restricted to gml:PolygonPatch patches.
&lt;/sch:assert>
</pre>

**De dimensie van het coordinaatreferentiesysteem is 1, 2 of 3**

<pre>
&lt;sch:assert test="not(self::*/@srsDimension > 3)">
    coordinate reference systems may have 1, 2 or 3 dimensions
&lt;/sch:assert>
</pre>
