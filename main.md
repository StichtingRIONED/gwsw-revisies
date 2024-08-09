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

## Projectmodel

<img src="media/Schema Inmeetproject.jpg" style="width:100%;height:50%" />

## Gegevensuitwisseling

Bij een inmeetproject worden de volgende gegevens uitgewisseld:

**Algemeen**  

| Veldnaam            | Waarde in RDF-termen                 | Opmerking                                  |
|---------------------|--------------------------------------|--------------------------------------------|
| NaamProject         | rdfs:label bij rev:Inmeetproject     | in Opera Project_Id                        |
| Opdrachtgever       | rdfs:label bij gwsw:Opdrachtgever    |                                            |
| Contractnummer      | gwsw:hasValue bij rev:Contractnummer |                                            |
| OmschrijvingProject | rdfs:comment bij rev:Inmeetproject   | in Opera Projectomschrijving               |
| Contactpersoon      | rdfs:label bij gwsw:Contactpersoon   | in Opera ProjectAdministratorOpdrachtgever |

**Deksel**  

| Veldnaam            | Waarde in RDF-termen                          | Opmerking                    |
|---------------------|-----------------------------------------------|------------------------------|
| NaamKnooppunt       | rdfs:label bij gwsw:Knooppunt                 | in Opera Knooppuntreferentie |
| TypeDeksel          | rdf:type van gwsw:Afdekking                   | in Opera SoortDeksel         |
| VormDeksel          | gwsw:hasReference bij gwsw:VormDeksel         |                              |
| LengteDeksel        | gwsw:hasValue bij gwsw:LengteDeksel           |                              |
| BreedteDeksel       | gwsw:hasValue bij gwsw:BreedteDeksel          |                              |
| MateriaalDeksel     | gwsw:hasReference bij gwsw:MateriaalDeksel    |                              |
| MeldingMetingDeksel | gwsw:hasReference bij rev:MeldingMetingDeksel | in Opera MeldingDeksel       |
| Opmerking           | gwsw:hasValue bij gwsw:Opmerking              | in Opera rdfs:comment        |

**Knooppunt** (Put of Bouwwerk)  

| Veldnaam               | Waarde in RDF-termen                                              | Opmerking             |
|------------------------|-------------------------------------------------------------------|-----------------------|
| TypeKnooppunt          | rdf:type van gwsw:Put of gwsw:Bouwwerk                            | in Opera SoortPut     |
| VormPut                | gwsw:hasReference bij gwsw:VormPut of gwsw:VormBouwwerk           |                       |
| BreedtePut             | gwsw:hasValue bij gwsw:BreedtePut of gwsw:BreedteBouwwerk         |                       |
| LengtePut              | gwsw:hasValue bij gwsw:LengtePut of gwsw:LengteBouwwerk           |                       |
| MateriaalPut           | gwsw:hasReference bij gwsw:MateriaalPut of gwsw:MateriaalBouwwerk |                       |
| Stroomprofiel          | gwsw:hasReference bij gwsw:Stroomprofiel                          |                       |
| Knooppuntreferentie    | rdfs:label bij gwsw:Knooppunt                                     |                       |
| X_coordinaat           | gwsw:hasValue bij gwsw:Punt                                       |                       |
| Y_coordinaat           | gwsw:hasValue bij gwsw:Punt                                       |                       |
| Z_coordinaat           | gwsw:hasValue bij gwsw:Punt                                       |                       |
| HoogtePut              | gwsw:hasValue bij gwsw:HoogtePut of gwsw:HoogteBouwwerk           |                       |
| StatusFunctioneren     | gwsw:hasReference bij gwsw:StatusFunctioneren                     |                       |
| Stelsel                | rdf:type bij gwsw:Stelsel                                         |                       |
| Constructieonderdeel   | rdf:type bij gwsw:Constructieonderdeel                            |                       |
| Drempelniveau          | gwsw:hasValue bijgwsw:Drempelniveau                               |                       |
| MeldingMetingKnooppunt | gwsw:hasReference bij rev:MeldingMetingKnooppunt                  | in Opera MeldingPut   |
| WijzeVanInwinning      | gwsw:hasReference bij gwsw:WijzeVanInwinning                      |                       |
| DatumInwinning         | gwsw:hasValue bij gwsw:DatumInwinning                             |                       |
| Waterstand             | gwsw:hasValue bij rev:Waterstand                                  |                       |
| HoogteStellaag         | gwsw:hasValue van gwsw:HoogteStellaag                             | Vanaf GWSW 1.6.1      |
| Fotoreferentie         | gwsw:seeAlso bij URI-knooppunt                                    |                       |
| Opmerking              | gwsw:hasValue bij gwsw:Opmerking                                  | in Opera rdfs:comment |

