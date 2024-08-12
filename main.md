# GWSW Revisies

<style>
  .symbolSmall{width:20px;height:20px;margin-right:1em;vertical-align:middle}
  .symbol{width:30px;height:30px;margin-right:1em;vertical-align:middle}
</style>

Stichting RIONED is initiatiefnemer en eigenaar van dit GitHub-project, Eric Oosterom is de verantwoordelijk projectmanager. 

Vragen over deze website en het GWSW kunt u stellen via gwsw@rioned.org. 

# Inleiding

De voornaamste initiator van dit deelmodel is de GWSW-Opera organisatie. De basis ligt bij een PoC gericht op het ontwikkelen en toetsen van het revisieproces, dus de gegevensuitwisseling van de landmeter naar de beheerder. 

# Doel en toepassing

Ondersteuning bij revisies van stedelijk water voorzieningen. 
Het efficient en effectief verwerken van inrevisieen door de landmeter.

# Gegevensmodel revisieproject

## Projectmodel

<img src="media/Schema Revisieproject.png" style="width:100%;height:50%" />

## Gegevensuitwisseling

Bij een revisieproject worden de gegevens via CSV of JSON uitgewisseld. 
In de volgende tabellen staat in de kolom Veldnaam de CSV-kolomheader of de JSON-objectidentificatie. 
Groepsgewijs (per CSV-bestand of JSON-Object) gaat het om de volgende gegevens :

**Project**  

| Veldnaam            | Waarde in RDF-termen                 | Opmerking                                  |
|---------------------|--------------------------------------|--------------------------------------------|
| NaamProject         | rdfs:label bij rev:Revisieproject    | in Opera Project_Id                        |
| Opdrachtgever       | rdfs:label bij gwsw:Opdrachtgever    |                                            |
| Contractnummer      | gwsw:hasValue bij rev:Contractnummer |                                            |
| OmschrijvingProject | rdfs:comment bij rev:Revisieproject  | in Opera Projectomschrijving               |
| Contactpersoon      | rdfs:label bij gwsw:Contactpersoon   | in Opera ProjectAdministratorOpdrachtgever |

**Deksel**  

| Veldnaam             | Waarde in RDF-termen                           | Opmerking                    |
|----------------------|------------------------------------------------|------------------------------|
| NaamKnooppunt        | rdfs:label bij gwsw:Knooppunt                  | in Opera Knooppuntreferentie |
| TypeDeksel           | rdf:type van gwsw:Afdekking                    | in Opera SoortDeksel         |
| VormDeksel           | gwsw:hasReference bij gwsw:VormDeksel          |                              |
| LengteDeksel         | gwsw:hasValue bij gwsw:LengteDeksel            |                              |
| BreedteDeksel        | gwsw:hasValue bij gwsw:BreedteDeksel           |                              |
| MateriaalDeksel      | gwsw:hasReference bij gwsw:MateriaalDeksel     |                              |
| MeldingRevisieDeksel | gwsw:hasReference bij rev:MeldingRevisieDeksel | in Opera MeldingDeksel       |
| Opmerking            | gwsw:hasValue bij gwsw:Opmerking               | in Opera rdfs:comment        |

**Knooppunt** (Put of Bouwwerk)  

