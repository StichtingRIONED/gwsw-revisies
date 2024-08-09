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



## Nieuwe GWSW-concepten voor het deelmodel GWSW-Revisies

| Naam | URI | Definitie | Opmerking |
|------|-----|-----------|-----------|
| a    | b   | c         |           |


  Definitie datamodel Inmeetproject GWSW-Opera (20240115)

  - Algemeen.csv
    - Project_Id Opdrachtgever Contractnummer Projectomschrijving ProjectAdministratorOpdrachtgever

  - Deksel.csv
    - Knooppuntreferentie SoortDeksel VormDeksel LengteDeksel BreedteDeksel MateriaalDeksel MeldingDeksel Opmerking

  -  Knooppunt.csv
    - SoortPut VormPut BreedtePut LengtePut MateriaalPut Stroomprofiel Knooppuntreferentie X_coordinaat Y_coordinaat Z_coordinaat HoogtePut
    - StatusFunctioneren Stelsel Constructieonderdeel MeldingPut WijzeVanInwinning DatumInwinning Waterstand Stellaag Fotoreferentie Drempelniveau Opmerking

  -  Leiding.csv
    - Leiding_id BeginpuntLeiding EindpuntLeiding BobBeginpuntLeiding BobEindpuntLeiding BbbBeginpuntLeiding BbbEindpuntLeiding StatusFunctioneren Stelsel 
    - Leidingtype VormLeiding HoogteLeiding BreedteLeiding MateriaalLeiding MeldingLeiding Fotoreferentie WijzeVanInwinning DatumInwinning Opmerking


<div class="example-dataset"><div class="example-title marker">Dataset: Voorbeeld inmeetproject</div><pre>

# Algemeen: heen en terug
<i01> rdfs:label <Algemeen.Project_id> ;
      rdf:type opera:Inmeetproject ;
      gwsw:isOutputOf [ rdf:type gwsw:Opdrachtgever ; rdfs:label <Algemeen.Opdrachtgever> ; ] ;
      gwsw:hasAspect [ rdf:type opera:Contractnummer ; gwsw:hasValue <Algemeen.Contractnummer> ; ] ;
      gwsw:isOutputOf [ rdf:type gwsw:Contactpersoon ; rdfs:label <Algemeen.ProjectAdministratorOpdrachtgever> ; ] ;
      rdfs:comment <Algemeen.Projectomschrijving> .

# MetingKnooppunt: heen en terug
<i10> gwsw:isPartOf <i01> ; 
      rdf:type opera:MetingKnooppunt .

# MetingKnooppunt: heen
<i10> gwsw:hasInput <i11> .

# MetingKnooppunt: terug (gebruik een andere URI voor i11, ook bij hetzelfde knooppunt) 
<i10> gwsw:hasOutput <i11> ;
      gwsw:hasAspect [ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference <Knooppunt.WijzeVanInwinning>; ] ;
      gwsw:hasAspect [ rdf:type gwsw:DatumInwinning ; gwsw:hasValue <Knooppunt.DatumInwinning> ; ] ;
      rdfs:seeAlso <Knooppunt.FotoReferentie> .

# Knooppunt heen en terug
<i11> rdf:type <Knooppunt.SoortPut> ;
      rdfs:label <Knooppunt.Knooppuntreferentie> ;
      gwsw:hasAspect [ rdf:type gwsw:VormPut ; gwsw:hasReference <Knooppunt.VormPut> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:BreedtePut ; gwsw:hasValue <Knooppunt.BreedtePut> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:LengtePut ; gwsw:hasValue <Knooppunt.LengtePut> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:MateriaalPut ; gwsw:hasReference <Knooppunt.MateriaalPut> ; ] ;
      gwsw:hasPart [ rdf:type gwsw:Stroomprofiel; gwsw:hasAspect [ rdf:type gwsw:VormStroomprofiel ; gwsw:hasReference <Knooppunt.Stroomprofiel> ; ] ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:HoogtePut ; gwsw:hasValue <Knooppunt.HoogtePut> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference <Knooppunt.StatusFunctioneren> ; ] ;
      gwsw:isPartOf [ rdf:type <Knooppunt.Stelsel>; ] ;
      gwsw:hasPart [ rdf:type <Knooppunt.Constructieonderdeel>; gwsw:hasAspect [ rdf:type gwsw:Drempelniveau ; gwsw:hasValue <Knooppunt.Drempelniveau> ; ]] .

# Knooppunt heen en terug: de verbinding
<i11> gwsw:hasAspect <i12> .
<i12> rdf:type gwsw:Putorientatie ;
      gwsw:hasAspect [ rdf:type gwsw:Punt ; gwsw:hasValue "gml:Point <Knooppunt.X_coordinaat> <Knooppunt.Y_coordinaat> <Knooppunt.Z_coordinaat>" ; ] .