**Leiding**  

| Veldnaam             | Waarde in RDF-termen                           | Opmerking                     |
|----------------------|------------------------------------------------|-------------------------------|
| NaamLeiding          | rdfs:label bij gwsw:Leiding                    | in Opera Leiding_id           |
| NaamKnooppunt1       | gwsw:hasConnection met URI-BeginpuntLeiding    | in Opera Knooppuntreferentie1 |
| NaamKnooppunt2       | gwsw:hasConnection met URI-EindpuntLeiding     | in Opera Knooppuntreferentie2 |
| BobBeginpuntLeiding  | hasValue van gwsw:BobBeginpuntLeiding          |                               |
| BobEindpuntLeiding   | hasValue van gwsw:BobEindpuntLeiding           |                               |
| BbbBeginpuntLeiding  | hasValue van rev:BbbBeginpuntLeiding           |                               |
| BbbEindpuntLeiding   | hasValue van rev:BbbEindpuntLeiding            |                               |
| StatusFunctioneren   | gwsw:hasReference bij gwsw:StatusFunctioneren  |                               |
| Stelsel              | rdf:type van gwsw:Stelsel                      |                               |
| TypeLeiding          | rdf:type van gwsw:Leiding                      | in Opera Leidingtype          |
| VormLeiding          | gwsw:hasReference bij gwsw:Vorm                |                               |
| HoogteLeiding        | gwsw:hasValue bij gwsw:Hoogte                  |                               |
| BreedteLeiding       | gwsw:hasValue bij gwsw:Breedte                 |                               |
| MateriaalLeiding     | gwsw:hasReference bij gwsw:Materiaal           |                               |
| MeldingMetingLeiding | gwsw:hasReference bij rev:MeldingMetingLeiding | in Opera MeldingLeiding       |
| Fotoreferentie       | gwsw:seeAlso bij URI-knooppunt                 |                               |
| WijzeVanInwinning    | gwsw:hasReference bij gwsw:WijzeVanInwinning   |                               |
| DatumInwinning       | gwsw:hasValue bij gwsw:DatumInwinning          |                               |
| Opmerking            | gwsw:hasValue bij gwsw:Opmerking               | in Opera rdfs:comment         |

Veel URI's staan al in het GWSW datamodel, voor het deelmodel Revisies zijn een aantal nieuwe concepten uitgewerkt.
In de vorige tabellen zijn al enkele nieuwe concepten opgenomen, herkenbaar aan de prefix rev: .

Een overzicht van de nieuwe concepten (exclusief in deelmodel GWSW-Revisies ):

| URI                    | Naam                              | Definitie                                                         | Opmerking |
|------------------------|-----------------------------------|-------------------------------------------------------------------|-----------|
| Inmeetproject          | Inmeetproject                     |                                                                   |           |
| Contractnummer         | Contractnummer                    |                                                                   |           |
| MetingKnooppunt        | Meting knooppunt                  | Een meting van een put of bouwwerk                                |           |
| Waterstand             | Waterstand                        | De gemeten waterstand tov de bodem                                | \[mm]     |
| MeldingMetingKnooppunt | Melding bij meting knooppunt      | Voorgedefinieerde meldingen bij de meting van een put of bouwwerk |           |
| MeldingMetingDeksel    | Melding bij meting deksel         | Voorgedefinieerde meldingen bij de meting van een deksel          |           |
| MeldingMetingLeiding   | Melding bij meting knooppunt      | Voorgedefinieerde meldingen bij de meting van een leiding         |           |
| BbbBeginpuntLeiding    | Binnenbovenkant beginpunt leiding | Het niveau van de binnenbovenkant                                 | \[m.nap]  |
| BbbEindpuntLeiding     | Binnenbovenkant eindpunt leiding  | Het niveau van de binnenbovenkant                                 | \[m.nap]  |