| Veldnaam                | Waarde in RDF-termen                                              | Opmerking                    |
|-------------------------|-------------------------------------------------------------------|------------------------------|
| TypeKnooppunt           | rdf:type van gwsw:Put of gwsw:Bouwwerk                            | in Opera SoortPut            |
| VormPut                 | gwsw:hasReference bij gwsw:VormPut of gwsw:VormBouwwerk           |                              |
| BreedtePut              | gwsw:hasValue bij gwsw:BreedtePut of gwsw:BreedteBouwwerk         |                              |
| LengtePut               | gwsw:hasValue bij gwsw:LengtePut of gwsw:LengteBouwwerk           |                              |
| MateriaalPut            | gwsw:hasReference bij gwsw:MateriaalPut of gwsw:MateriaalBouwwerk |                              |
| Stroomprofiel           | gwsw:hasReference bij gwsw:Stroomprofiel                          |                              |
| NaamKnoopppunt          | rdfs:label bij gwsw:Knooppunt                                     | in Opera Knooppuntreferentie |
| X_coordinaat            | gwsw:hasValue bij gwsw:Punt                                       |                              |
| Y_coordinaat            | gwsw:hasValue bij gwsw:Punt                                       |                              |
| Z_coordinaat            | gwsw:hasValue bij gwsw:Punt                                       |                              |
| HoogtePut               | gwsw:hasValue bij gwsw:HoogtePut of gwsw:HoogteBouwwerk           |                              |
| StatusFunctioneren      | gwsw:hasReference bij gwsw:StatusFunctioneren                     |                              |
| Stelsel                 | rdf:type bij gwsw:Stelsel                                         |                              |
| Constructieonderdeel    | rdf:type bij gwsw:Constructieonderdeel                            |                              |
| Drempelniveau           | gwsw:hasValue bijgwsw:Drempelniveau                               |                              |
| MeldingRevisieKnooppunt | gwsw:hasReference bij rev:MeldingRevisieKnooppunt                 | in Opera MeldingPut          |
| WijzeVanInwinning       | gwsw:hasReference bij gwsw:WijzeVanInwinning                      |                              |
| DatumInwinning          | gwsw:hasValue bij gwsw:DatumInwinning                             |                              |
| Waterstand              | gwsw:hasValue bij rev:Waterstand                                  |                              |
| HoogteStellaag          | gwsw:hasValue van gwsw:HoogteStellaag                             | Vanaf GWSW 1.6.1             |
| Fotoreferentie          | gwsw:seeAlso bij URI-knooppunt                                    |                              |
| Opmerking               | gwsw:hasValue bij gwsw:Opmerking                                  | in Opera rdfs:comment        |

**Leiding**  

| Veldnaam              | Waarde in RDF-termen                            | Opmerking                     |
|-----------------------|-------------------------------------------------|-------------------------------|
| NaamLeiding           | rdfs:label bij gwsw:Leiding                     | in Opera Leiding_id           |
| NaamKnooppuntBegin    | gwsw:hasConnection met URI-BeginpuntLeiding     | in Opera Knooppuntreferentie1 |
| NaamKnooppuntEind     | gwsw:hasConnection met URI-EindpuntLeiding      | in Opera Knooppuntreferentie2 |
| BobBeginpuntLeiding   | hasValue van gwsw:BobBeginpuntLeiding           |                               |
| BobEindpuntLeiding    | hasValue van gwsw:BobEindpuntLeiding            |                               |
| BbbBeginpuntLeiding   | hasValue van rev:BbbBeginpuntLeiding            |                               |
| BbbEindpuntLeiding    | hasValue van rev:BbbEindpuntLeiding             |                               |
| StatusFunctioneren    | gwsw:hasReference bij gwsw:StatusFunctioneren   |                               |
| Stelsel               | rdf:type van gwsw:Stelsel                       |                               |
| TypeLeiding           | rdf:type van gwsw:Leiding                       | in Opera Leidingtype          |
| VormLeiding           | gwsw:hasReference bij gwsw:Vorm                 |                               |
| HoogteLeiding         | gwsw:hasValue bij gwsw:Hoogte                   |                               |
| BreedteLeiding        | gwsw:hasValue bij gwsw:Breedte                  |                               |
| MateriaalLeiding      | gwsw:hasReference bij gwsw:Materiaal            |                               |
| MeldingRevisieLeiding | gwsw:hasReference bij rev:MeldingRevisieLeiding | in Opera MeldingLeiding       |
| Fotoreferentie        | gwsw:seeAlso bij URI-knooppunt                  |                               |
| WijzeVanInwinning     | gwsw:hasReference bij gwsw:WijzeVanInwinning    |                               |
| DatumInwinning        | gwsw:hasValue bij gwsw:DatumInwinning           |                               |
| Opmerking             | gwsw:hasValue bij gwsw:Opmerking                | in Opera rdfs:comment         |

Veel URI's staan al in het GWSW datamodel, voor het deelmodel Revisies zijn een aantal nieuwe concepten uitgewerkt.
In de vorige tabellen staan al enkele nieuwe concepten, herkenbaar aan de prefix rev: .

Een overzicht van de nieuwe concepten (exclusief in deelmodel GWSW-Revisies ):

