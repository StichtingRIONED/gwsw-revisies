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

Het projectmodel beschrijft globaal het activiteiten-schema van een revisieproject.
Algemene kenmerken zoals meldingen, opmerkingen, en wijze van inwinning worden als kenmerken bij de deelactiviteit (revisie knooppunt, revisie leiging) geregistreerd.

De objectmetingen zoals afmetingen, hoogteligging en waterstand worden als kenmerken bij het fysieke object geregistreerd.

Hetzelfde fysieke object kan in twee vormen (met bijbehorende kenmerken) voorkomen: als input (definitie) en/of als output (resultaat) bij de activiteit.
In RDF-formaat hebben die input- en output-vorm dezelfde objectnaam (rdfs:label) maar een eigen URI, daardoor hebben de bijbehorende kenmerken ook een input- en output-vorm.

<img src="media/Schema Revisieproject.png" style="width:100%;height:50%" />

## Gegevensuitwisseling

Een revisieproject gebruikt gegevens met de projectdefinitie (de beschrijving van de in te meten objecten) en gegevens met de projectresultaten (de resultaten van de inmetingen). 
Die gegevens zijn gebundeld in zogenaamde heen- en terug-bestanden (analoog aan de GWSW-HydX uitwisseling). 

Bij een revisieproject worden de gegevens via CSV of JSON uitgewisseld in aparte heen- en terug-bestanden.

Er zijn vier groepen: Project, Knooppunt, Deksel en Leiding. 
Elk uitwisselgegeven wordt geïdentificeerd door groep + veldcode (zie hierna).  

**CSV**

In het CSV-formaat is het heen- en terug-bestand een zipfile met daarin voor elke groep een apart CSV-bestand. 
De veldcode per groep is de kolomheader in het CSV-bestand.

**Voorbeeld Project.csv uit bestand heen.zip**  
<div class="box"><pre>
Naam;Opdrachtgever;Contractnummer;Omschrijving;Contactpersoon
"Project A";"Opdrachtgever B";"Contract C";"Omschrijving E";"Persoon F"
</pre></div>

**JSON**

In JSON-vorm is elke groep een object binnen het omvattende JSON-object, elk groep-object bevat vervolgens een object-array met daarin objecten met elementnamen conform de veldcode.
In het JSON-formaat is een heen- en terug-bestand een tekstfile met een JSON-string.

**Voorbeeld bestand heen.json**  
<div class="box"><pre>
{
  "Project": [
    {"Naam": "Project A", "Opdrachtgever": "Opdrachtgever B", "Contractnummer": "Contract C", "Omschrijving": "Omschrijving E", "Contactpersoon": "Persoon F"},
  ],
  "Knooppunt": [
  ],
  "Deksel": [
  ],
  "Leiding": [
  ],
}
</pre></div>

In de volgende tabellen staan de uitwisselgegevens per groep, de veldcode identificeert dus het gegeven per groep.

**Project**  

| Veldcode       | Omschrijving         | Waarde in RDF-termen                 | Opmerking                                  |
|----------------|----------------------|--------------------------------------|--------------------------------------------|
| Naam           | Naam project         | rdfs:label bij rev:Revisieproject    | in Opera Project_Id                        |
| Opdrachtgever  | Opdrachtgever        | rdfs:label bij gwsw:Opdrachtgever    |                                            |
| Contractnummer | Contractnummer       | gwsw:hasValue bij rev:Contractnummer |                                            |
| Omschrijving   | Omschrijving project | rdfs:comment bij rev:Revisieproject  | in Opera Projectomschrijving               |
| Contactpersoon | Contactpersoon       | rdfs:label bij gwsw:Contactpersoon   | in Opera ProjectAdministratorOpdrachtgever |

**Knooppunt** (Put of Bouwwerk)  