## Projectmodel met inmeetgegevens in een GWSW-dataset

Als we de meetgegevens combineren met het eerder beschreven projectmodel kan een GWSW-dataset worden opgebouwd met daarin de uit te wisselen gegevens voor inmeetprojecten.
Zo'n GWSW-dataset zal er dan als volgt uitzien:

<div class="example-dataset"><div class="example-title marker">Dataset: Voorbeeld inmeetproject</div><pre>

{i01} \# Algemeen heen en terug
      rdfs:label {Algemeen.Projectnaam} ;
      rdf:type opera:Inmeetproject ;
      gwsw:isOutputOf \[ rdf:type gwsw:Opdrachtgever ; rdfs:label {Algemeen.Opdrachtgever} ; ] ;
      gwsw:hasAspect \[ rdf:type opera:Contractnummer ; gwsw:hasValue {Algemeen.Contractnummer} ; ] ;
      gwsw:isOutputOf \[ rdf:type gwsw:Contactpersoon ; rdfs:label {Algemeen.ProjectAdministratorOpdrachtgever} ; ] ;
      rdfs:comment {Algemeen.Projectomschrijving} ;
.
{i10} \# MetingKnooppunt: heen en terug
      gwsw:isPartOf {i01} ; 
      rdf:type opera:MetingKnooppunt ;
.
{i10} \# MetingKnooppunt: heen
      gwsw:hasInput {i11} ;
.
{i10} \# MetingKnooppunt: terug (gebruik een andere URI voor i11, ook bij hetzelfde knooppunt) 
      gwsw:hasOutput {i11} ;
      gwsw:hasAspect \[ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference {Knooppunt.WijzeVanInwinning}; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:DatumInwinning ; gwsw:hasValue {Knooppunt.DatumInwinning} ; ] ;
      rdfs:seeAlso {Knooppunt.FotoReferentie} ;
.
{i11} \# Knooppunt heen en terug
      rdf:type {Knooppunt.SoortPut} ;
      rdfs:label {Knooppunt.Knooppuntreferentie} ;
      gwsw:hasAspect \[ rdf:type gwsw:VormPut ; gwsw:hasReference {Knooppunt.VormPut} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:BreedtePut ; gwsw:hasValue {Knooppunt.BreedtePut} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:LengtePut ; gwsw:hasValue {Knooppunt.LengtePut} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:MateriaalPut ; gwsw:hasReference {Knooppunt.MateriaalPut} ; ] ;
      gwsw:hasPart \[ rdf:type gwsw:Stroomprofiel; gwsw:hasAspect \[ rdf:type gwsw:VormStroomprofiel ; gwsw:hasReference {Knooppunt.Stroomprofiel} ; ] ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:HoogtePut ; gwsw:hasValue {Knooppunt.HoogtePut} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference {Knooppunt.StatusFunctioneren} ; ] ;
      gwsw:isPartOf \[ rdf:type {Knooppunt.Stelsel}; ] ;
      gwsw:hasPart \[ rdf:type {Knooppunt.Constructieonderdeel}; gwsw:hasAspect \[ rdf:type gwsw:Drempelniveau ; gwsw:hasValue {Knooppunt.Drempelniveau} ; ] ; ] ;
.
{i11} \# Knooppunt heen en terug: de verbinding
      gwsw:hasAspect {i12} ;
.
{i12} 
      rdf:type gwsw:Putorientatie ;
      gwsw:hasAspect \[ rdf:type gwsw:Punt ; gwsw:hasValue "gml:Point {Knooppunt.X_coordinaat} {Knooppunt.Y_coordinaat} {Knooppunt.Z_coordinaat}" ; ] ;
.
{i11} \# Knooppunt terug
      gwsw:hasAspect \[ rdf:type opera:Waterstand ; gwsw:hasValue {Knooppunt.Waterstand} ; ] ;
      gwsw:hasPart \[ rdf:type gwsw:Stellaag; gwsw:hasAspect \[ rdf:type gwsw:HoogteStellaag ; gwsw:hasValue {Knooppunt.Stellaag} ; ] ; ] ;
      gwsw:hasAspect \[ rdf:type opera:MeldingKnooppunt ; gwsw:hasValue {Knooppunt.MeldingPut} ; ] ;
      rdfs:comment {Knooppunt.Opmerking} ;
