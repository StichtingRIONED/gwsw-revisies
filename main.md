# GWSW Revisies

<style>
  .symbolSmall{width:20px;height:20px;margin-right:1em;vertical-align:middle}
  .symbol{width:30px;height:30px;margin-right:1em;vertical-align:middle}
</style>

Stichting RIONED is initiatiefnemer en eigenaar van dit GitHub-project, Eric Oosterom is de verantwoordelijk projectmanager. De inhoud van GWSW Revisies is in grote mate tot stand gekomen in samenwerking met GWSW-Opera B.V., die samen met een partners GWSW-Inmeten een aantal Proof-of-Concepts (PoC’s) heeft uitgevoerd. 

Vragen over deze website en het GWSW kunt u stellen via gwsw@rioned.org. 

# Inleiding
Het inmeten van vaste gegevens is een activiteit die bijdraagt aan goed beheer van stedelijk watervoorzieningen. Door ontbrekende, foutieve of achterhaalde maatvoeringen (opnieuw) in te meten ontstaat een betrouwbaar beheerbestand waarmee kostbare besluiten onderbouwd kunnen worden, bijvoorbeeld als basis voor een hydrodynamisch rekenmodel dat wordt gebruikt om te bepalen of stelselaanpassingen nodig zijn. Een foutieve leidingdiameter of verouderde overstortdrempelhoogte in zettingsgevoelig gebied kan dan al snel leiden tot grote verschillen tussen theoretische modelberekeningen en wat buiten gebeurt tijdens hevige neerslag. De ligging van vaste gegevens op orde hebben is ook een belangrijk middel om graafschade door grondroerders te voorkomen.

Door te werken met GWSW-conforme datasets van opdrachtgever naar landmeter over in te meten objecten en daarna vice versa met meetresultaten terug, ontstaat een efficiënte informatie-uitwisseling waar op eenvoudige wijze validatieregels aan toe te voegen zijn die controleren op volledigheid en eventueel foutieve metingen. 

Het initiatief voor dit deelmodel komt voor een belangrijk deel van de GWSW-Opera organisatie. De basis ligt bij een PoC gericht op het ontwikkelen en toetsen van het inmeetproces, dus de gegevensuitwisseling tussen landmeter en beheerder.

## Doel en toepassing

Ondersteuning bij revisies en andere metingen van stedelijk water voorzieningen, vooral het efficiënt en effectief verwerken van inmetingen door de landmeter.

**Revisie**  
De term "revisie" wordt gebruikt voor het inmeten van de objectgegevens na de aanleg (de realisatie van het ontwerp). Dit deelmodel heeft een bredere scope, ook het inmeten van al langer in gebruik zijnde objecten is een toepassing van dit deelmodel. 
Denk dan bijvoorbeeld aan het verbeteren van de bestaande registratie of het actualiseren van gegevens na verzakkingen.

## Leeswijzer
In hoofdstuk twee van dit ontwerpdocument wordt beschreven uit welke elementen een revisieproject bestaat en welke gegevens van de opdrachtgever (beheerder) naar de opdrachtnemer (landmeter) worden uitgewisseld en andersom. Hoofdstuk drie gaat over de uitwisselingsformaten (CSV, JSON, OroX) waarmee deze gegevens kunnen worden uitgewisseld. Tot slot beschrijft hoofdstuk vier de aanpassingen aan het GWSW datamodel. 

# Projectmodel
Dit hoofdstuk beschrijft de opbouw van een revisieproject. Een revisieproject bestaat uit de algemene kenmerken van een project (opdrachtgever, opdrachtnemer, projectreferentie, etc.), waaraan verschillende deelactiviteiten, oftewel acties, aan gekoppeld zijn (zie ook Figuur 2.1).

**Deelactiviteiten**  
De deelactiviteiten van een revisieproject gaan over het inmeten van een knooppunt (put of bouwwerk) en/of het inmeten van een leiding.
Een deelactiviteit heeft algemene kenmerken zoals meldingen, opmerkingen en de wijze van inwinning. Elke activiteit kent een in- en uitvoer, waarin de gegevens staan die richting de landmeter gaan en na meten weer terugkomen.

**Invoer**   
Een knooppunt of leiding met oorspronkelijke kenmerken zoals afmetingen vormt de invoer voor de deelactiviteit. Die gegevens komen uit het beheersysteem of vanuit het ontwerpplan en gaan naar de opdrachtnemer (landmeter) zodat bekend is welk object ingemeten dient te worden.

**Uitvoer**  
Het ingemeten object wordt als uitvoer van de deelactiviteit beschreven, de ingemeten kenmerken zoals afmetingen en hoogteligging worden - net zoals bij het invoer-object - bij het uitvoer-object opgenomen. Waargenomen toestandsgegevens (een soort meting) zoals "meting waterstand" worden als aparte uitvoer bij de deelactiviteit beschreven. 

Hetzelfde fysieke object kan dus (met bijbehorende kenmerken) in twee vormen voorkomen: als invoer (definitie) en/of als uitvoer (resultaat) bij de activiteit.
Volgens het GWSW Datamodel hebben die invoer- en uitvoer-vorm dezelfde objectnaam (rdfs:label) maar een eigen URI, daardoor hebben de bijbehorende kenmerken ook een invoer- en uitvoer-vorm.

<img src="media/Schema Revisieproject.png" style="width:80%;height:80%" />

*Figuur 2.1 - Schematisatie revisieproject met de verschillende deelactiviteiten (acties)*

# Gegevensuitwisseling
Een revisieproject gebruikt de projectdefinitie en gegevens over de oorspronkelijke kenmerken van de in te meten objecten. Dit kunnen brongegevens zijn of gegevens afkomstig van de GWSW-server, zie ook Figuur 3.1. Als projectresultaat worden de inmetingen terug geleverd. Veelal wordt hierbij ook een verschilanalyse uitgevoerd en een rapportage opgeleverd. Uitwisseling van inmeetgegevens tussen de opdrachtgever en de opdrachtnemer geschiedt via een uitwisselingsformaat in OroX, JSON of CSV. Deze uitwisselingsformaten zijn in de onderstaande paragrafen uitgewerkt. 

<img src="media/Proces uitwisseling.png" style="width:80%;height:80%" />

*Figuur 3.1 - Schematische weergave van de gegevensuitwisseling via Orox / JSON / CSV in verschillende stadia van een revisieproject*

## GWSW-OroX formaat
Beheersystemen kunnen veelal omgaan met een GWSW-datasets, ze exporteren of importeren dan een dataset (bestand) conform het GWSW-OroX protocol. 
Zo'n dataset is direct bruikbaar op het GWSW platform, waarmee de gegevens voor allerlei algemene toepassingen beschikbaar komen. 
Zo kan de inhoud direct in GIS systemen worden ontsloten. Zie ook https://apps.gwsw.nl.

Ook de gegevens van een revisieproject kunnen via het OroX-protocol worden uitgewisseld, dat is de meest directe vorm van uitwisseling. 
Het complete revisieproject, zowel de definitie als de resultaten past dan in één dataset. In de [bijlage](#orox-uitwisselbestand) van dit ontwerpdocument is een voorbeeldbestand volgens het OroX-protocol opgenomen

**Validatie uitwisseling**  
Gebruik voor de validatie van de volledigheid van heen- en terug-gegevens ook de tabellen in de volgende paragraaf, zie de kolommen "Heen" en "Terug"

Het GWSW-OroX protocol is een speciaal formaat, ingericht op het uitwisselen via linked data en het kunnen bouwen van ontologiën. 
Een ontologie is een speciale datastructuur waarin de stedelijk water voorzieningen volledig beschreven kunnen worden, dat geldt voor zowel de systemen als de (beheer)processen.

## Tussenvorm CSV of JSON 
Linked data formaten zoals het GWSW-OroX zijn vaak minder bekend bij uitvoerende partijen zoals de landmeter bij inmetingen of de CAD-tekenaar bij het ontwerp van systemen.
Om die reden zijn er tussenvormen beschikbaar in bekendere formaten zoals CSV en JSON (minder bekend maar wel eenvoudig van opzet). 
Omzetters van CSV naar JSON en vice versa zijn algemeen beschikbaar.

Via CSV of JSON worden de gegevens uitgewisseld in aparte heen- en terug-bestanden (analoog aan de GWSW-RibX uitwisseling). Nadeel van deze route is dat er sprake is van enige redundantie, zo komen projectgegevens zowel in het heen- als terug bestand voor. Daarmee zijn deze tussenvormen foutgevoeliger.

In deze tussenvorm zijn er vier groepen: Project, Knooppunt, Deksel en Leiding. 
Elk uitwisselgegeven wordt geïdentificeerd door deze groep + de veldcode (zie hierna).  

**CSV**

In het CSV-formaat is het heen- en terug-bestand een zipfile met daarin voor elke groep een apart CSV-bestand. 
De veldcodes uit de onderstaande tabellen per groep, vormen de kolomheader voor het CSV-bestand. Wanneer een kolom meerdere waarden bevat, bijvoorbeeld meerdere foto's bij een put, worden deze gescheiden door middel van een 'pipe' teken '|'.

**Voorbeeld Project.csv uit bestand heen.zip**  
<div class="box"><pre>
Bestandstype;Versie;Naam;Opdrachtgever;Opdrachtnemer;ProjectreferentieOpdrachtgever;ProjectreferentieOpdrachtnemer;Omschrijving;Contactpersoon;WijzeVanInwinningKnooppunt;WijzeVanInwinningDeksel;WijzeVanInwinningLeiding;Knooppuntnamen;WijzeVanInwinningXY;WijzeVanInwinningZ
"Revisie terug";"1.6.2";"Inmeten alles";"Gemeente Juinen";"Hekking Meetadvies B.V.";"OPD12345";"AAN67890";"Inmeting klein Juinen";"Walter de Rochebrune";"Inmeting";"GNSS Vanuit wagen";"Inmeting";"K9999"|"K9998"|"K9997"|"K9996"|"K9995"|"K9994"|"K9993"|"K9992";"GNSS Landmeting";"GNSS Landmeting"
</pre></div>

**JSON**

In JSON-vorm is elke groep een object binnen het omvattende JSON-object, elk groep-object bevat vervolgens een object-array met daarin objecten met elementnamen conform de veldcode. In het JSON-formaat is een heen- en terug-bestand een tekstfile met daarin de JSON-string. In de [bijlage](#json-uitwisselbestand) is voor zowel het heen- als terugbestand een voorbeeld opgenomen.

In de volgende tabellen staan de uitwisselgegevens per groep, de veldcode identificeert dus het gegeven per groep.

**Vullingsvoorschriften uitwisseling (identiek aan de RibX-definitie):**

De vullingsvoorschriften staan in twee kolommen:
* “Heen”: de veldvulling in een vooraf aangeleverd uitwisselbestand, afkomstig van (het beheersysteem van) de rioleringsbeheerder.
* “Terug”: de veldvulling in een terug geleverd uitwisselbestand, de resultaten van de landmeter.

De kolommen “heen” en “terug” gebruiken de volgende codes om aan te geven of een gegeven verplicht is:

| Code | Voorschrift veldvulling in uitwisselbestand                                 |
|------|-----------------------------------------------------------------------------|
|      | Geen code in kolom “heen”: Niet vooraf invullen                             |
|      | Geen code in kolom “terug”: Niet achteraf invullen (terug zonder wijziging) |
| O    | Optioneel                                                                   |
| A    | Altijd *)                                                                   |

*) Als voor de kolom “heen” geldt dat het gegeven verplicht is (A) en het gegeven ontbreekt in het heen-bestand, dan moet de rioleringsbeheerder met de landmeter 
afspraken maken over de teruglevering. Wanneer het gegeven voor zowel “heen” als “terug” verplicht is (A) en het “heen”-gegeven is fout of ontbreekt (nieuw object, niet vooraf 
ingevuld), dan moet de landmeter dit gegeven – als het bekend is – altijd bij de inmeting corrigeren of aanvullen.