| Veldcode             | Omschrijving              | Waarde in RDF-termen                                              | Opmerking                    |
|----------------------|---------------------------|-------------------------------------------------------------------|------------------------------|
| Type                 | Type put of bouwwerk      | rdf:type van gwsw:Put of gwsw:Bouwwerk                            | in Opera SoortPut            |
| Vorm                 | Vorm put of bouwwerk      | gwsw:hasReference bij gwsw:VormPut of gwsw:VormBouwwerk           | in Opera VormPut             |
| Breedte              | Breedte put of bouwwerk   | gwsw:hasValue bij gwsw:BreedtePut of gwsw:BreedteBouwwerk         | in Opera BreedtePut          |
| Lengte               | Lengte put of bouwwerk    | gwsw:hasValue bij gwsw:LengtePut of gwsw:LengteBouwwerk           | in Opera LengtePut           |
| Materiaal            | Materiaal put of bouwwerk | gwsw:hasReference bij gwsw:MateriaalPut of gwsw:MateriaalBouwwerk | in Opera MateriaalPut        |
| Stroomprofiel        | Stroomprofiel             | gwsw:hasReference bij gwsw:Stroomprofiel                          |                              |
| Naam                 | Naam put of bouwwerk      | rdfs:label bij gwsw:Knooppunt                                     | in Opera Knooppuntreferentie |
| X                    | X coördinaat              | gwsw:hasValue bij gwsw:Punt                                       | in Opera X_coordinaat        |
| Y                    | Y coördinaat              | gwsw:hasValue bij gwsw:Punt                                       | in Opera Y_coordinaat        |
| Z                    | Z coördinaat              | gwsw:hasValue bij gwsw:Punt                                       | in Opera Z_coordinaat        |
| Hoogte               | Hoogte knooppunt          | gwsw:hasValue bij gwsw:HoogtePut of gwsw:HoogteBouwwerk           |                              |
| StatusFunctioneren   | Status functioneren       | gwsw:hasReference bij gwsw:StatusFunctioneren                     |                              |
| TypeStelsel          | Type stelsel              | rdf:type bij gwsw:Stelsel                                         |                              |
| Constructieonderdeel | Constructieonderdeel      | rdf:type bij gwsw:Constructieonderdeel                            |                              |
| Drempelniveau        | Drempelniveau             | gwsw:hasValue bijgwsw:Drempelniveau                               |                              |
| Melding              | Melding revisie knooppunt | gwsw:hasReference bij rev:MeldingRevisieKnooppunt                 | in Opera MeldingPut          |
| WijzeVanInwinning    | Wijze van inwinning       | gwsw:hasReference bij gwsw:WijzeVanInwinning                      |                              |
| DatumInwinning       | Datum inwinning           | gwsw:hasValue bij gwsw:DatumInwinning                             |                              |
| Waterstand           | Waterstand                | gwsw:hasValue bij rev:Waterstand                                  |                              |
| HoogteStellaag       | Hoogte stellaag           | gwsw:hasValue van gwsw:HoogteStellaag                             | Vanaf GWSW 1.6.1             |
| Fotoreferentie       | Fotoreferentie            | gwsw:seeAlso bij URI-knooppunt                                    |                              |
| Opmerking            | Opmerking                 | gwsw:hasValue bij gwsw:Opmerking                                  | in Opera rdfs:comment        |

**Deksel**  

| Veldcode  | Omschrijving               | Waarde in RDF-termen                           | Opmerking                    |
|-----------|----------------------------|------------------------------------------------|------------------------------|
| Naam      | Naam put of bouwwerk       | rdfs:label bij gwsw:Knooppunt                  | in Opera Knooppuntreferentie |
| Type      | Type deksel                | rdf:type van gwsw:Afdekking                    | in Opera SoortDeksel         |
| Vorm      | Vorm deksel                | gwsw:hasReference bij gwsw:VormDeksel          | in Opera VormDeksel          |
| Lengte    | Lengte deksel              | gwsw:hasValue bij gwsw:LengteDeksel            | in Opera LengteDeksel        |
| Breedte   | Breedte deksel             | gwsw:hasValue bij gwsw:BreedteDeksel           | in Opera BreedteDeksel       |
| Materiaal | Materiaal deksel           | gwsw:hasReference bij gwsw:MateriaalDeksel     | in Opera MateriaalDeksel     |
| Melding   | Melding bij revisie deksel | gwsw:hasReference bij rev:MeldingRevisieDeksel | in Opera MeldingDeksel       |
| Opmerking | Opmerking                  | gwsw:hasValue bij gwsw:Opmerking               | in Opera rdfs:comment        |

**Leiding**  