.
{i13} \# Deksel heen en terug 
      rdf:type {Deksel.SoortDeksel} ;
      gwsw:isPartOf {i11} ; # Afleiden uit {Deksel.Knooppuntreferentie}
      gwsw:hasAspect \[ rdf:type gwsw:VormDeksel ; gwsw:hasReference {Deksel.VormDeksel} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:BreedteDeksel ; gwsw:hasValue {Deksel.BreedteDeksel} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:LengteDeksel ; gwsw:hasValue {Deksel.LengteDeksel} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:MateriaalDeksel ; gwsw:hasReference {Deksel.MateriaaDeksel} ; ] ;
      gwsw:hasAspect \[ rdf:type opera:MeldingDeksel ; gwsw:hasValue {Deksel.MeldingDeksel} ; ] ;
      rdfs:comment {Deksel.Opmerking} ;
.
{i20} \# MetingLeiding: heen en terug
      gwsw:isPartOf {i01} ; 
      rdf:type opera:MetingLeiding ;
.
{i20} \# MetingLeiding: heen
      gwsw:hasInput {i21} ;
.
{i20} \# MetingLeiding: terug (gebruik een andere URI voor i21, ook bij dezelfde leiding) 
      gwsw:hasOutput {i21} ;
      gwsw:hasAspect \[ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference {Leiding.WijzeVanInwinning}; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:DatumInwinning ; gwsw:hasValue {Leiding.DatumInwinning} ; ] ;
      rdfs:seeAlso {Leiding.FotoReferentie} ;
.
{i21} \# Leiding heen en terug
      rdf:type {Leiding.Leidingtype} ;
      rdfs:label {Leiding.Leiding_id} ;
      gwsw:hasAspect \[ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference {Leiding.StatusFunctioneren} ; ] ;
      gwsw:isPartOf \[ rdf:type {Leiding.Stelsel}; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:VormLeiding ; gwsw:hasReference {Leiding.VormLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:HoogteLeiding ; gwsw:hasValue {Leiding.HoogteLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:BreedteLeiding ; gwsw:hasValue {Leiding.BreedteLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:MateriaalLeiding ; gwsw:hasReference {Leiding.MateriaalLeiding} ; ] ;
.
{i21} \# Leiding heen en terug: de verbinding
      gwsw:hasAspect {i22} ;
.
{i22} 
      rdf:type gwsw:Leidingorientatie ; \# Afleiden uit {Leiding.BeginpuntLeiding} en {Leiding.EindpuntLeiding} 
      gwsw:hasAspect \[ rdf:type gwsw:Lijn ; gwsw:hasValue "gml:LineString {Knooppunt.X_coordinaat} {Knooppunt.Y_coordinaat} {Knooppunt.Z_coordinaat}, {Knooppunt.X_coordinaat} {Knooppunt.Y_coordinaat} {Knooppunt.Z_coordinaat}" ; ] ;
      gwsw:hasPart {i23} ;
      gwsw:hasPart {i24} ;
.
{i23} 
      rdf:type gwsw:BeginpuntLeiding ; 
      gwsw:hasConnection {i12} ; \# Afleiden uit {Leiding.BeginpuntLeiding}
      gwsw:hasAspect \[ rdf:type gwsw:BobBeginpuntLeiding ; gwsw:hasValue {Leiding.BobBeginpuntLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type opera:BbbBeginpuntLeiding ; gwsw:hasValue {Leiding.BbbBeginpuntLeiding} ; ] ;
.
{i24} 
      rdf:type gwsw:EindpuntLeiding ; 
      gwsw:hasConnection {i12} ; \# Afleiden uit {Leiding.EindpuntLeiding} {i12} is natuurlijk een andere put
      gwsw:hasAspect \[ rdf:type gwsw:BobEindpuntLeiding ; gwsw:hasValue {Leiding.BobEindpuntLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type opera:BbbEindpuntLeiding ; gwsw:hasValue {Leiding.BbbEindpuntLeiding} ; ] ;
.
{i21} \# Leiding terug
      gwsw:hasAspect \[ rdf:type opera:MeldingLeiding ; gwsw:hasValue {Leiding.MeldingLeiding} ; ] ;
      rdfs:comment {Leiding.Opmerking} ;
.
 </pre> </div>