**Link naar datamodel GWSW**

Het GWSW-datamodel beschrijft de gebruikte concepten, de definitie en het waardetype is daarin beschreven.  
Elk concept linkt via een URI naar het GWSW-datamodel (de deelmodellen onder https:data.gwsw.nl/totaal of https:data.gwsw.nl/revisies).


**Gegevens Project**  

| Veldcode                       | Omschrijving                    | Waardetype (in RDF-termen)                      | Heen | Terug | Opmerking |
|--------------------------------|---------------------------------|-------------------------------------------------|------|-------|-----------|
| Naam                           | Naam project                    | rdfs:label bij [Revisieproject]                 | A    |       |           |
| Opdrachtgever                  | Opdrachtgever                   | rdfs:label bij [Opdrachtgever]                  | A    |       |           |
| Opdrachtnemer                  | Opdrachtnemer                   | rdfs:label bij [Opdrachtnemer]                  | A    |       |           |
| ProjectreferentieOpdrachtgever | Projectreferentie Opdrachtgever | rdfs:label bij [ProjectreferentieOpdrachtgever] | A    |       |           |
| ProjectreferentieOpdrachtnemer | Projectreferentie Opdrachtnemer | rdfs:label bij [ProjectreferentieOpdrachtnemer] | A    |       |           |
| Omschrijving                   | Omschrijving project            | rdfs:comment bij [Revisieproject]               | A    |       |           |
| Contactpersoon                 | Contactpersoon                  | rdfs:label bij [Contactpersoon]                 | A    |       |           |
| WijzeVanInwinningKnooppunt     | Wijze van inwinning Knooppunt   | gwsw:hasReference [WijzeVanInwinningColl]       |      | A     |           |
| WijzeVanInwinningDeksel        | Wijze van inwinning Deksel      | gwsw:hasReference [WijzeVanInwinningColl]       |      | A     |           |
| WijzeVanInwinningLeiding       | Wijze van inwinning Leiding     | gwsw:hasReference [WijzeVanInwinningColl]       |      | A     |           |
| Knooppuntnamen                 | Beschikbare knooppuntnamen      | rdfs:label                                      | O    |       |           |
| WijzeVanInwinningXY            | Wijze van inwinning XY          | gwsw:hasReference [WijzeVanInwinningColl]       |      | A     |           |
| WijzeVanInwinningZ             | Wijze van inwinning X           | gwsw:hasReference [WijzeVanInwinningColl]       |      | A     |           |

