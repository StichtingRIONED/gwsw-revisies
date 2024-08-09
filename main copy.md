# GWSW Revisies

<style>
  .symbolSmall{width:20px;height:20px;margin-right:1em;vertical-align:middle}
  .symbol{width:30px;height:30px;margin-right:1em;vertical-align:middle}
</style>

Stichting RIONED is initiatiefnemer en eigenaar van dit GitHub-project, Eric Oosterom is de verantwoordelijk projectmanager. 

Vragen over deze website en het GWSW kunt u stellen via gwsw@rioned.org. 

# Inleiding

De voornaamste initiator van dit deelmodel is de GWSW-Opera organisatie. De basis ligt bij een PoC gericht op het ontwikkelen en toetsen van het inmeetproces, dus de gegevensuitwisseling van de landmeter naar de beheerder. 

# Doel en toepassing

Ondersteuning bij revisies van stedelijk water voorzieningen. 
Het efficient en effectief verwerken van inmetingen door de landmeter.

# Gegevensmodel inmeetproject

## Inmeetproject in schema

<img src="media/Schema Inmeetproject.jpg" style="width:100%;height:50%" />

## Gegevens in het deelmodel GWSW-Revisies

Bij een inmeetproject worden de volgende gegevens uitgewisseld (aangeduid met de URI):

**Algemeen**  
Project_Id, Opdrachtgever, Contractnummer, Projectomschrijving, ProjectAdministratorOpdrachtgever

**Deksel**  
Knooppuntreferentie, SoortDeksel, VormDeksel, LengteDeksel, BreedteDeksel, MateriaalDeksel, MeldingDeksel, Opmerking

**Knooppunt** (Put of Bouwwerk) 
SoortPut VormPut BreedtePut LengtePut MateriaalPut Stroomprofiel Knooppuntreferentie X_coordinaat Y_coordinaat Z_coordinaat HoogtePut
StatusFunctioneren Stelsel Constructieonderdeel MeldingPut WijzeVanInwinning DatumInwinning Waterstand Stellaag Fotoreferentie Drempelniveau Opmerking

**Leiding**
Leiding_id BeginpuntLeiding EindpuntLeiding BobBeginpuntLeiding BobEindpuntLeiding BbbBeginpuntLeiding BbbEindpuntLeiding StatusFunctioneren Stelsel 
Leidingtype VormLeiding HoogteLeiding BreedteLeiding MateriaalLeiding MeldingLeiding Fotoreferentie WijzeVanInwinning DatumInwinning Opmerking


Veel URI's staan al in het GWSW datamodel, de volgende URI's zijn nieuw:


| URI | Naam | Definitie | Opmerking |
|------|-----|-----------|-----------|
| a    | Contractnummer   | c         |           |


<div class="example-dataset"><div class="example-title marker">Dataset: Voorbeeld inmeetproject</div><pre>

{i01}  Algemeen heen en terug

      rdfs:label {algemeen.Project_id} ;
      rdf:type opera:Inmeetproject ;
      gwsw:isOutputOf [ rdf:type gwsw:Opdrachtgever ; rdfs:label {algemeen.Opdrachtgever} ; ] ;
      gwsw:hasAspect [ rdf:type opera:Contractnummer ; gwsw:hasValue {algemeen.Contractnummer} ; ] ;
      gwsw:isOutputOf [ rdf:type gwsw:Contactpersoon ; rdfs:label {algemeen.ProjectAdministratorOpdrachtgever} ; ] ;
      rdfs:comment {algemeen.Projectomschrijving} .

{i10}  MetingKnooppunt: heen en terug

      gwsw:isPartOf {i01} ; 
      rdf:type opera:MetingKnooppunt .

{i10}  MetingKnooppunt: heen
      
      gwsw:hasInput {i11} .

{i10}  MetingKnooppunt: terug (gebruik een andere URI voor i11, ook bij hetzelfde knooppunt) 

      gwsw:hasOutput {i11} ;
      gwsw:hasAspect [ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference {knooppunt.WijzeVanInwinning}; ] ;
      gwsw:hasAspect [ rdf:type gwsw:DatumInwinning ; gwsw:hasValue {knooppunt.DatumInwinning} ; ] ;
      rdfs:seeAlso {knooppunt.FotoReferentie} .

{i11}  Knooppunt heen en terug

      rdf:type {knooppunt.SoortPut} ;
      rdfs:label {knooppunt.Knooppuntreferentie} ;
      gwsw:hasAspect [ rdf:type gwsw:VormPut ; gwsw:hasReference {knooppunt.VormPut} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:BreedtePut ; gwsw:hasValue {knooppunt.BreedtePut} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:LengtePut ; gwsw:hasValue {knooppunt.LengtePut} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:MateriaalPut ; gwsw:hasReference {knooppunt.MateriaalPut} ; ] ;
      gwsw:hasPart [ rdf:type gwsw:Stroomprofiel; gwsw:hasAspect [ rdf:type gwsw:VormStroomprofiel ; gwsw:hasReference {knooppunt.Stroomprofiel} ; ] ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:HoogtePut ; gwsw:hasValue {knooppunt.HoogtePut} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference {knooppunt.StatusFunctioneren} ; ] ;
      gwsw:isPartOf [ rdf:type {knooppunt.Stelsel}; ] ;
      gwsw:hasPart [ rdf:type {knooppunt.Constructieonderdeel}; gwsw:hasAspect [ rdf:type gwsw:Drempelniveau ; gwsw:hasValue {knooppunt.Drempelniveau} ; ] ; ] .