# Knooppunt terug
<i11> gwsw:hasAspect [ rdf:type opera:Waterstand ; gwsw:hasValue <Knooppunt.Waterstand> ; ] ;
      gwsw:hasPart [ rdf:type opera:Stellaag; gwsw:hasAspect [ rdf:type opera:HoogteStellaag ; gwsw:hasValue <Knooppunt.Stellaag> ; ]] ;
      gwsw:hasAspect [ rdf:type opera:MeldingKnooppunt ; gwsw:hasValue <Knooppunt.MeldingPut> ; ] ;
      rdfs:comment <Knooppunt.Opmerking> .

# Deksel heen en terug 
<i13> rdf:type <Deksel.SoortDeksel> ;
      gwsw:isPartOf <i11> ; # Afleiden uit <Deksel.Knooppuntreferentie>
      gwsw:hasAspect [ rdf:type gwsw:VormDeksel ; gwsw:hasReference <Deksel.VormDeksel> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:BreedteDeksel ; gwsw:hasValue <Deksel.BreedteDeksel> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:LengteDeksel ; gwsw:hasValue <Deksel.LengteDeksel> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:MateriaalDeksel ; gwsw:hasReference <Deksel.MateriaaDeksel> ; ] ;
      gwsw:hasAspect [ rdf:type opera:MeldingDeksel ; gwsw:hasValue <Deksel.MeldingDeksel> ; ] ;
      rdfs:comment <Deksel.Opmerking> .

# MetingLeiding: heen en terug
<i20> gwsw:isPartOf <i01> ; 
      rdf:type opera:MetingLeiding .

# MetingLeidingt: heen
<i20> gwsw:hasInput <i21> .

# MetingLeiding: terug (gebruik een andere URI voor i21, ook bij dezelfde leiding) 
<i20> gwsw:hasOutput <i21> ;
      gwsw:hasAspect [ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference <Leiding.WijzeVanInwinning>; ] ;
      gwsw:hasAspect [ rdf:type gwsw:DatumInwinning ; gwsw:hasValue <Leiding.DatumInwinning> ; ] ;
      rdfs:seeAlso <Leiding.FotoReferentie> .

# Leiding heen en terug
<i21> rdf:type <Leiding.Leidingtype> ;
      rdfs:label <Leiding.Leiding_id> ;
      gwsw:hasAspect [ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference <Leiding.StatusFunctioneren> ; ] ;
      gwsw:isPartOf [ rdf:type <Leiding.Stelsel>; ] ;
      gwsw:hasAspect [ rdf:type gwsw:VormLeiding ; gwsw:hasReference <Leiding.VormLeiding> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:HoogteLeiding ; gwsw:hasValue <Leiding.HoogteLeiding> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:BreedteLeiding ; gwsw:hasValue <Leiding.BreedteLeiding> ; ] ;
      gwsw:hasAspect [ rdf:type gwsw:MateriaalLeiding ; gwsw:hasReference <Leiding.MateriaalLeiding> ; ] .

# Leiding heen en terug: de verbinding
<i21> gwsw:hasAspect <i22> .
<i22> rdf:type gwsw:Leidingorientatie ;
      # Afleiden uit <Leiding.BeginpuntLeiding> en <Leiding.EindpuntLeiding> 
      gwsw:hasAspect [ rdf:type gwsw:Lijn ; gwsw:hasValue "gml:LineString <Knooppunt.X_coordinaat> <Knooppunt.Y_coordinaat> <Knooppunt.Z_coordinaat>, <Knooppunt.X_coordinaat> <Knooppunt.Y_coordinaat> <Knooppunt.Z_coordinaat>" ; ] ;
      gwsw:hasPart <i23> ;
      gwsw:hasPart <i24> .
<i23> rdf:type gwsw:BeginpuntLeiding ; 
      gwsw:hasConnection <i12> ; # Afleiden uit <Leiding.BeginpuntLeiding>
      gwsw:hasAspect [ rdf:type gwsw:BobBeginpuntLeiding ; gwsw:hasValue <Leiding.BobBeginpuntLeiding> ; ] ;
      gwsw:hasAspect [ rdf:type opera:BbbBeginpuntLeiding ; gwsw:hasValue <Leiding.BbbBeginpuntLeiding> ; ] .
<i24> rdf:type gwsw:EindpuntLeiding ; 
      gwsw:hasConnection <i12> ; # Afleiden uit <Leiding.EindpuntLeiding> <i12> is natuurlijk een andere put
      gwsw:hasAspect [ rdf:type gwsw:BobEindpuntLeiding ; gwsw:hasValue <Leiding.BobEindpuntLeiding> ; ] ;
      gwsw:hasAspect [ rdf:type opera:BbbEindpuntLeiding ; gwsw:hasValue <Leiding.BbbEindpuntLeiding> ; ] .

  # Leiding terug
<i21> gwsw:hasAspect [ rdf:type opera:MeldingLeiding ; gwsw:hasValue <Leiding.MeldingLeiding> ; ] ;
      rdfs:comment <Leiding.Opmerking> .
 </pre></div>