| URI                     | Naam                              | Definitie                                                               | Opmerking |
|-------------------------|-----------------------------------|-------------------------------------------------------------------------|-----------|
| Revisieproject          | Revisieproject                    |                                                                         |           |
| Contractnummer          | Contractnummer                    |                                                                         |           |
| RevisieKnooppunt        | Revisie knooppunt                 | Een revisie van een put of bouwwerk (deelactiviteit van RevisieProject) |           |
| RevisieLeiding          | Revisie leiding                   | Een revisie van een leiding (deelactiviteit van RevisieProject)         |           |
| Waterstand              | Waterstand                        | De gemeten waterstand tov de constructiebodem                           | \[mm]     |
| MeldingRevisieKnooppunt | Melding bij revisie knooppunt     | Voorgedefinieerde meldingen bij de revisie van een put of bouwwerk      |           |
| MeldingRevisieDeksel    | Melding bij revisie deksel        | Voorgedefinieerde meldingen bij de revisie van een deksel               |           |
| MeldingRevisieLeiding   | Melding bij revisie leiding       | Voorgedefinieerde meldingen bij de revisie van een leiding              |           |
| BbbBeginpuntLeiding     | Binnenbovenkant beginpunt leiding | Het niveau van de binnenbovenkant bij het topologische beginpunt        | \[m.nap]  |
| BbbEindpuntLeiding      | Binnenbovenkant eindpunt leiding  | Het niveau van de binnenbovenkant bij het topologische eindpunt         | \[m.nap]  |

## Projectmodel met revisiegegevens in een GWSW-dataset

Als we de meetgegevens combineren met het eerder beschreven projectmodel kan een GWSW-dataset worden opgebouwd met daarin de uit te wisselen gegevens voor revisieprojecten.
Zo'n GWSW-dataset zal er dan als volgt uitzien:

<div class="example-dataset"><div class="example-title marker">Dataset: Voorbeeld revisieproject</div><pre>

\# ex: - prefix met de individuen, de objecten in de projectdefintie en in het terrein
\# gwsw: - bestaande gwsw-concepten
\# rev: - concepten in deelmodel GWSW-Revisies
\# rdf:/rdfs: - generieke RDF-concepten

{ex:01} \# Revisieproject
      rdfs:label {Project.NaamProject} ;
      rdf:type rev:Revisieproject ;
      gwsw:isOutputOf \[ rdf:type gwsw:Opdrachtgever ; rdfs:label {Project.Opdrachtgever} ; ] ;
      gwsw:hasAspect \[ rdf:type rev:Contractnummer ; gwsw:hasValue {Project.Contractnummer} ; ] ;
      gwsw:isOutputOf \[ rdf:type gwsw:Contactpersoon ; rdfs:label {Project.Contactpersoon} ; ] ;
      rdfs:comment {Project.OmschrijvingProject} ;
.
{ex:10} \# Revisie knooppunt - activiteit
      gwsw:isPartOf {ex:01} ; 
      rdf:type rev:RevisieKnooppunt ;
.
{ex:10} \# Revisie knooppunt - projectdefinitie (heen)
      gwsw:hasInput {ex:11i} ;
.
{ex:10} \# Revisie knooppunt - resultaat (terug)
      gwsw:hasOutput {ex:11o} ; \# Gebruik een andere URI dan ex:11i, ook bij hetzelfde knooppunt (houdt dezelfde naam)
      gwsw:hasAspect \[ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference {Knooppunt.WijzeVanInwinning}; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:DatumInwinning ; gwsw:hasValue {Knooppunt.DatumInwinning} ; ] ;
      rdfs:seeAlso {Knooppunt.FotoReferentie} ;
.
{ex:11i/ex:11o} \# Knooppunt heen en terug
      rdf:type {Knooppunt.TypeKnooppunt} ;
      rdfs:label {Knooppunt.NaamKnooppunt} ;
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
{ex:11i/ex:11o} \# Knooppunt heen en terug: de verbinding
      gwsw:hasAspect {ex:12i/ex:12o} ;
.
{ex:12i/ex:12o} 
      rdf:type gwsw:Putorientatie ;
      gwsw:hasAspect \[ rdf:type gwsw:Punt ; gwsw:hasValue "gml:Point {Knooppunt.X_coordinaat} {Knooppunt.Y_coordinaat} {Knooppunt.Z_coordinaat}" ; ] ;
.
{ex:11o} \# Knooppunt terug
      gwsw:hasAspect \[ rdf:type rev:Waterstand ; gwsw:hasValue {Knooppunt.Waterstand} ; ] ;
      gwsw:hasPart \[ rdf:type gwsw:Stellaag; gwsw:hasAspect \[ rdf:type gwsw:HoogteStellaag ; gwsw:hasValue {Knooppunt.Stellaag} ; ] ; ] ;
      gwsw:hasAspect \[ rdf:type rev:MeldingRevisieKnooppunt ; gwsw:hasValue {Knooppunt.MeldingRevisieKnooppunt} ; ] ;
      gwsw:Opmerking {Knooppunt.Opmerking} ;