| Veldcode           | Omschrijving            | Waarde in RDF-termen                            | Opmerking                     |
|--------------------|-------------------------|-------------------------------------------------|-------------------------------|
| Naam               | Naam leiding            | rdfs:label bij gwsw:Leiding                     | in Opera Leiding_id           |
| NaamKnooppuntBegin | Naam knooppunt begin    | gwsw:hasConnection met URI-BeginpuntLeiding     | in Opera Knooppuntreferentie1 |
| NaamKnooppuntEind  | Naam knooppunt eind     | gwsw:hasConnection met URI-EindpuntLeiding      | in Opera Knooppuntreferentie2 |
| BobKnooppuntBegin  | Bob bij knooppunt begin | hasValue van gwsw:BobBeginpuntLeiding           | in Opera BobBeginpuntLeiding  |
| BobKnooppuntEind   | Bob bij knooppunt eind  | hasValue van gwsw:BobEindpuntLeiding            | in Opera BobEindpuntLeiding   |
| BbbKnooppuntBegin  | Bbb bij knooppunt begin | hasValue van rev:BbbBeginpuntLeiding            | in Opera BbbBeginpuntLeiding  |
| BbbKnooppuntEind   | Bbb bij knooppunt eind  | hasValue van rev:BbbEindpuntLeiding             | in Opera BbbEindpuntLeiding   |
| StatusFunctioneren | Status functioneren     | gwsw:hasReference bij gwsw:StatusFunctioneren   |                               |
| TypeStelsel        | Type stelsel            | rdf:type van gwsw:Stelsel                       |                               |
| Type               | Type leiding            | rdf:type van gwsw:Leiding                       | in Opera Leidingtype          |
| Vorm               | Vorm leiding            | gwsw:hasReference bij gwsw:Vorm                 | in Opera VormLeiding          |
| Hoogte             | Hoogte leiding          | gwsw:hasValue bij gwsw:Hoogte                   | in Opera HoogteLeiding        |
| Breedte            | Breedte leiding         | gwsw:hasValue bij gwsw:Breedte                  | in Opera BreedteLeiding       |
| Materiaal          | Materiaal leiding       | gwsw:hasReference bij gwsw:Materiaal            | in Opera MateriaalLeiding     |
| Melding            | Melding revisie leiding | gwsw:hasReference bij rev:MeldingRevisieLeiding | in Opera MeldingLeiding       |
| Fotoreferentie     | Fotoreferentie          | gwsw:seeAlso bij URI-knooppunt                  |                               |
| WijzeVanInwinning  | Wijze van inwinning     | gwsw:hasReference bij gwsw:WijzeVanInwinning    |                               |
| DatumInwinning     | Datum inwinning         | gwsw:hasValue bij gwsw:DatumInwinning           |                               |
| Opmerking          | Opmerking               | gwsw:hasValue bij gwsw:Opmerking                | in Opera rdfs:comment         |

Veel URI's staan al in het GWSW datamodel, voor het deelmodel Revisies zijn ook een aantal nieuwe concepten uitgewerkt 
(in de tabellen hiervoor staan al enkele nieuwe concepten, herkenbaar aan de prefix rev:).

Een overzicht van de nieuwe concepten (exclusief in deelmodel GWSW-Revisies):

| URI                     | Naam                              | Definitie                                                               | Opmerking |
|-------------------------|-----------------------------------|-------------------------------------------------------------------------|-----------|
| Revisieproject          | Revisieproject                    |                                                                         |           |
| Contractnummer          | Contractnummer                    |                                                                         |           |
| RevisieKnooppunt        | Revisie knooppunt                 | Een revisie van een put of bouwwerk (deelactiviteit van Revisieproject) |           |
| RevisieLeiding          | Revisie leiding                   | Een revisie van een leiding (deelactiviteit van Revisieproject)         |           |
| RevisieWaterstand       | Revisie waterstand                | De gemeten waterstand tov de constructiebodem                           | \[mm]     |
| MeldingRevisieKnooppunt | Melding bij revisie knooppunt     | Voorgedefinieerde meldingen bij de revisie van een put of bouwwerk      |           |
| MeldingRevisieDeksel    | Melding bij revisie deksel        | Voorgedefinieerde meldingen bij de revisie van een deksel               |           |
| MeldingRevisieLeiding   | Melding bij revisie leiding       | Voorgedefinieerde meldingen bij de revisie van een leiding              |           |
| BbbBeginpuntLeiding     | Binnenbovenkant beginpunt leiding | Het niveau van de binnenbovenkant bij het topologische beginpunt        | \[m.nap]  |
| BbbEindpuntLeiding      | Binnenbovenkant eindpunt leiding  | Het niveau van de binnenbovenkant bij het topologische eindpunt         | \[m.nap]  |