[Revisieproject]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Revisieproject
[Opdrachtgever]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Opdrachtgever
[Opdrachtnemer]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Opdrachtnemer
[ProjectreferentieOpdrachtgever]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./ProjectreferentieOpdrachtgever
[ProjectreferentieOpdrachtnemer]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./ProjectreferentieOpdrachtnemer
[Contactpersoon]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Contactpersoon
[WijzeVanInwinningColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./WijzeVanInwinningColl

**Gegevens Knooppunt** (Put of Bouwwerk)  

| Veldcode             | Omschrijving               | Waardetype (in RDF-termen)                      | Heen | Terug | Opmerking        |
|----------------------|----------------------------|-------------------------------------------------|------|-------|------------------|
| Naam                 | Naam put of bouwwerk       | rdfs:label bij [Put] of [Bouwwerk]              | A    | A     |                  |
| Type                 | Type put of bouwwerk       | rdf:type [Put] of [Bouwwerk]                    | O    | A     |                  |
| NaamStelsel          | Naam stelsel               | rdfs:label bij [Stelsel]                        | A    | A     |                  |
| TypeStelsel          | Type stelsel               | rdf:type [Stelsel]                              | O    | O     |                  |
| DatumInwinning       | Datum inwinning            | gwsw:hasValue [DatumInwinning]                  |      | A     |                  |
| Vorm                 | Vorm put of bouwwerk       | gwsw:hasReference [VormPutColl]                 | O    | A     |                  |
| Breedte              | Breedte put of bouwwerk    | gwsw:hasValue [BreedtePut] of [BreedteBouwwerk] | O    | A     |                  |
| Lengte               | Lengte put of bouwwerk     | gwsw:hasValue [LengtePut] of [LengteBouwwerk]   | O    | A     |                  |
| Materiaal            | Materiaal put of bouwwerk  | gwsw:hasReference [MateriaalPutColl]            | O    | A     |                  |
| Bodemprofiel         | Bodemprofiel               | gwsw:hasReference [BodemprofielColl]            | O    | A     | Vanaf GWSW 1.6.1 |
| X                    | X coördinaat               | gwsw:hasValue [Punt]                            | A    | A     |                  |
| Y                    | Y coördinaat               | gwsw:hasValue [Punt]                            | A    | A     |                  |
| Z                    | Z coördinaat               | gwsw:hasValue [Punt]                            | O    | O     |                  |
| Hoogte               | Hoogte put of bouwwerk     | gwsw:hasValue [HoogtePut] of [HoogteBouwwerk]   | O    | A     |                  |
| StatusFunctioneren   | Status functioneren        | gwsw:hasReference [StatusFunctionerenColl]      | O    | A     |                  |
| Constructieonderdeel | Bevat constructieonderdeel | rdf:type [Constructieonderdeel]                 | O    | A     | String-array     |
| Drempelniveau        | Drempelniveau              | gwsw:hasValue [Drempelniveau]                   | O    | A     | Decimal-array    |
| Drempelbreedte       | Drempelbreedte             | gwsw:hasValue [Drempelbreedte]                  | O    | A     | Integer-array    |
| HoogteStellaag       | Hoogte stellaag            | gwsw:hasValue [HoogteStellaag]                  | O    | A     |                  |
| Waterstand           | Meting waterstand          | gwsw:hasValue [MetingWaterstand]                |      | A     |                  |
| Fotoreferentie       | Fotoreferentie             | rdfs:seeAlso bij [Put] of [Bouwwerk]            |      | O     | String-array     |
| Melding              | Melding meting knooppunt   | gwsw:hasReference [MeldingMetingKnooppuntColl]  |      | O     | String-array     |
| Opmerking            | Opmerking                  | gwsw:hasValue [Opmerking]                       |      | O     |                  |

[Put]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Put
[Bouwwerk]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Bouwwerk
[VormPutColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./VormPutColl
[BreedtePut]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BreedtePut
[BreedteBouwwerk]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BreedteBouwwerk
[LengtePut]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./LengtePut
[LengteBouwwerk]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./LengteBouwwerk
[MateriaalPutColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./MateriaalPutColl
[BodemprofielColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BodemprofielColl
[Punt]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Punt
[HoogtePut]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./HoogtePut
[HoogteBouwwerk]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./HoogteBouwwerk
[StatusFunctionerenColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./StatusFunctionerenColl
[Stelsel]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Stelsel
[Constructieonderdeel]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Constructieonderdeel
[Drempelniveau]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Drempelniveau
[Drempelbreedte]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Drempelbreedte  
[MeldingMetingKnooppuntColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./MeldingMetingKnooppuntColl
[DatumInwinning]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./DatumInwinning
[MetingWaterstand]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./MetingWaterstand
[HoogteStellaag]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./HoogteStellaag
[Opmerking]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Opmerking


**Gegevens Deksel**  

| Veldcode       | Omschrijving          | Waardetype (in RDF-termen)                  | Heen | Terug | Opmerking    |
|----------------|-----------------------|---------------------------------------------|------|-------|--------------|
| Naam           | Naam put of bouwwerk  | rdfs:label bij [Put] of [Bouwwerk]          | A    | A     |              |
| DatumInwinning | Datum inwinning       | gwsw:hasValue [DatumInwinning]              |      | A     |              |
| X              | X coördinaat          | gwsw:hasValue [Punt]                        | A    | A     |              |
| Y              | Y coördinaat          | gwsw:hasValue [Punt]                        | A    | A     |              |
| Z              | Z coördinaat          | gwsw:hasValue [Punt]                        | O    | O     |              |
| Type           | Type deksel           | rdf:type [Afdekking]                        | O    | A     |              |
| Vorm           | Vorm deksel           | gwsw:hasReference [VormDekselColl]          | O    | A     |              |
| Lengte         | Lengte deksel         | gwsw:hasValue [LengteDeksel]                | O    | A     |              |
| Breedte        | Breedte deksel        | gwsw:hasValue [BreedteDeksel]               | O    | A     |              |
| Materiaal      | Materiaal deksel      | gwsw:hasReference [MateriaalDekselColl]     | O    | A     |              |
| Melding        | Melding meting deksel | gwsw:hasReference [MeldingMetingDekselColl] |      | O     | String-array |
| Opmerking      | Opmerking             | gwsw:hasValue [Opmerking]                   |      | O     |              |
| Fotoreferentie | Fotoreferentie        | rdfs:seeAlso bij [Put] of [Bouwwerk]        |      | O     | String-array |

[Afdekking]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Afdekking
[VormDekselColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./VormDekselColl
[LengteDeksel]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./LengteDeksel
[BreedteDeksel]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BreedteDeksel
[MateriaalDekselColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./MateriaalDekselColl
[MeldingMetingDekselColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./MeldingMetingDekselColl

**Gegevens Leiding**  

| Veldcode           | Omschrijving            | Waardetype (in RDF-termen)                   | Heen | Terug | Opmerking    |
|--------------------|-------------------------|----------------------------------------------|------|-------|--------------|
| Naam               | Naam leiding            | rdfs:label bij [Leiding]                     | A    | A     |              |
| Type               | Type leiding            | rdf:type [Leiding]                           | O    | A     |              |
| NaamStelsel        | Naam stelsel            | rdfs:label bij [Stelsel]                     | A    | A     |              |
| TypeStelsel        | Type stelsel            | rdf:type [Stelsel]                           | O    | O     |              |
| DatumInwinning     | Datum inwinning         | gwsw:hasValue [DatumInwinning]               |      | A     |              |
| NaamKnooppuntBegin | Naam knooppunt begin    | rdfs:label bij [Put] of [Bouwwerk]           | A    | A     |              |
| NaamKnooppuntEind  | Naam knooppunt eind     | rdfs:label bij [Put] of [Bouwwerk]           | A    | A     |              |
| BobKnooppuntBegin  | Bob bij knooppunt begin | gwsw:hasValue [BobBeginpuntLeiding]          | O    | A     |              |
| BobKnooppuntEind   | Bob bij knooppunt eind  | gwsw:hasValue [BobEindpuntLeiding]           | O    | A     |              |
| BbbKnooppuntBegin  | Bbb bij knooppunt begin | gwsw:hasValue [BbbBeginpuntLeiding]          |      | A     |              |
| BbbKnooppuntEind   | Bbb bij knooppunt eind  | gwsw:hasValue [BbbEindpuntLeiding]           |      | A     |              |
| StatusFunctioneren | Status functioneren     | gwsw:hasReference [StatusFunctionerenColl]   | O    | A     |              |
| Vorm               | Vorm leiding            | gwsw:hasReference [VormLeidingColl]          | O    | A     |              |
| Hoogte             | Hoogte leiding          | gwsw:hasValue [HoogteLeiding]                | O    | A     |              |
| Breedte            | Breedte leiding         | gwsw:hasValue [BreedteLeiding]               | O    | A     |              |
| Materiaal          | Materiaal leiding       | gwsw:hasReference [MateriaalLeidingColl]     | O    | A     |              |
| Fotoreferentie     | Fotoreferentie          | rdfs:seeAlso bij [Leiding]                   |      | O     | String-array |
| Melding            | Melding meting leiding  | gwsw:hasReference [MeldingMetingLeidingColl] |      | O     | String-array |
| Opmerking          | Opmerking               | gwsw:hasValue [Opmerking]                    |      | O     |              |

[Leiding]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Leiding
[BobBeginpuntLeiding]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BobBeginpuntLeiding
[BobEindpuntLeiding]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BobEindpuntLeiding
[BbbBeginpuntLeiding]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BbbBeginpuntLeiding
[BbbEindpuntLeiding]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BbbEindpuntLeiding
[VormLeidingColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./VormLeidingColl
[HoogteLeiding]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./HoogteLeiding
[BreedteLeiding]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BreedteLeiding
[MateriaalLeidingColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./MateriaalLeidingColl
[MeldingMetingLeidingColl]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./MeldingMetingLeidingColl

## Voorstel nieuwe versie

**Samenvatting wijzigingen:**
- Groep Project wordt Algemeen (breder, ook voor niet-revisie uitwisseling)
- Groep Deksel wordt Afdekking (breder, ook rooster, luik enzo)
- Nieuwe groep Stelsel (ook bruikbaar voor Gebied)
- Nieuwe groepen Wand en Doorlaat (meervoudige constructieonderdelen)
- Veldcodes voor WijzeVanInwinning van projectniveau naar objectniveau (kan per object variëren)
- Veldcode DatumInwinning vervalt in groep Afdekking (zie ook Uitgangspunten)
- Veldcode TypeStelsel, HoogteStellaag, Drempelniveau, Drempelbreedte vervalt in groep Knooppunt
- Veldcode HoogteStellaag verhuist naar groep Afdekking
- Veldcodes X,Y,Z vervallen in groep Knooppunt en Deksel, zijn vervangen door Punt met GeoJSON-notatie "Point": \[X,Y(,Z)\]
- Veldcode Lijn toegevoegd aan groep Leiding, met de GeoJSON-notatie "LineString": \[ \[X,Y(,Z)\], \[X,Y(,Z)\], \[X,Y(,Z)\] \]
- In de CSV-vorm de arrays noteren conform de JSON-notatie, was pipe-teken, wordt \[..., ...\] (vanwege de meer complexe LineString-arrays, zie hiervoor)
- Veldcode Maaiveld toegevoegd aan groep Knooppunt, met GeoJSON-notatie "Point": \[X,Y,Z\] (het punt met de meet-positie en gemeten niveau)

**Uitgangspunten:** 
- Bij alleen metingen van onderdeel-groepen (bijvoorbeeld bij inmeten deksels, niet tillen) altijd ook de groep Stelsel (met daarin Naam) en de groep Knooppunt (met daarin Naam, NaamStelsel en DatumInwinning) vullen.
- Onderdelen van Knooppunt die meervoudig kunnen voorkomen in aparte groep opnemen (voorlopig alleen Wand en Doorlaat)
- Deze vorm blijft (met minimale overhead) bruikbaar voor CSV, JSON en GeoJSON

**Formaten**  

Enkele formaatregels bij **JSON** en **GeoJSON** (zie ook https://nl.wikipedia.org/wiki/JSON)
- **Extensie** - De extensie van een JSON-bestand is ".json" *(altijd kleine letters)*. **extensie .geojson ook gebruiken?**
- **Velden** - De JSON-veldnamen zijn hoofdletter-gevoelig, gebruik de exacte Veldcode-naam uit de hierna volgende tabellen.
- **String-waarden** - Noteren tussen aanhalingstekens (double quotation): `"tekst"`
- **Datum-waarden** - Noteren als string met xsd:date opbouw: `"yyyy-mm-dd"`
- **Getal-waarden** - Integers *(zonder decimaal-teken)* en decimals *(altijd met decimaal-teken ".")* noteren als: `333` en `333.33`
- **Boolean-waarden** - Waar/onwaar, noteren als: `true` of `false`
- **Nul-waarden** - Velden met een lege waarde noteren als: `null` (kunnen bijvoorbeeld voorkomen in GeoJSON om aan te geven dat een object geen geometrie heeft)
- **Arrays** - Een JSON-veld kan verwijzen naar een waarde-array, noteren als: `[ "tekst1", "tekst2" ]` of `[1, 2, 3]` of `[ [1, 2, 3], [4, 5, 6] ]` 
(arrays kunnen alle waardetypen - inclusief arrays - bevatten).

Enkele opmerkingen bij **GeoJSON**
- **QGIS/GDAL** - Het GeoJSON-formaat is getest op de import van QGIS. De GeoJSON-functionaliteit van QGIS is gebaseerd op de GDAL-bibliotheek.
- **GeoJSON-versie** - GDAL gebruikt als basis de 2008-versie van GeoJSON, optioneel wordt ook de RFC 7946 (uit 2016) toegepast. 
- **Coördinaatsysteem** - EPSG:7415 hanteren, conform het GWSW (in de 2008-versie is het gebruik van een specifiek referentiesysteeem toegestaan, 
in RFC 7946 ontbreekt die mogelijkheid, daar wordt uitgegaan van WGS 84).
- **Objecten zonder geometrie** - Objecten met null-geometrie zijn toegestaan (conform RFC 7946), dat geldt bijvoorbeeld voor de objectgroep Algemeen (zie hierna).
- **Gecombineerde lagen** - In het GeoJSON-bestand worden de lagen (of groepen, zie hierna) gecombineerd, er wordt een GWSW-specifieke GeoJSON-interpretatie gebruikt.
Deze GeoJSON-vorm werkt op QGIS/GDAL maar een algemene definitie hiervan is niet beschikbaar (standaard bevat een GeoJSON-bestand één laag).   
- **Objectnamen** - Zet in de feature-properties de property Naam bovenaan, de inhoud van Naam wordt dan de objectidentificatie in GIS (getest met QGIS). 

Enkele formaatregels bij **CSV**
- **Arrays** - De CSV-cellen kunnen een array met waarden bevatten, deze noteren conform JSON *(gebruik aanhalingstekens als het CSV-scheidingsteken een komma is)*:
`"[tekst1, tekst2]"` of `"[1, 2, 3]"` of `"[ [1, 2, 3], [4, 5, 6] ]"`. Als `tekst1` het CSV-scheidingsteken bevat, dan als volgt noteren: `"[""tekst1"", tekst2]"`

### Algemeen

**Algemene informatie** 

| Veldcode                       | Omschrijving                    | Waardetype (in RDF-termen)                      | H | T | Opmerking                                                     |
|--------------------------------|---------------------------------|-------------------------------------------------|---|---|---------------------------------------------------------------|
| Versie                         | Versie van dit formaat          | gwsw:hasValue "1.0.0"                           | A | A | Vigerende versie 1.0.0                                        |
| Naam                           | Naam project                    | rdfs:label bij [Project]                        | A | A | Identificatie van het werk                                    |
| Type                           | Type project                    | rdf:type [Project]                              | O |   | Nu vooral [Revisieproject]                                    |
| Omschrijving                   | Omschrijving                    | rdfs:comment bij [Project]                      | O |   |                                                               |
| Bestandstype                   | Soort uitwisseling              | "Revisie heen" of "Revisie terug"               | A | A | Meer soorten volgen ("CAD ontwerp", ...)                      |
| Opdrachtgever                  | Opdrachtgever                   | rdfs:label bij [Opdrachtgever]                  | O |   |                                                               |
| Opdrachtnemer                  | Opdrachtnemer                   | rdfs:label bij [Opdrachtnemer]                  | O |   |                                                               |
| ProjectreferentieOpdrachtgever | Projectreferentie Opdrachtgever | rdfs:label bij [ProjectreferentieOpdrachtgever] | O |   |                                                               |
| ProjectreferentieOpdrachtnemer | Projectreferentie Opdrachtnemer | rdfs:label bij [ProjectreferentieOpdrachtnemer] | O |   |                                                               |
| Contactpersoon                 | Contactpersoon                  | rdfs:label bij [Contactpersoon]                 | O |   |                                                               |
| Knooppuntnamen                 | Beschikbare knooppuntnamen      | rdfs:label bij [Put] of [Bouwwerk]              | O |   | \[string-array\] Voor nieuwe knooppunten (ontbrekend in Heen) |

[Project]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Project

### Stelsel

**Gegevens van [Stelsel] (of [Gebied])**

De groepering van putten, bouwwerken en leidingen.

| Veldcode | Omschrijving           | Waardetype (in RDF-termen)           | H | T | Opmerking                                                                                                     |
|----------|------------------------|--------------------------------------|---|---|---------------------------------------------------------------------------------------------------------------|
| Naam     | Naam stelsel of gebied | rdfs:label bij [Stelsel] of [Gebied] | A | A | Gebruik conform GWSW naam [Stelsel]. Als [Stelsel] ontbreekt in het beheersysteem, gebruik dan naam [Gebied]. |
| Type     | Type stelsel of gebied | rdf:type [Stelsel] of [Gebied]       | A | A | Gebruik conform GWSW type [Stelsel]. Als [Stelsel] ontbreekt in het beheersysteem, gebruik dan type [Gebied]. |

[Gebied]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Gebied

### Knooppunt

**Gegevens van [Put] of [Bouwwerk]**

| Veldcode             | Omschrijving               | Waardetype (in RDF-termen)                      | H | T | Opmerking                                                     |
|----------------------|----------------------------|-------------------------------------------------|---|---|---------------------------------------------------------------|
| Naam                 | Naam put of bouwwerk       | rdfs:label bij [Put] of [Bouwwerk]              | A | A |                                                               |
| NaamStelsel          | Naam stelsel of gebied     | rdfs:label bij [Stelsel] of [Gebied]            | A | A |                                                               |
| Type                 | Type put of bouwwerk       | rdf:type [Put] of [Bouwwerk]                    | A | O |                                                               |
| DatumInwinning       | Datum inwinning            | gwsw:hasValue [DatumInwinning]                  | O | O |                                                               |
| WijzeVanInwinning    | Wijze van inwinning        | gwsw:hasReference [WijzeVanInwinningColl]       | O | O | Algemeen voor het object                                      |
| Punt                 | Coördinaat X,Y(,Z)         | gwsw:hasValue [Punt]                            | A | O | \[GeoJSON Point\] Zie [Putorientatie] of [Bouwwerkorientatie] |
| Maaiveld             | Coördinaat X,Y,Z           | gwsw:hasValue [Punt]                            | O | O | \[GeoJSON Point\] Zie [Maaiveldorientatie]                    |
| WijzeVanInwinningXY  | Wijze van inwinning XY     | gwsw:hasReference [WijzeVanInwinningColl]       | O | O |                                                               |
| WijzeVanInwinningZ   | Wijze van inwinning niveau | gwsw:hasReference [WijzeVanInwinningColl]       |   | O | Niveau = binnenbovenkant middelpunt bodem                     |
| Vorm                 | Vorm put of bouwwerk       | gwsw:hasReference [VormPutColl]                 | O | O |                                                               |
| Lengte               | Lengte put of bouwwerk     | gwsw:hasValue [LengtePut] of [LengteBouwwerk]   | O | O |                                                               |
| Breedte              | Breedte put of bouwwerk    | gwsw:hasValue [BreedtePut] of [BreedteBouwwerk] | O | O |                                                               |
| Hoogte               | Hoogte put of bouwwerk     | gwsw:hasValue [HoogtePut] of [HoogteBouwwerk]   | O | O |                                                               |
| Materiaal            | Materiaal put of bouwwerk  | gwsw:hasReference [MateriaalPutColl]            | O | O |                                                               |
| Bodemprofiel         | Bodemprofiel               | gwsw:hasReference [BodemprofielColl]            | O | O | Vanaf GWSW 1.6.1                                              |
| StatusFunctioneren   | Status functioneren        | gwsw:hasReference [StatusFunctionerenColl]      | O | O |                                                               |
| Constructieonderdeel | Bevat constructieonderdeel | rdf:type [Constructieonderdeel]                 | O | O | \[string-array\] Onderdelen, anders dan Wand of Doorlaat      |
| Waterstand           | Meting waterstand          | gwsw:hasValue [MetingWaterstand]                |   | O |                                                               |
| Fotoreferentie       | Fotoreferentie             | rdfs:seeAlso bij [Put] of [Bouwwerk]            |   | O | \[string-array\]                                              |
| Melding              | Melding meting knooppunt   | gwsw:hasReference [MeldingMetingKnooppuntColl]  |   | O | \[string-array\]                                              |
| Opmerking            | Opmerking                  | gwsw:hasValue [Opmerking]                       |   | O |                                                               |

[Putorientatie]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Putorientatie
[Bouwwerkorientatie]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Bouwwerkorientatie
[Maaiveldorientatie]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Maaiveldorientatie

### Afdekking

**Gegevens van [Afdekking] op [Put] of [Bouwwerk]**

| Veldcode            | Omschrijving               | Waardetype (in RDF-termen)                  | H | T | Opmerking                                |
|---------------------|----------------------------|---------------------------------------------|---|---|------------------------------------------|
| Naam                | Naam put of bouwwerk       | rdfs:label bij [Put] of [Bouwwerk]          | A | A |                                          |
| Type                | Type afdekking             | rdf:type [Afdekking]                        | A | A | Deksel, Luik, ...                        |
| Punt                | Coördinaat X,Y(,Z)         | gwsw:hasValue [Punt]                        | O | A | \[GeoJSON Point\] Zie [Dekselorientatie] |
| WijzeVanInwinningXY | Wijze van inwinning XY     | gwsw:hasReference [WijzeVanInwinningColl]   |   | A |                                          |
| WijzeVanInwinningZ  | Wijze van inwinning niveau | gwsw:hasReference [WijzeVanInwinningColl]   |   | A | Niveau = bovenkant middelpunt afdekking  |
| Vorm                | Vorm afdekking             | gwsw:hasReference [VormDekselColl]          | O | O |                                          |
| Lengte              | Lengte afdekking           | gwsw:hasValue [LengteDeksel]                | O | O |                                          |
| Breedte             | Breedte afdekking          | gwsw:hasValue [BreedteDeksel]               | O | O |                                          |
| Materiaal           | Materiaal afdekking        | gwsw:hasReference [MateriaalDekselColl]     | O | O |                                          |
| HoogteStellaag      | Hoogte stellaag            | gwsw:hasValue [HoogteStellaag]              | O | O |                                          |
| Fotoreferentie      | Fotoreferentie             | rdfs:seeAlso bij [Put] of [Bouwwerk]        |   | O | \[string-array\]                         |
| Melding             | Melding meting afdekking   | gwsw:hasReference [MeldingMetingDekselColl] |   | O | \[string-array\]                         |
| Opmerking           | Opmerking                  | gwsw:hasValue [Opmerking]                   |   | O |                                          |

[Dekselorientatie]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Dekselorientatie

### Wand

**Gegevens van [Wand] in [Put] of [Bouwwerk]**

| Veldcode            | Omschrijving               | Waardetype (in RDF-termen)                | H | T | Opmerking                                   |
|---------------------|----------------------------|-------------------------------------------|---|---|---------------------------------------------|
| Naam                | Naam put of bouwwerk       | rdfs:label bij [Put] of [Bouwwerk]        | A | A |                                             |
| Type                | Type wand                  | rdf:type [Wand]                           | A | A | Overstortdrempel, Stuwmuur, ...             |
| Punt                | Coördinaat X,Y(,Z)         | gwsw:hasValue [Punt]                      | A | A | \[GeoJSON Point\] Zie [Onderdeelorientatie] |
| WijzeVanInwinningXY | Wijze van inwinning XY     | gwsw:hasReference [WijzeVanInwinningColl] |   | O |                                             |
| WijzeVanInwinningZ  | Wijze van inwinning niveau | gwsw:hasReference [WijzeVanInwinningColl] |   | A | Niveau = bovenkant wand                     |
| Breedte             | Breedte van de wand        | gwsw:hasValue [Drempelbreedte]            | O | O |                                             |
| Opmerking           | Opmerking                  | gwsw:hasValue [Opmerking]                 |   | O |                                             |

[Wand]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Wand
[Onderdeelorientatie]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Onderdeelorientatie

### Doorlaat

**Gegevens van [Doorlaat] in [Put] of [Bouwwerk]**

| Veldcode            | Omschrijving               | Waardetype (in RDF-termen)                | H | T | Opmerking                                   |
|---------------------|----------------------------|-------------------------------------------|---|---|---------------------------------------------|
| Naam                | Naam put of bouwwerk       | rdfs:label bij [Put] of [Bouwwerk]        | A | A |                                             |
| Type                | Type doorlaat              | rdf:type [Doorlaat]                       | A | A | OpeningInWand, Terugslagklep, ...           |
| Punt                | Coördinaat X,Y(,Z)         | gwsw:hasValue [Punt]                      | A | A | \[GeoJSON Point\] Zie [Onderdeelorientatie] |
| WijzeVanInwinningXY | Wijze van inwinning XY     | gwsw:hasReference [WijzeVanInwinningColl] |   | O |                                             |
| WijzeVanInwinningZ  | Wijze van inwinning niveau | gwsw:hasReference [WijzeVanInwinningColl] |   | A | Niveau = onderkant opening                  |
| Vorm                | Vorm opening               | gwsw:hasReference [VormOpening]           | O | O |                                             |
| Breedte             | Breedte opening            | gwsw:hasValue [BreedteOpening]            | O | O |                                             |
| Hoogte              | Hoogte opening             | gwsw:hasValue [HoogteOpening]             | O | O |                                             |
| Opmerking           | Opmerking                  | gwsw:hasValue [Opmerking]                 | O | O |                                             |

[Doorlaat]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Doorlaat
[BreedteOpening]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./BreedteOpening
[HoogteOpening]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./HoogteOpening
[VormOpening]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./VormOpening

### Leiding

**Gegevens van [Leiding]**

| Veldcode            | Omschrijving            | Waardetype (in RDF-termen)                   | H | T | Opmerking                                                                      |
|---------------------|-------------------------|----------------------------------------------|---|---|--------------------------------------------------------------------------------|
| Naam                | Naam leiding            | rdfs:label bij [Leiding]                     | A | A |                                                                                |
| NaamStelsel         | Naam stelsel of gebied  | rdfs:label bij [Stelsel] of [Gebied]         | A | A |                                                                                |
| Type                | Type leiding            | rdf:type [Leiding]                           | A | A |                                                                                |
| TypeStelsel         | Type stelsel            | rdf:type [Stelsel]                           | O | O | Invullen als in de groep Stelsel verwezen is naar [Gebied] (niet GWSW-conform) |
| DatumInwinning      | Datum inwinning         | gwsw:hasValue [DatumInwinning]               |   | A |                                                                                |
| WijzeVanInwinning   | Wijze van inwinning     | gwsw:hasReference [WijzeVanInwinningColl]    |   | A | Algemeen voor het object                                                       |
| Lijn                | Coördinaatreeks X,Y(,Z) | gwsw:hasValue [Lijn]                         | A | O | \[GeoJSON LineString\] Zie [Leidingorientatie]. Toepasbaar bij goten enzo.     |
| WijzeVanInwinningXY | Wijze van inwinning XY  | gwsw:hasReference [WijzeVanInwinningColl]    |   | O |                                                                                |
| WijzeVanInwinningZ  | Wijze van inwinning bob | gwsw:hasReference [WijzeVanInwinningColl]    |   | O | Bob = binnenonderkant buis                                                     |
| NaamKnooppuntBegin  | Naam knooppunt begin    | rdfs:label bij [Put] of [Bouwwerk]           | A | A |                                                                                |
| NaamKnooppuntEind   | Naam knooppunt eind     | rdfs:label bij [Put] of [Bouwwerk]           | A | A |                                                                                |
| BobKnooppuntBegin   | Bob bij knooppunt begin | gwsw:hasValue [BobBeginpuntLeiding]          | O | O | Zie [Leidingorientatie]                                                        |
| BobKnooppuntEind    | Bob bij knooppunt eind  | gwsw:hasValue [BobEindpuntLeiding]           | O | O |                                                                                |
| BbbKnooppuntBegin   | Bbb bij knooppunt begin | gwsw:hasValue [BbbBeginpuntLeiding]          |   | O |                                                                                |
| BbbKnooppuntEind    | Bbb bij knooppunt eind  | gwsw:hasValue [BbbEindpuntLeiding]           |   | O |                                                                                |
| StatusFunctioneren  | Status functioneren     | gwsw:hasReference [StatusFunctionerenColl]   | O | O |                                                                                |
| Vorm                | Vorm leiding            | gwsw:hasReference [VormLeidingColl]          | O | O |                                                                                |
| Breedte             | Breedte leiding         | gwsw:hasValue [BreedteLeiding]               | O | O |                                                                                |
| Hoogte              | Hoogte leiding          | gwsw:hasValue [HoogteLeiding]                | O | O |                                                                                |
| Materiaal           | Materiaal leiding       | gwsw:hasReference [MateriaalLeidingColl]     | O | O |                                                                                |
| Fotoreferentie      | Fotoreferentie          | rdfs:seeAlso bij [Leiding]                   |   | O | \[string-array\]                                                               |
| Melding             | Melding meting leiding  | gwsw:hasReference [MeldingMetingLeidingColl] |   | O | \[string-array\]                                                               |
| Opmerking           | Opmerking               | gwsw:hasValue [Opmerking]                    |   | O |                                                                                |

[Leidingorientatie]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Leidingorientatie
[Lijn]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./Lijn

# Datamodel

## Nieuwe GWSW-concepten

Veel URI's staan al in het GWSW datamodel, voor het deelmodel Revisies zijn ook een aantal nieuwe concepten uitgewerkt. In de eerdere hoofdstukken zijn enkele van deze concepten al voorbijgekomen.

Een overzicht van de nieuw toegevoegde concepten (vanaf concept-deelmodel GWSW-Revisies 1.6.1):

| URI                          | Naam                              | Definitie                                                                                |
|------------------------------|-----------------------------------|------------------------------------------------------------------------------------------|
| [Revisieproject]             | Revisieproject                    |                                                                                          |
| [InmetenKnooppunt]           | Inmeten knooppunt                 | Inmeten van een put of bouwwerk met eventuele deksel (deelactiviteit van Revisieproject) |
| [InmetenLeiding]             | Inmeten leiding                   | Inmeten van een leiding (deelactiviteit van Revisieproject)                              |
| [MetingWaterstand]           | Meting waterstand                 | De gemeten waterstand tov de constructiebodem                                            |
| [MeldingMetingKnooppuntColl] | Melding bij meting knooppunt      | Voorgedefinieerde meldingen bij de meting van een put of bouwwerk                        |
| [MeldingMetingDekselColl]    | Melding bij meting deksel         | Voorgedefinieerde meldingen bij de meting van een deksel                                 |
| [MeldingMetingLeidingColl]   | Melding bij meting leiding        | Voorgedefinieerde meldingen bij de meting van een leiding                                |
| [BbbBeginpuntLeiding]        | Binnenbovenkant beginpunt leiding | Het niveau van de binnenbovenkant bij het beginpunt                                      |
| [BbbEindpuntLeiding]         | Binnenbovenkant eindpunt leiding  | Het niveau van de binnenbovenkant bij het eindpunt                                       |

[InmetenKnooppunt]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./InmetenKnooppunt
[InmetenLeiding]: https://data.gwsw.nl/Revisies/index.html?menu_item=classes&item=./InmetenLeiding

## Datamodel Revisies in RDF

Hieronder staat het eerste concept model met daarin alleen de toegevoegde revisie-concepten (in de uitgewerkte versies wordt de prefix rev: vervangen door gwsw: ).  

De uitwerking van het complete deelmodel GWSW-Revisies staat onder https://data.gwsw.nl/Revisies.

<div class="example"><div class="example-title marker">Datamodel: Revisieproject</div><pre>

rev:Revisieproject rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Project ;
  rdfs:label "Revisieproject";
  skos:definition "Revisieproject" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenKnooppunt (min=0)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetenKnooppunt ;
    owl:onProperty gwsw:hasPart ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenLeiding (min=0)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetenLeiding ;
    owl:onProperty gwsw:hasPart ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:InmetenKnooppunt rdf:type owl:Class ;
  rdfs:subClassOf gwsw:Meten ;
  rdfs:label "Inmeten knooppunt" ;
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
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk MeldingMetingKnooppunt (max=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:MeldingMetingKnooppunt ;
    owl:onProperty gwsw:hasAspect ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk MeldingMetingDeksel (min=0, er kunnen meerdere (niet geïdentificeerde) deksels zijn)
    rdf:type owl:Restriction ;
    owl:onClass rev:MeldingMetingDeksel ;
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
rev:InmetenLeiding rdf:type owl:Class ;
  rdfs:subClassOf gwsw:Meten ;
  rdfs:label "Inmeten leiding" ;
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
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk MeldingMetingLeiding (max=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:MeldingMetingLeiding ;
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
rev:MeldingMetingKnooppunt rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Melding meting knooppunt";
  skos:definition "Melding bij meting van put of bouwwerk";
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenKnooppunt (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetenKnooppunt ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MeldingMetingDeksel rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Melding meting deksel" ;
  skos:definition "Melding bij meting van putdeksel" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenKnooppunt (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetengKnooppunt ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MeldingMetingLeiding rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Melding meting leiding" ;
  skos:definition "Melding bij meting van leiding" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenLeiding (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetenLeiding ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MetingWaterstand rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Gemeten waterstand bij revisie-object" ;
  skos:definition "Gemeten waterstand bij de meting van een object, de hoogte tov de bodem";
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenKnooppunt (exact=1)
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

## Projectmodel revisies in RDF (dataset)

Als we de meetgegevens combineren met het eerder beschreven projectmodel kan een GWSW-dataset worden opgebouwd.
Zo'n GWSW-dataset omvat de complete uitwisseling binnen het revisieproject, dus zowel de gegevens van de heen- als van de terug-levering.  

Het ziet er dan als volgt uit (in één GWSW-dataset):

<div class="example-dataset"><div class="example-title marker">Dataset: Voorbeeld revisieproject</div><pre>

\# ex: - prefix met de individuen, de objecten in de projectdefintie en in het terrein
\# gwsw: - bestaande gwsw-concepten
\# rev: - concepten in deelmodel GWSW-Revisies
\# rdf: / rdfs: - generieke RDF-concepten

{ex:01} \# Revisieproject
  rdfs:label "Inmeetproject Hollandse buurt";
  rdf:type rev:Revisieproject ;
  gwsw:isOutputOf \[ rdf:type gwsw:Opdrachtgever ; rdfs:label "Gemeente Juinen" ; ] ;
  gwsw:hasAspect \[ rdf:type rev:ProjectreferentieOpdrachtnemer ; rdfs:label "Pr20250101_00892" ; ] ;
  gwsw:isOutputOf \[ rdf:type gwsw:Contactpersoon ; rdfs:label "Walter de Rochebrune" ; ] ;
  rdfs:comment "Dit is een inmeetproject" ;
.
{ex:10} \# Inmeten knooppunt - activiteit
  gwsw:isPartOf {ex:01} ; 
  rdf:type rev:InmetenKnooppunt ;
.
{ex:10} \# Inmeten knooppunt - projectdefinitie (heen)
  gwsw:hasInput {ex:11i} ;
.
{ex:10} \# Inmeten knooppunt - resultaat (terug)
  gwsw:hasOutput {ex:11o} ; \# Gebruik een andere URI dan ex:11i, ook bij hetzelfde knooppunt (houdt dezelfde naam)
  gwsw:hasAspect \[ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference gwsw:Inmeting; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:DatumInwinning ; gwsw:hasValue "20240828"^^xsd:date. ; ] ;
  rdfs:seeAlso _:24084\G265_1.jpg, _:24084\G265_2.jpg;
  gwsw:hasAspect \[ rdf:type rev:MeldingMetingKnooppunt ; rev:hasReference rev:GeurWaargenomen ; ] ;
  gwsw:hasAspect \[ rdf:type rev:MeldingMetingDeksel ; rev:hasReference rev:DekselGebroken ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:Opmerking ; gwsw:hasValue "Mooi weer buiten" ; ] ;
.
{ex:11i/ex:11o} \# Knooppunt heen en terug
  rdf:type  gwsw:ExterneOverstortput; /# Ga hier uit van supertype gwsw:Put 
  rdfs:label "KN90001" ;
  gwsw:hasAspect \[ rdf:type gwsw:VormPut ; gwsw:hasReference gwsw:Rechthoekig ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:BreedtePut ; gwsw:hasValue 800 ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:LengtePut ; gwsw:hasValue 800 ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:MateriaalPut ; gwsw:hasReference gwsw:Beton ; ] ;
  gwsw:hasPart \[ rdf:type gwsw:Stroomprofiel; gwsw:hasAspect \[ rdf:type gwsw:VormStroomprofiel ; gwsw:hasReference gwsw:Geulprofiel ; ] ; ] ;
  gwsw:hasPart \[ rdf:type gwsw:Stellaag; gwsw:hasAspect \[ rdf:type gwsw:HoogteStellaag ; gwsw:hasValue 45 ; ] ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:HoogtePut ; gwsw:hasValue 2140 ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference gwsw:InGebruik ; ] ;
  gwsw:isPartOf \[ rdf:type gwsw:GemengdStelsel; ] ;
  gwsw:hasPart \[ rdf:type gwsw:Overstortdrempel; gwsw:hasAspect \[ rdf:type gwsw:Drempelniveau ; gwsw:hasValue 7.9 ; ] ; ] ;
.
{ex:11i/ex:11o} \# Knooppunt heen en terug: de verbinding
  gwsw:hasAspect {ex:12i/ex:12o} ;
.
{ex:12i/ex:12o} 
  rdf:type gwsw:Putorientatie ;
  gwsw:hasAspect \[ rdf:type gwsw:Punt ; gwsw:hasValue "<gml:Point xmlns:gml=\"https:www.opengis.net/gml\"><gml:pos>168443.01 442691.00 22.42</gml:pos></gml:Point>"^^geo:gmlLiteral . ; ] ;
.
{ex:11o} \# Knooppunt terug
  gwsw:hasAspect \[ rdf:type rev:MetingWaterstand ; gwsw:hasValue 0.2 ; ] ;
.
{ex:13i/ex:13o} \# Deksel heen en terug 
  rdf:type gwsw:Putdeksel ;
  gwsw:isPartOf {ex:11i/i11o} ; # Afleiden uit {Deksel.NaamKnooppunt}
  gwsw:hasAspect \[ rdf:type gwsw:VormDeksel ; gwsw:hasReference gwsw:Rond ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:BreedteDeksel ; gwsw:hasValue 0.58 ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:LengteDeksel ; gwsw:hasValue 0.58 ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:MateriaalDeksel ; gwsw:hasReference gwsw:Gietijzer ; ] ;
.
{ex:20} \# Inmeten Leiding - activiteit
  gwsw:isPartOf {ex:01} ; 
  rdf:type rev:InmetenLeiding ;
.
{ex:20} \# Inmeten Leiding - projectdefinitie (heen)
  gwsw:hasInput {ex:21i} ;
.
{ex:20} \# InmetenLeiding: - resultaat (terug)
  gwsw:hasOutput {ex:21o} ; \# Gebruik een andere URI dan ex:21i, ook bij dezelfde leiding (houdt dezelfde naam)
  gwsw:hasAspect \[ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference gwsw:Inmeting; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:DatumInwinning ; gwsw:hasValue "20250102"^^xsd:date. ; ] ;
  gwsw:hasAspect \[ rdf:type rev:MeldingMetingLeiding ; rev:hasReference rev:WortelsInObject ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:Opmerking ; gwsw:hasValue "De leiding was rond" ; ] ;
  rdfs:seeAlso _:24084\G293_1.jpg, _:24084\G293_2.jpg ;
.
{ex:21i/ex:21o} \# Leiding heen en terug
  rdf:type gwsw:GemengdRiool ;
  rdfs:label "90003_1" ;
  gwsw:hasAspect \[ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference gwsw:InGebruik ; ] ;
  gwsw:isPartOf \[ rdf:type gwsw:GemengdStelsel; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:VormLeiding ; gwsw:hasReference gwsw:Rond ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:HoogteLeiding ; gwsw:hasValue 300 ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:BreedteLeiding ; gwsw:hasValue 300 ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:MateriaalLeiding ; gwsw:hasReference gwsw:Beton ; ] ;
.
{ex:21i/ex:21o} \# Leiding heen en terug: de verbinding
  gwsw:hasAspect {ex:22} ;
.
{ex:22} 
  rdf:type gwsw:Leidingorientatie ; \# Afleiden uit {Leiding.KnooppuntBegin} en {Leiding.KnooppuntEind} 
  gwsw:hasAspect \[ rdf:type gwsw:Lijn ; gwsw:hasValue "<gml:LineString xmlns:gml=\"https:www.opengis.net/gml\"><gml:posList srsDimension=\"3\">168462.01 442691.30 22.45 168503.00 442701.30 22.45</gml:posList></gml:LineString>"^^geo:gmlLiteral ; ] ;
  gwsw:hasPart {ex:23} ;
  gwsw:hasPart {ex:24} ;
.
{ex:23} \# Leiding heen en terug: beginpunt
  rdf:type gwsw:BeginpuntLeiding ; 
  gwsw:hasConnection {ex:12} ; \# Afleiden uit {Leiding.KnooppuntBegin}
  gwsw:hasAspect \[ rdf:type gwsw:BobBeginpuntLeiding ; gwsw:hasValue 22.45 ; ] ;
.
{ex:24} \# Leiding heen en terug: eindpunt 
  rdf:type gwsw:EindpuntLeiding ; 
  gwsw:hasConnection {ex:12} ; \# Afleiden uit {Leiding.KnooppuntEind} {ex:12} is natuurlijk een andere put
  gwsw:hasAspect \[ rdf:type gwsw:BobEindpuntLeiding ; gwsw:hasValue 22.46 ; ] ;
.
{ex:241} \# Beginpunt terug
  gwsw:hasAspect \[ rdf:type rev:BbbBeginpuntLeiding ; gwsw:hasValue 22.75} ; ] ;
.
{ex:24o} \# Eindpunt terug
  gwsw:hasAspect \[ rdf:type rev:BbbEindpuntLeiding ; gwsw:hasValue 22.76 ; ] ;
.
 </pre> </div>

# Bijlagen

## OroX Uitwisselbestand
**Voorbeeld bestand volgens het OroX-protocol**  
<div class="box"><pre>
@prefix rdf: &lt;http://www.w3.org/1999/02/22-rdf-syntax-ns#&gt;.
@prefix rdfs: &lt;http://www.w3.org/2000/01/rdf-schema#&gt;.
@prefix owl: &lt;http://www.w3.org/2002/07/owl#&gt;.
@prefix skos: &lt;http://www.w3.org/2004/02/skos/core#&gt;.
@prefix xsd: &lt;http://www.w3.org/2001/XMLSchema#&gt;.
@prefix geo: &lt;http://www.opengis.net/ont/geosparql#&gt;.
@prefix gwsw: &lt;http://data.gwsw.nl/1.6/totaal/&gt;.
@prefix ex: &lt;http://sparql.gwsw.nl/instances#&gt;.
ex:Proj_1 rdfs:label "Inmeten alles";
    rdfs:comment "Inmeting klein Juinen";
    a gwsw:Revisieproject;
	gwsw:hasInput [rdfs:label "Gemeente Juinen";
		a gwsw:Opdrachtgever],
		[rdfs:label "Hekking Meetadvies B.V.";
			a gwsw:Opdrachtnemer],
		[rdfs:label "Walter de Rochebrune";
			a gwsw:Contactpersoon];	
	gwsw:hasAspect [ a gwsw:ProjectreferentieOpdrachtgever;
		gwsw:hasValue "OPD12345" ], 
		[ a gwsw:ProjectreferentieOpdrachtnemer;
		gwsw:hasValue "AAN67890" ].
ex:Knp_2 rdfs:label "K0001";
    a gwsw:Inspectieput;
    gwsw:hasAspect [a gwsw:Putorientatie;
		gwsw:hasAspect [ a gwsw:Punt;
			gwsw:hasValue "<gml:Point xmlns:gml=\"http://www.opengis.net/gml\"><gml:pos>163042.58 383220.11 undefined</gml:pos></gml:Point>"^^geo:gmlLiteral ] ],
		[a gwsw:BreedtePut;
			gwsw:hasValue "800"^^xsd:integer],
		[a gwsw:LengtePut;
			gwsw:hasValue "800"^^xsd:integer],
		[a gwsw:VormPut;
			gwsw:hasReference gwsw:Rechthoekig],
		[a gwsw:MateriaalPut;
			gwsw:hasReference gwsw:Beton];
    gwsw:isPartOf ex:Stl_5;
    gwsw:hasPart [a gwsw:Stellaag].
ex:InmKnp_4 a gwsw:InmetenKnooppunt;
    gwsw:isPartOf ex:Proj_1;
    gwsw:hasInput ex:Knp_2;
    gwsw:hasAspect [ a gwsw:DatumInwinning;
			gwsw:hasValue "2026-01-01"^^xsd:date],
		[ a gwsw:MetingWaterstand;
			gwsw:hasValue "0.15"^^xsd:decimal];
	gwsw:hasOutput ex:Knp_20.
ex:Stl_5 rdfs:label "Centrum hoofd";
    a gwsw:GemengdStelsel.
ex:Knp_6 rdfs:label "K0002";
    a gwsw:ExterneOverstortput;
    gwsw:hasAspect [a gwsw:Putorientatie;
		gwsw:hasAspect [a gwsw:Punt;
			gwsw:hasValue "<gml:Point xmlns:gml=\"http://www.opengis.net/gml\"><gml:pos>163035.93 383176.51 undefined</gml:pos></gml:Point>"^^geo:gmlLiteral] ],
		[a gwsw:VormPut;
			gwsw:hasReference gwsw:Rechthoekig],
		[a gwsw:MateriaalPut;
			gwsw:hasReference gwsw:Beton];
    gwsw:isPartOf ex:Stl_5;
    gwsw:hasPart [a gwsw:Stellaag].
ex:InmKnp_8 a gwsw:InmetenKnooppunt;
    gwsw:isPartOf ex:Proj_1;
    gwsw:hasInput ex:Knp_6;
    gwsw:hasAspect [ a gwsw:DatumInwinning;
			gwsw:hasValue "2026-01-01"^^xsd:date],
		[ a gwsw:MetingWaterstand;
			gwsw:hasValue "0.1"^^xsd:decimal];
    gwsw:hasOutput ex:Knp_24.
ex:Dks_9 a gwsw:Afdekking;
    gwsw:isPartOf ex:Knp_2;
    gwsw:hasAspect [ a gwsw:Dekselorientatie;
		gwsw:hasAspect [a gwsw:Punt;
			gwsw:hasValue "<gml:Point xmlns:gml=\"http://www.opengis.net/gml\"><gml:pos>163042.58 383220.11 </gml:pos></gml:Point>"^^geo:gmlLiteral] ],
		[a gwsw:Dekselorientatie;
			gwsw:hasAspect [a gwsw:Putdekselniveau;
				gwsw:hasValue "15.28"^^xsd:decimal]]. 
ex:Dks_12 a gwsw:Afdekking;
    gwsw:isPartOf ex:Knp_6;
    gwsw:hasAspect [a gwsw:Dekselorientatie;
		gwsw:hasAspect [a gwsw:Punt;
			gwsw:hasValue "<gml:Point xmlns:gml=\"http://www.opengis.net/gml\"><gml:pos>163035.93 383176.51 </gml:pos></gml:Point>"^^geo:gmlLiteral ] ],
		[a gwsw:Dekselorientatie;
			gwsw:hasAspect [a gwsw:Putdekselniveau;
				gwsw:hasValue "15.3"^^xsd:decimal]].
ex:Lei_15 rdfs:label "001";
    a gwsw:Rioolleiding;
    gwsw:isPartOf ex:Stl_5;
    gwsw:hasAspect [a gwsw:BreedteLeiding;
		gwsw:hasValue "300"^^xsd:integer],
	[a gwsw:HoogteLeiding;
		gwsw:hasValue "300"^^xsd:integer],
	[a gwsw:MateriaalLeiding;
		gwsw:hasReference gwsw:Beton],
	[a gwsw:VormLeiding;
	    gwsw:hasReference gwsw:Rond],
	[a gwsw:Leidingorientatie; 
		gwsw:hasAspect [a gwsw:Lijn;
			gwsw:hasValue "<gml:LineString xmlns:gml=\"http://www.opengis.net/gml\"><gml:posList srsDimension=2>163042.58 383220.11 163035.93 383176.51</gml:posList></gml:LineString>"];
		gwsw:hasPart ex:LeiOriB_18, ex:LeiOriE_19].
ex:LeiOriB_18 a gwsw:BeginpuntLeiding;
    gwsw:hasConnection ex:KnpOri_3;
    gwsw:hasAspect [a gwsw:BobBeginpuntLeiding;
		gwsw:hasValue "16.43"^^xsd:decimal].
ex:LeiOriE_19 a gwsw:EindpuntLeiding;
    gwsw:hasConnection ex:KnpOri_7;
    gwsw:hasAspect [a gwsw:BobEindpuntLeiding;
		gwsw:hasValue "16.56"^^xsd:decimal].
ex:InmLei_16 a gwsw:InmetenLeiding;
    gwsw:isPartOf ex:Proj_1;
    gwsw:hasInput ex:Lei_15;
	gwsw:hasAspect [ a gwsw:DatumInwinning;
		gwsw:hasValue "2026-01-15"^^xsd:date];
    gwsw:hasAspect _:b1000_85;
    gwsw:hasOutput ex:Lei_39.
ex:Knp_20 rdfs:label "K0001";
    a gwsw:Inspectieput;
    gwsw:hasAspect [a gwsw:Putorientatie;
		gwsw:hasAspect [a gwsw:Punt;
			gwsw:hasValue "<gml:Point xmlns:gml=\"http://www.opengis.net/gml\"><gml:pos>163042.42 383220.109 </gml:pos></gml:Point>"^^geo:gmlLiteral] ],
    [a gwsw:BreedtePut;
		gwsw:hasValue "800"^^xsd:integer],
	[a gwsw:LengtePut;
		gwsw:hasValue "800"^^xsd:integer],
	[a gwsw:HoogtePut;
		gwsw:hasValue "1150"^^xsd:integer],	
	[a gwsw:VormPut;
		gwsw:hasReference gwsw:Rechthoekig;
		gwsw:hasAspect [a gwsw:Inwinning;
			gwsw:hasAspect [a gwsw:WijzeVanInwinning;
				gwsw:hasReference gwsw:Inmeting], [a gwsw:DatumInwinning;
					gwsw:hasValue "2026-01-01"^^xsd:date] ]
		],
	[a gwsw:MateriaalPut;
		gwsw:hasReference gwsw:Beton],
	[a gwsw:Bodemprofiel;
		gwsw:hasReference gwsw:VlakkeBodemBanken],
	[a gwsw:StatusFunctioneren;
    gwsw:hasReference gwsw:InGebruik];
	gwsw:isPartOf ex:Stl_22;
    gwsw:hasPart [a gwsw:Stellaag;
		gwsw:hasAspect [a gwsw:HoogteStellaag;
			gwsw:hasValue "210"^^xsd:integer] ].
ex:Stl_22 rdfs:label "Centrum hoofd";
    a gwsw:GemengdStelsel.
ex:Knp_24 rdfs:label "K0002";
    a gwsw:ExterneOverstortput;
    gwsw:hasAspect [a gwsw:Putorientatie;
		gwsw:hasAspect [a gwsw:Punt;
    gwsw:hasValue "<gml:Point xmlns:gml=\"http://www.opengis.net/gml\"><gml:pos>163035.89 383176.6 </gml:pos></gml:Point>"^^geo:gmlLiteral] ],
	[a gwsw:BreedtePut;
		gwsw:hasValue "1600"^^xsd:integer],
	[a gwsw:LengtePut;
		gwsw:hasValue "1600"^^xsd:integer],
	[a gwsw:HoogtePut;
		gwsw:hasValue "1300"^^xsd:integer],
	[a gwsw:VormPut;
		gwsw:hasAspect [a gwsw:Inwinning;
			gwsw:hasAspect [a gwsw:WijzeVanInwinning;
				gwsw:hasReference gwsw:Inmeting], 
			[a gwsw:DatumInwinning;
				gwsw:hasValue "2026-01-01"^^xsd:date] ];
		gwsw:hasReference gwsw:Rechthoekig],
	[a gwsw:MateriaalPut;
		gwsw:hasReference gwsw:Beton],
	[a gwsw:Bodemprofiel;
		gwsw:hasReference gwsw:VlakkeBodem],
	[a gwsw:StatusFunctioneren;
		gwsw:hasReference gwsw:InGebruik];
    gwsw:isPartOf ex:Stl_22;
    gwsw:hasPart [a gwsw:Wand;
		gwsw:hasAspect _:b1000_54, _:b1000_57], 
		[a gwsw:Wand;
			gwsw:hasAspect _:b1000_61, _:b1000_64], 
		[a gwsw:Stellaag;
			gwsw:hasAspect [a gwsw:HoogteStellaag;
				gwsw:hasValue "100"^^xsd:integer] ].
_:b1000_54 a gwsw:Drempelbreedte;
    gwsw:hasAspect [a gwsw:Inwinning;
		gwsw:hasAspect [a gwsw:WijzeVanInwinning;
			gwsw:hasReference gwsw:Inmeting], 
		[a gwsw:DatumInwinning;
			gwsw:hasValue "2026-01-01"^^xsd:date]] ;
    gwsw:hasValue "1200"^^xsd:integer.
_:b1000_57 a gwsw:Drempelniveau;
    gwsw:hasAspect [a gwsw:Inwinning;
		gwsw:hasAspect [a gwsw:WijzeVanInwinning;
			gwsw:hasReference gwsw:GPSLandmeting], 
		[a gwsw:DatumInwinning;
			gwsw:hasValue "2026-01-01"^^xsd:date] ];
    gwsw:hasValue "14.51"^^xsd:decimal.
_:b1000_61 a gwsw:Drempelbreedte;
    gwsw:hasAspect [a gwsw:Inwinning;
		gwsw:hasAspect [a gwsw:WijzeVanInwinning;
			gwsw:hasReference gwsw:Inmeting], 
		[a gwsw:DatumInwinning;
			gwsw:hasValue "2026-01-01"^^xsd:date] ];
    gwsw:hasValue "800"^^xsd:integer.
_:b1000_64 a gwsw:Drempelniveau;
    gwsw:hasAspect [a gwsw:Inwinning;
		gwsw:hasAspect [a gwsw:WijzeVanInwinning;
			gwsw:hasReference gwsw:GPSLandmeting], 
		[a gwsw:DatumInwinning;
			gwsw:hasValue "2026-01-01"^^xsd:date] ];
    gwsw:hasValue "14.62"^^xsd:decimal.
ex:Dks_31 a gwsw:Deksel;
    gwsw:isPartOf ex:Knp_20;
    gwsw:hasAspect [a gwsw:BreedteDeksel;
		gwsw:hasValue "520"^^xsd:integer],
	[a gwsw:LengteDeksel;
		gwsw:hasValue "520"^^xsd:integer],
	[a gwsw:VormDeksel;
		gwsw:hasReference gwsw:Rond],
	[a gwsw:MateriaalDeksel;
		gwsw:hasReference gwsw:Gietijzer],
	[a gwsw:Dekselorientatie;
		gwsw:hasAspect [a gwsw:Punt;
			gwsw:hasValue "<gml:Point xmlns:gml=\"http://www.opengis.net/gml\"><gml:pos>163042.42 383220.109 </gml:pos></gml:Point>"^^geo:gmlLiteral] ],
	[a gwsw:Dekselorientatie;
		gwsw:hasAspect [a gwsw:Putdekselniveau;
			gwsw:hasValue "15.3"^^xsd:decimal;
			gwsw:hasAspect ex:Inwinn_34 ] ].	
ex:Inwinn_34 a gwsw:Inwinning;
    gwsw:hasAspect [a gwsw:WijzeVanInwinning;
		gwsw:hasReference gwsw:GPSLandmeting], 
	[a gwsw:DatumInwinning;
		gwsw:hasValue "2026-01-01"^^xsd:date].
ex:Dks_35 a gwsw:Putdeksel_ZwaarVerkeer;
    gwsw:isPartOf ex:Knp_24;
    gwsw:hasAspect [a gwsw:BreedteDeksel;
		gwsw:hasValue "600"^^xsd:integer],
	[a gwsw:LengteDeksel;
		gwsw:hasValue "600"^^xsd:integer],
	[a gwsw:VormDeksel;
		gwsw:hasReference gwsw:Rond],
	[a gwsw:MateriaalDeksel;
		gwsw:hasReference gwsw:Gietijzer],
	[a gwsw:Dekselorientatie;
		gwsw:hasAspect [a gwsw:Punt;
			gwsw:hasValue "<gml:Point xmlns:gml=\"http://www.opengis.net/gml\"><gml:pos>163035.89 383176.6 </gml:pos></gml:Point>"^^geo:gmlLiteral] ],
	[a gwsw:Dekselorientatie;
		gwsw:hasAspect [a gwsw:Putdekselniveau;
			gwsw:hasAspect [a gwsw:Inwinning;
				gwsw:hasAspect _:b1000_83, _:b1000_84];
			gwsw:hasValue "15.31"^^xsd:decimal] ].
_:b1000_83 a gwsw:WijzeVanInwinning;
    gwsw:hasReference gwsw:GPSLandmeting.
_:b1000_84 a gwsw:DatumInwinning;
    gwsw:hasValue "2026-01-01"^^xsd:date.
ex:Lei_39 rdfs:label "001";
    a gwsw:GemengdRiool;
    gwsw:isPartOf ex:Stl_22;
    gwsw:hasAspect [a gwsw:BreedteLeiding;
		gwsw:hasAspect [a gwsw:Inwinning;
			gwsw:hasAspect [a gwsw:WijzeVanInwinning;
				gwsw:hasReference gwsw:Inmeting], 
			[a gwsw:DatumInwinning;
				gwsw:hasValue "2026-06-15"^^xsd:date] ];
		gwsw:hasValue "300"^^xsd:integer ],
	[a gwsw:HoogteLeiding;
		gwsw:hasAspect [a gwsw:Inwinning;
			gwsw:hasAspect [a gwsw:WijzeVanInwinning;
				gwsw:hasReference gwsw:Inmeting], 
			[a gwsw:DatumInwinning;
				gwsw:hasValue "2026-06-15"^^xsd:date] ];
		gwsw:hasValue "300"^^xsd:integer],
	[a gwsw:StatusFunctioneren;
		gwsw:hasReference gwsw:InGebruik],
	[a gwsw:VormLeiding;
		gwsw:hasAspect [a gwsw:Inwinning;
			gwsw:hasAspect [a gwsw:WijzeVanInwinning;
				gwsw:hasReference gwsw:Inmeting], 
			[a gwsw:DatumInwinning;
				gwsw:hasValue "2026-06-15"^^xsd:date]];
		gwsw:hasReference gwsw:Rond],
	[a gwsw:MateriaalLeiding;
		gwsw:hasAspect [a gwsw:Inwinning;
			gwsw:hasAspect [a gwsw:WijzeVanInwinning;
				gwsw:hasReference gwsw:Inmeting], 
			[a gwsw:DatumInwinning;
				gwsw:hasValue "2026-06-15"^^xsd:date] ];
		gwsw:hasReference gwsw:Beton],
	[a gwsw:Leidingorientatie;
		gwsw:hasPart [a gwsw:BeginpuntLeiding;
			gwsw:hasConnection ex:KnpOri_21;
			gwsw:hasAspect _:b1000_99, _:b1000_102], 
		[a gwsw:EindpuntLeiding;
			gwsw:hasConnection ex:KnpOri_25;
			gwsw:hasAspect _:b1000_103, _:b1000_106];
		gwsw:hasAspect [a gwsw:Lijn;
			gwsw:hasValue "<gml:LineString xmlns:gml=\"http://www.opengis.net/gml\"><gml:posList srsDimension=2>163042.42 383220.109 163035.89 383176.6</gml:posList></gml:LineString>"] ].
_:b1000_99 a gwsw:BobBeginpuntLeiding;
    gwsw:hasAspect [a gwsw:Inwinning;
		gwsw:hasAspect [a gwsw:WijzeVanInwinning;
			gwsw:hasReference gwsw:Inmeting], 
		[a gwsw:DatumInwinning;
			gwsw:hasValue "2026-06-15"^^xsd:date] ];
    gwsw:hasValue "16.12"^^xsd:decimal.
_:b1000_102 a gwsw:BbbBeginpuntLeiding;
    gwsw:hasValue "16.42"^^xsd:decimal.
_:b1000_103 a gwsw:BobEindpuntLeiding;
    gwsw:hasAspect [a gwsw:Inwinning;
		gwsw:hasAspect [a gwsw:WijzeVanInwinning;
			gwsw:hasReference gwsw:Inmeting], 
		[a gwsw:DatumInwinning;
			gwsw:hasValue "2026-06-15"^^xsd:date] ];
    gwsw:hasValue "16.27"^^xsd:decimal.
_:b1000_106 a gwsw:BbbEindpuntLeiding;
    gwsw:hasValue "16.57"^^xsd:decimal.
</pre></div>

## JSON Uitwisselbestand
**Voorbeeld bestand heen.json**  
<div class="box"><pre>
{
  "Project": [
    {
      "Bestandstype": "Revisie heen",
	  "Versie": "0.1",
      "Naam": "Inmeten alles",
      "Opdrachtgever": "Gemeente Juinen",
      "Opdrachtnemer": "Hekking Meetadvies B.V.",
      "ProjectreferentieOpdrachtgever": "OPD12345",
      "ProjectreferentieOpdrachtnemer": "AAN67890",
      "Omschrijving": "Inmeting klein Juinen",
      "Contactpersoon": "Walter de Rochebrune"
    }
  ],
  "Deksel": [
    {
      "Naam": "K0001",
      "X": 163042.580,
      "Y": 383220.110,
      "Z": 15.28
    },
    {
      "Naam": "K0002",
      "X": 163035.930,
      "Y": 383176.510,
      "Z": 15.30
    }
  ],
  "Knooppunt": [
    {
      "Naam": "K0001",
	  "X": 163042.580,
      "Y": 383220.110,
      "Type": "Inspectieput",
      "NaamStelsel": "Centrum hoofd",
      "TypeStelsel": "Gemengd stelsel",
      "Vorm": "Rechthoekig",
      "Breedte": 800,
      "Lengte": 800,
      "Materiaal": "Beton"
    },
    {
      "Naam": "K0002",
	  "X": 163035.930,
      "Y": 383176.510,
      "Type": "Externe overstortput",
      "NaamStelsel": "Centrum hoofd",
      "TypeStelsel": "Gemengd stelsel",
      "Vorm": "Rechthoekig",
      "Materiaal": "Beton"
    }
  ],
  "Leiding": [
    {
      "Naam": "001",
      "Type": "Rioolleiding",
      "NaamStelsel": "Centrum hoofd",
      "TypeStelsel": "Gemengd stelsel",
      "NaamKnooppuntBegin": "K0001",
      "NaamKnooppuntEind": "K0002",
      "BobKnooppuntBegin": 16.43,
      "BobKnooppuntEind": 16.56,
      "Vorm": "Rond",
      "Hoogte": 300,
      "Breedte": 300,
      "Materiaal": "Beton"
    }
  ]
}
</pre></div>

**Voorbeeld bestand terug.json**  
<div class="box"><pre>
{
  "Project": [
    {
      "Bestandstype": "Revisie terug",
	  "Versie": "0.1",
      "Naam": "Inmeten alles",
      "Opdrachtgever": "Gemeente Juinen",
      "Opdrachtnemer": "Hekking Meetadvies B.V.",
      "ProjectreferentieOpdrachtgever": "OPD12345",
      "ProjectreferentieOpdrachtnemer": "AAN67890",
      "Omschrijving": "Inmeting klein Juinen",
      "Contactpersoon": "Walter de Rochebrune",
	  "WijzeVanInwinningKnooppunt": "Inmeting",
	  "WijzeVanInwinningDeksel": "GNSS Vanuit wagen",
	  "WijzeVanInwinningLeiding": "Inmeting",
	  "WijzeVanInwinningXY":"GNSS Landmeting",
	  "WijzeVanInwinningZ": "GNSS Landmeting"
    }
  ],
  "Deksel": [
    {
      "Naam": "K0001",
	  "DatumInwinning": "2026-01-01",
      "X": 163042.420,
      "Y": 383220.109,
      "Z": 15.30,
      "Type": "Deksel",
      "Vorm": "Rond",
      "Lengte": 520,
      "Breedte": 520,
      "Materiaal": "Gietijzer",
      "Melding": [ "Deksel gebroken", "Deksel boven maaiveld" ]
    },
    {
      "Naam": "K0002",
	  "DatumInwinning": "2026-01-01",
      "X": 163035.890,
      "Y": 383176.600,
      "Z": 15.31,
      "Type": "Putdeksel - zwaar verkeer",
      "Vorm": "Rond",
      "Lengte": 600,
      "Breedte": 600,
      "Materiaal": "Gietijzer",
	  "Opmerking": "Mooie deksel"
    }
  ],
  "Knooppunt": [
    {
      "Naam": "K0001",
      "Type": "Inspectieput",
      "NaamStelsel": "Centrum hoofd",
      "TypeStelsel": "Gemengd stelsel",
      "DatumInwinning": "2026-01-01",
      "Vorm": "Rechthoekig",
      "Breedte": 800,
      "Lengte": 800,
      "Materiaal": "Beton",
      "Bodemprofiel": "Vlakke bodem met banken",
	  "X": 163042.420,
      "Y": 383220.109,
      "Z": 14.15,
      "Hoogte": 1150,
      "StatusFunctioneren": "In gebruik",
      "Constructieonderdeel": [ "Afdekking", "Stellaag" ],
      "HoogteStellaag": 210,
      "Waterstand": 0.15,
      "Fotoreferentie": [ "Foto001.jpg","Foto002.jpg" ],
      "Melding": [ "Oppervlakteschade in object", "Vuil in object" ]
    },
    {
      "Naam": "K0002",
      "Type": "Externe overstortput",
      "NaamStelsel": "Centrum hoofd",
      "TypeStelsel": "Gemengd stelsel",
      "DatumInwinning": "2026-01-01",
      "Vorm": "Rechthoekig",
      "Breedte": 1600,
      "Lengte": 1600,
      "Materiaal": "Beton",
      "Bodemprofiel": "Vlakke bodem",
      "X": 163035.890,
      "Y": 383176.600,
      "Z": 14.01,
      "Hoogte": 1300,
      "StatusFunctioneren": "In gebruik",
      "Constructieonderdeel": [ "Afdekking", "Stellaag", "Overstortdrempel" ],
	  "Drempelniveau": [14.51, 14.62],
	  "Drempelbreedte": [1200, 800],
      "HoogteStellaag": 100,
      "Waterstand": 0.1,
      "Fotoreferentie": [ "Foto003.jpg", "Foto004.jpg" ],
	  "Melding": [ "Object ontbreekt in opdracht","Object toegevoegd","Scheur in object" ],
	  "Opmerking": "Prima overstort"
    }
  ],
  "Leiding": [
    {
      "Naam": "001",
      "Type": "Gemengd riool",
      "NaamStelsel": "Centrum hoofd",
      "TypeStelsel": "Gemengd stelsel",
	  "DatumInwinning": "2026-06-15",
      "NaamKnooppuntBegin": "K0001",
      "NaamKnooppuntEind": "K0002",
      "BobKnooppuntBegin": 16.12,
      "BobKnooppuntEind": 16.27,
      "BbbKnooppuntBegin": 16.42,
      "BbbKnooppuntEind": 16.57,
      "StatusFunctioneren": "In gebruik",
      "Vorm": "Rond",
      "Hoogte": 300,
      "Breedte": 300,
      "Materiaal": "Beton",
      "Fotoreferentie": [ "Foto004.jpg", "Foto005.jpg" ],
	  "Melding": [ "Grond in object","Object toegevoegd","Ongedierte in object" ],
      "Opmerking": "Dit is een opmerking"
    }
  ]
}
</pre></div>