.
{ex:13i/ex:13o} \# Deksel heen en terug 
      rdf:type {Deksel.TypeDeksel} ;
      gwsw:isPartOf {ex:11i/i11o} ; # Afleiden uit {Deksel.NaamKnooppunt}
      gwsw:hasAspect \[ rdf:type gwsw:VormDeksel ; gwsw:hasReference {Deksel.VormDeksel} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:BreedteDeksel ; gwsw:hasValue {Deksel.BreedteDeksel} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:LengteDeksel ; gwsw:hasValue {Deksel.LengteDeksel} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:MateriaalDeksel ; gwsw:hasReference {Deksel.MateriaaDeksel} ; ] ;
      gwsw:hasAspect \[ rdf:type rev:MeldingRevisieDeksel ; gwsw:hasValue {Deksel.MeldingDeksel} ; ] ;
      gwsw:Opmerking {Deksel.Opmerking} ;
.
{ex:20} \# Revisie Leiding - activiteit
      gwsw:isPartOf {ex:01} ; 
      rdf:type rev:RevisieLeiding ;
.
{ex:20} \# Revisie Leiding - projectdefinitie (heen)
      gwsw:hasInput {ex:21i} ;
.
{ex:20} \# RevisieLeiding: - resultaat (terug)
      gwsw:hasOutput {ex:21o} ; \# Gebruik een andere URI dan ex:21i, ook bij dezelfde leiding (houdt dezelfde naam)
      gwsw:hasAspect \[ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference {Leiding.WijzeVanInwinning}; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:DatumInwinning ; gwsw:hasValue {Leiding.DatumInwinning} ; ] ;
      rdfs:seeAlso {Leiding.FotoReferentie} ;
.
{ex:21i/ex:21o} \# Leiding heen en terug
      rdf:type {Leiding.TypeLeiding} ;
      rdfs:label {Leiding.NaamLeiding} ;
      gwsw:hasAspect \[ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference {Leiding.StatusFunctioneren} ; ] ;
      gwsw:isPartOf \[ rdf:type {Leiding.Stelsel}; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:VormLeiding ; gwsw:hasReference {Leiding.VormLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:HoogteLeiding ; gwsw:hasValue {Leiding.HoogteLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:BreedteLeiding ; gwsw:hasValue {Leiding.BreedteLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:MateriaalLeiding ; gwsw:hasReference {Leiding.MateriaalLeiding} ; ] ;
.
{ex:21i/ex:21o} \# Leiding heen en terug: de verbinding
      gwsw:hasAspect {ex:22} ;
.
{ex:22} 
      rdf:type gwsw:Leidingorientatie ; \# Afleiden uit {Leiding.BeginpuntLeiding} en {Leiding.EindpuntLeiding} 
      gwsw:hasAspect \[ rdf:type gwsw:Lijn ; gwsw:hasValue "gml:LineString {Knooppunt.X_coordinaat} {Knooppunt.Y_coordinaat} {Knooppunt.Z_coordinaat}, {Knooppunt.X_coordinaat} {Knooppunt.Y_coordinaat} {Knooppunt.Z_coordinaat}" ; ] ;
      gwsw:hasPart {ex:23} ;
      gwsw:hasPart {ex:24} ;
.
{ex:23} 
      rdf:type gwsw:BeginpuntLeiding ; 
      gwsw:hasConnection {ex:12} ; \# Afleiden uit {Leiding.BeginpuntLeiding}
      gwsw:hasAspect \[ rdf:type gwsw:BobBeginpuntLeiding ; gwsw:hasValue {Leiding.BobBeginpuntLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type rev:BbbBeginpuntLeiding ; gwsw:hasValue {Leiding.BbbBeginpuntLeiding} ; ] ;
.
{ex:24} 
      rdf:type gwsw:EindpuntLeiding ; 
      gwsw:hasConnection {ex:12} ; \# Afleiden uit {Leiding.EindpuntLeiding} {ex:12} is natuurlijk een andere put
      gwsw:hasAspect \[ rdf:type gwsw:BobEindpuntLeiding ; gwsw:hasValue {Leiding.BobEindpuntLeiding} ; ] ;
      gwsw:hasAspect \[ rdf:type rev:BbbEindpuntLeiding ; gwsw:hasValue {Leiding.BbbEindpuntLeiding} ; ] ;
.
{ex:21o} \# Leiding terug
      gwsw:hasAspect \[ rdf:type rev:MeldingRevisieLeiding ; gwsw:hasValue {Leiding.MeldingRevisieLeiding} ; ] ;
      gwsw:Opmerking {Leiding.Opmerking} ;
.
 </pre> </div>