{i11}  Knooppunt heen en terug: de verbinding

      gwsw:hasAspect {i12} .
{i12} 
      rdf:type gwsw:Putorientatie ;
      gwsw:hasAspect [ rdf:type gwsw:Punt ; gwsw:hasValue "gml:Point {knooppunt.X_coordinaat} {knooppunt.Y_coordinaat} {knooppunt.Z_coordinaat}" ; ] .

{i11}  Knooppunt terug

      gwsw:hasAspect [ rdf:type opera:Waterstand ; gwsw:hasValue {knooppunt.Waterstand} ; ] ;
      gwsw:hasPart [ rdf:type opera:Stellaag; gwsw:hasAspect [ rdf:type opera:HoogteStellaag ; gwsw:hasValue {knooppunt.Stellaag} ; ] ; ] ;
      gwsw:hasAspect [ rdf:type opera:MeldingKnooppunt ; gwsw:hasValue {knooppunt.MeldingPut} ; ] ;
      rdfs:comment {knooppunt.Opmerking} .

{i13}  Deksel heen en terug 

      rdf:type {deksel.SoortDeksel} ;
      gwsw:isPartOf {i11} ; \# Afleiden uit {deksel.Knooppuntreferentie}
      gwsw:hasAspect [ rdf:type gwsw:VormDeksel ; gwsw:hasReference {deksel.VormDeksel} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:BreedteDeksel ; gwsw:hasValue {deksel.BreedteDeksel} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:LengteDeksel ; gwsw:hasValue {deksel.LengteDeksel} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:MateriaalDeksel ; gwsw:hasReference {deksel.MateriaaDeksel} ; ] ;
      gwsw:hasAspect [ rdf:type opera:MeldingDeksel ; gwsw:hasValue {deksel.MeldingDeksel} ; ] ;
      rdfs:comment {deksel.Opmerking} .

{i20}  MetingLeiding: heen en terug

      gwsw:isPartOf {i01} ; 
      rdf:type opera:MetingLeiding .


{i20}  MetingLeiding: heen

      gwsw:hasInput {i21} .


{i20}  MetingLeiding: terug (gebruik een andere URI voor i21, ook bij dezelfde leiding) 

      gwsw:hasOutput {i21} ;
      gwsw:hasAspect [ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference {leiding.WijzeVanInwinning}; ] ;
      gwsw:hasAspect [ rdf:type gwsw:DatumInwinning ; gwsw:hasValue {leiding.DatumInwinning} ; ] ;
      rdfs:seeAlso {leiding.FotoReferentie} .


{i21}  Leiding heen en terug

      rdf:type {leiding.Leidingtype} ;
      rdfs:label {leiding.Leiding_id} ;
      gwsw:hasAspect [ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference {leiding.StatusFunctioneren} ; ] ;
      gwsw:isPartOf [ rdf:type {leiding.Stelsel}; ] ;
      gwsw:hasAspect [ rdf:type gwsw:VormLeiding ; gwsw:hasReference {leiding.VormLeiding} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:HoogteLeiding ; gwsw:hasValue {leiding.HoogteLeiding} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:BreedteLeiding ; gwsw:hasValue {leiding.BreedteLeiding} ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:MateriaalLeiding ; gwsw:hasReference {leiding.MateriaalLeiding} ; ] .

{i21}  Leiding heen en terug: de verbinding
      
      gwsw:hasAspect {i22} .
{i22} 
      rdf:type gwsw:Leidingorientatie ;
      \# Afleiden uit {leiding.BeginpuntLeiding} en {leiding.EindpuntLeiding} 
      gwsw:hasAspect [ rdf:type gwsw:Lijn ; gwsw:hasValue "gml:LineString {knooppunt.X_coordinaat} {knooppunt.Y_coordinaat} {knooppunt.Z_coordinaat}, {knooppunt.X_coordinaat} {knooppunt.Y_coordinaat} {knooppunt.Z_coordinaat}" ; ] ;
      gwsw:hasPart {i23} ;
      gwsw:hasPart {i24} .
{i23} 
      rdf:type gwsw:BeginpuntLeiding ; 
      gwsw:hasConnection {i12} ; \# Afleiden uit {leiding.BeginpuntLeiding}
      gwsw:hasAspect [ rdf:type gwsw:BobBeginpuntLeiding ; gwsw:hasValue {leiding.BobBeginpuntLeiding} ; ] ;
      gwsw:hasAspect [ rdf:type opera:BbbBeginpuntLeiding ; gwsw:hasValue {leiding.BbbBeginpuntLeiding} ; ] .
{i24} 
      rdf:type gwsw:EindpuntLeiding ; 
      gwsw:hasConnection {i12} ; \# Afleiden uit {leiding.EindpuntLeiding} {i12} is natuurlijk een andere put
      gwsw:hasAspect [ rdf:type gwsw:BobEindpuntLeiding ; gwsw:hasValue {leiding.BobEindpuntLeiding} ; ] ;
      gwsw:hasAspect [ rdf:type opera:BbbEindpuntLeiding ; gwsw:hasValue {leiding.BbbEindpuntLeiding} ; ] .

{i21}  Leiding terug

      gwsw:hasAspect [ rdf:type opera:MeldingLeiding ; gwsw:hasValue {leiding.MeldingLeiding} ; ] ;
      rdfs:comment {leiding.Opmerking} .
 </pre> </div>