## Datamodel revisiegegevens in RDF

Hieronder staat het eerste concept model met daarin alleen de toegevoegde revisie-concepten (in de uitgewerkte versies wordt de prefix rev: vervangen door gwsw:).  

De uitwerking van het complete deelmodel GWSW-Revisies staat onder https://data.gwsw.nl/Revisies.

<div class="example"><div class="example-title marker">Datamodel: Revisiegegevens</div><pre>

rev:Revisieproject rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Project ;
  rdfs:label "Revisieproject";
  skos:definition "Revisieproject" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit RevisieKnooppunt (min=0)
    rdf:type owl:Restriction ;
    owl:onClass rev:RevisieKnooppunt ;
    owl:onProperty gwsw:hasPart ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit RevisieLeiding (min=0)
    rdf:type owl:Restriction ;
    owl:onClass rev:RevisieLeiding ;
    owl:onProperty gwsw:hasPart ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:RevisieKnooppunt rdf:type owl:Class ;
  rdfs:subClassOf gwsw:Meting ;
  rdfs:label "Revisie knooppunt" ;
  skos:definition "Landmeetkundige inmeting van een put of bouwwerk" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit Revisieproject (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:Revisieproject ;
    owl:onProperty gwsw:isPartOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk WijzeVanInwinning (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:WijzeVanInwinning ;
    owl:onProperty gwsw:hasAspect ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk DatumInwinning (exact=1)
    rdf:type owl:Restriction;
    owl:onClass gwsw:DatumInwinning;
    owl:onProperty gwsw:hasAspect;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Put (projectdefinitie) (max=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Put ;
    owl:onProperty gwsw:hasInput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Bouwwerk (projectdefinitie) (max=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Bouwwerk ;
    owl:onProperty gwsw:hasInput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Put (projectresultaat) (max=1, kan ook Bouwwerk zijn)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Put ;
    owl:onProperty gwsw:hasOutput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Bouwwerk (projectresultaat) (max=1, kan ook Put zijn)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Bouwwerk ;
    owl:onProperty gwsw:hasOutput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk MeldingRevisieKnooppunt (max=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:MeldingRevisieKnooppunt ;
    owl:onProperty gwsw:hasAspect ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk MeldingRevisieDeksel (min=0, er kunnen meerdere (niet geïdentificeerde) deksels zijn)
    rdf:type owl:Restriction ;
    owl:onClass rev:MeldingRevisieDeksel ;
    owl:onProperty gwsw:hasAspect ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk Opmerking (min=0, er kunnen er meerdere zijn)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Opmerking ;
    owl:onProperty gwsw:hasAspect ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:RevisieLeiding rdf:type owl:Class ;
  rdfs:subClassOf gwsw:Meting ;
  rdfs:label "Revisie leiding" ;
  skos:definition "Landmeetkundige inmeting van een leiding" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit Revisieproject (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:Revisieproject ;
    owl:onProperty gwsw:isPartOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk WijzeVanInwinning (exact=1)
    rdf:type owl:Restriction;
    owl:onClass gwsw:WijzeVanInwinning;
    owl:onProperty gwsw:hasAspect ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk DatumInwinning (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:DatumInwinning ;
    owl:onProperty gwsw:hasAspect ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Leiding (projectdefinitie) (max=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Leiding ;
    owl:onProperty gwsw:hasInput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Leiding (projectresultaat) (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Leiding ;
    owl:onProperty gwsw:hasOutput ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk MeldingRevisieLeiding (max=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:MeldingRevisieLeiding ;
    owl:onProperty gwsw:hasAspect ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk Opmerking (min=0, er kunnen er meerdere zijn)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Opmerking ;
    owl:onProperty gwsw:hasAspect ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MeldingRevisieKnooppunt rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Melding revisie knooppunt";
  skos:definition "Melding bij revisie van put of bouwwerk";
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit RevisieKnooppunt (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:RevisieKnooppunt ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MeldingRevisieDeksel rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Melding revisie deksel" ;
  skos:definition "Melding bij revisie van putdeksel" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit RevisieKnooppunt (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:RevisieKnooppunt ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MeldingRevisieLeiding rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Melding revisie leiding" ;
  skos:definition "Melding bij revisie van leiding" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit RevisieLeiding (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:RevisieLeiding ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:RevisieWaterstand rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Gemeten waterstand bij revisie-object" ;
  skos:definition "Gemeten waterstand bij de revisie van een object, de hoogte tov de bodem";
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit RevisieKnooppunt (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Put ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:BbbBeginpuntLeiding rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "B.b.b. beginpunt leiding" ;
  skos:definition "Niveau binnenbovenkant buis ter plaatse van het beginpunt" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op topologisch element BeginpuntLeiding (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:BeginpuntLeiding ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:BbbEindpuntLeiding rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "B.b.b. eindpunt leiding" ;
  skos:definition "Niveau binnenbovenkant buis ter plaatse van het eindpunt" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op topologisch element EinduntLeiding (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:EindpuntLeiding ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
</pre> </div>

## Projectmodel revisiegegevens in RDF

Als we de meetgegevens combineren met het eerder beschreven projectmodel kan een GWSW-dataset worden opgebouwd.
Zo'n GWSW-dataset omvat de uitwisseling binnen het volledige project, dus zowel de gegevens van de heen- als van de terug-levering.  

Het ziet er dan als volgt uit (in één GWSW-dataset):

<div class="example-dataset"><div class="example-title marker">Dataset: Voorbeeld revisieproject</div><pre>

\# ex: - prefix met de individuen, de objecten in de projectdefintie en in het terrein
\# gwsw: - bestaande gwsw-concepten
\# rev: - concepten in deelmodel GWSW-Revisies
\# rdf:/rdfs: - generieke RDF-concepten

{ex:01} \# Revisieproject
      rdfs:label {Project.Naam} ;
      rdf:type rev:Revisieproject ;
      gwsw:isOutputOf \[ rdf:type gwsw:Opdrachtgever ; rdfs:label {Project.Opdrachtgever} ; ] ;
      gwsw:hasAspect \[ rdf:type rev:Contractnummer ; gwsw:hasValue {Project.Contractnummer} ; ] ;
      gwsw:isOutputOf \[ rdf:type gwsw:Contactpersoon ; rdfs:label {Project.Contactpersoon} ; ] ;
      rdfs:comment {Project.Omschrijving} ;
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
      gwsw:hasAspect \[ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference {RevisieKnooppunt.WijzeVanInwinning}; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:DatumInwinning ; gwsw:hasValue {RevisieKnooppunt.DatumInwinning} ; ] ;
      rdfs:seeAlso {RevisieKnooppunt.FotoReferentie} ;
      gwsw:hasAspect \[ rdf:type rev:MeldingRevisieKnooppunt ; gwsw:hasValue {Knooppunt.Melding} ; ] ;
      gwsw:hasAspect \[ rdf:type rev:MeldingRevisieDeksel ; gwsw:hasValue {Deksel.Melding} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:Opmerking ; gwsw:hasValue {RevisieKnooppunt.Opmerking} ; ] ;
.
{ex:11i/ex:11o} \# Knooppunt heen en terug
      rdf:type {Knooppunt.Type} ; /# Ga hier uit van supertype gwsw:Put 
      rdfs:label {Knooppunt.Naam} ;
      gwsw:hasAspect \[ rdf:type gwsw:VormPut ; gwsw:hasReference {Knooppunt.Vorm} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:BreedtePut ; gwsw:hasValue {Knooppunt.Breedte} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:LengtePut ; gwsw:hasValue {Knooppunt.Lengte} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:MateriaalPut ; gwsw:hasReference {Knooppunt.Materiaal} ; ] ;
      gwsw:hasPart \[ rdf:type gwsw:Stroomprofiel; gwsw:hasAspect \[ rdf:type gwsw:VormStroomprofiel ; gwsw:hasReference {Knooppunt.Stroomprofiel} ; ] ; ] ;
      gwsw:hasPart \[ rdf:type gwsw:Stellaag; gwsw:hasAspect \[ rdf:type gwsw:HoogteStellaag ; gwsw:hasValue {Knooppunt.Stellaag} ; ] ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:HoogtePut ; gwsw:hasValue {Knooppunt.Hoogte} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference {Knooppunt.StatusFunctioneren} ; ] ;
      gwsw:isPartOf \[ rdf:type {Knooppunt.TypeStelsel}; ] ;
      gwsw:hasPart \[ rdf:type {Knooppunt.Constructieonderdeel}; gwsw:hasAspect \[ rdf:type gwsw:Drempelniveau ; gwsw:hasValue {Knooppunt.Drempelniveau} ; ] ; ] ;
.
{ex:11i/ex:11o} \# Knooppunt heen en terug: de verbinding
      gwsw:hasAspect {ex:12i/ex:12o} ;
.
{ex:12i/ex:12o} 
      rdf:type gwsw:Putorientatie ;
      gwsw:hasAspect \[ rdf:type gwsw:Punt ; gwsw:hasValue "gml:Point {Knooppunt.X} {Knooppunt.Y} {Knooppunt.Z}" ; ] ;
.
{ex:11o} \# Knooppunt terug
      gwsw:hasAspect \[ rdf:type rev:RevisieWaterstand ; gwsw:hasValue {Knooppunt.RevisieWaterstand} ; ] ;
.
{ex:13i/ex:13o} \# Deksel heen en terug 
      rdf:type {Deksel.Type} ;
      gwsw:isPartOf {ex:11i/i11o} ; # Afleiden uit {Deksel.NaamKnooppunt}
      gwsw:hasAspect \[ rdf:type gwsw:VormDeksel ; gwsw:hasReference {Deksel.Vorm} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:BreedteDeksel ; gwsw:hasValue {Deksel.Breedte} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:LengteDeksel ; gwsw:hasValue {Deksel.Lengte} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:MateriaalDeksel ; gwsw:hasReference {Deksel.Materiaal} ; ] ;

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
      gwsw:hasAspect \[ rdf:type rev:MeldingRevisieLeiding ; gwsw:hasValue {Leiding.Melding} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:Opmerking ; gwsw:hasValue {Leiding.Opmerking} ; ] ;
      rdfs:seeAlso {Leiding.FotoReferentie} ;
.
{ex:21i/ex:21o} \# Leiding heen en terug
      rdf:type {Leiding.Type} ;
      rdfs:label {Leiding.Naam} ;
      gwsw:hasAspect \[ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference {Leiding.StatusFunctioneren} ; ] ;
      gwsw:isPartOf \[ rdf:type {Leiding.TypeStelsel}; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:VormLeiding ; gwsw:hasReference {Leiding.Vorm} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:HoogteLeiding ; gwsw:hasValue {Leiding.Hoogte} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:BreedteLeiding ; gwsw:hasValue {Leiding.Breedte} ; ] ;
      gwsw:hasAspect \[ rdf:type gwsw:MateriaalLeiding ; gwsw:hasReference {Leiding.Materiaal} ; ] ;
.
{ex:21i/ex:21o} \# Leiding heen en terug: de verbinding
      gwsw:hasAspect {ex:22} ;
.
{ex:22} 
      rdf:type gwsw:Leidingorientatie ; \# Afleiden uit {Leiding.KnooppuntBegin} en {Leiding.KnooppuntEind} 
      gwsw:hasAspect \[ rdf:type gwsw:Lijn ; gwsw:hasValue "gml:LineString {Knooppunt.X} {Knooppunt.Y} {Knooppunt.Z}, {Knooppunt.X} {Knooppunt.Y} {Knooppunt.Z}" ; ] ;
      gwsw:hasPart {ex:23} ;
      gwsw:hasPart {ex:24} ;
.
{ex:23} \# Leiding heen en terug: beginpunt
      rdf:type gwsw:BeginpuntLeiding ; 
      gwsw:hasConnection {ex:12} ; \# Afleiden uit {Leiding.KnooppuntBegin}
      gwsw:hasAspect \[ rdf:type gwsw:BobBeginpuntLeiding ; gwsw:hasValue {Leiding.BobKnooppuntBegin} ; ] ;
.
{ex:24} \# Leiding heen en terug: eindpunt 
      rdf:type gwsw:EindpuntLeiding ; 
      gwsw:hasConnection {ex:12} ; \# Afleiden uit {Leiding.KnooppuntEind} {ex:12} is natuurlijk een andere put
      gwsw:hasAspect \[ rdf:type gwsw:BobEindpuntLeiding ; gwsw:hasValue {Leiding.BobKnooppuntEind} ; ] ;
.
{ex:241} \# Beginpunt terug
      gwsw:hasAspect \[ rdf:type rev:BbbBeginpuntLeiding ; gwsw:hasValue {Leiding.BbbKnooppuntBegin} ; ] ;
{ex:24o} \# Eindpunt terug
      gwsw:hasAspect \[ rdf:type rev:BbbEindpuntLeiding ; gwsw:hasValue {Leiding.BbbKnooppuntEind} ; ] ;
.
 </pre> </div>



