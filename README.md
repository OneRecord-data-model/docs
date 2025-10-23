Notes:




**OneRecord ontologia**
*  liiketoimintaan/toimitusketjuun liittyvät osapuolet (organisaatiot)
*  liiketoiminta-asiakirjojen (sanomien) sisällön (katalogi, tilaus, toimitus, logistiikka sanomat) udelleen käytettävä tieto (OneRecord excelin esittäminen graafina)
  * lähettäjä
  * vastaanottaja

  * luokkakaavio OWL-muodossa
  * --> Drawio muodossa esitetty

<img width="691" height="467" alt="Näyttökuva 2025-10-22 090556" src="https://github.com/user-attachments/assets/48e6a02d-b78f-4993-bd4c-ff89f4e19f2f" />


# 1. OneRecord for the construction industry

What is OneRecord?
A shared vision for interoperable data exchange in construction supply chains

🌍 Background

Construction industry data flows are still fragmented across organizations, systems, and project boundaries. Each actor maintains its own ERP, TMS, CRM, and financial systems, resulting in multiple overlapping document formats and limited interoperability.

Although Peppol BIS / UBL 2.4 enables standardized document exchange (eOrders, eInvoices, etc.), in practice every implementation interprets data elements differently.

OneRecord for Construction proposes a system-level solution: A harmonized, traceable, and semantically unified data model built on top of Peppol/UBL, designed specifically for construction supply chains.

🧩 What is OneRecord?

OneRecord connects all Peppol/UBL-based business documents into a single interoperable dataset, a digital “thread” of the supply chain linking design, procurement, logistics, and finance.

From fragmented documents → to an interconnected record of transactions and product data.

Each document (Order, Despatch Advice, Invoice, etc.) contributes new and reused data. By identifying which document originally created a data element and where it is reused, we can remove duplicates and enable consistent traceability across systems and organizations.

📘 Conceptual Model

Concept	Description
cbc (Basic)	Individual data leaf that carries a unique value and meaning.
cac (Aggregate)	Logical branch grouping related basic data elements.
OneRecord	The unified data model combining all documents and processes.
ERP → Peppol Document → OneRecord → Interoperability Platform

Each cbc element has

a unique definition and content

a known origin (sender–receiver process)

a reuse rule (which later documents inherit the same data)

Document	Sender	Receiver	Data	Reuse in
Order	Buyer	Seller	Item ID, Price, Delivery Date	Invoice, Despatch
Despatch Advice	Seller	Buyer	Package, Weight	Transport Status
Invoice	Seller	Buyer	Total, OrderRef	Finance, Reporting
🔗 Data and Process Integration

OneRecord enables systematic linkage between

eProcurement: Order, Order Response, Catalogue, Invoice

eLogistics: Despatch Advice, Transport Plan, Waybill, IoT weight data

Regulatory Data: eFTI, Customs, Environmental reporting

Product Data: DPP (Digital Product Passport), EPD (Environmental Product Declaration)

Each record connects business, product, and process data through shared identifiers (ItemID, ProjectID, OrderRef, etc.) and links to external sources such as catalogue providers (CPC) or classification systems.

💡 Why OneRecord?

Challenge	OneRecord Solution
Fragmented data ownership	Shared, traceable data model across actors
Duplicate information	Unique element definitions with reuse mapping
Difficult ERP–Peppol mapping	Common cbc-based reference content
Limited visibility	End-to-end digital record from order to delivery
Slow connector development	Faster, standardized integration points
⚙️ Technical Vision

Built on UBL 2.4 and Peppol BIS (no new standard needed)

Extensible for industry-specific requirements (construction, prefabrication, logistics)

Interoperable across Web2 (ERP–ERP) and Web3 (DLT-based) environments

Ledger-ready enabling verified storage and smart contracts for future decentralized use cases

Peppol Web2 stores messages in ERP backends. Peppol Web3 stores verified messages in decentralized ledgers (“wallets”). OneRecord ensures that both use the same data semantics.

🧭 Roadmap

Define OneRecord mapping between UBL 2.4 documents (Excel/JSON schema)

Publish localized Peppol BIS extensions for construction use cases (FI/SE/NO)

Demonstrate ERP–Peppol mapping examples for procurement and logistics

Pilot interoperability platform with OneRecord-based traceability

Prepare Web3 integration for DLT-enabled data sharing and apps ecosystem

2025-10-21_Kuva3
Kuva havainnollistaa UBL (Universal Business Language) -rakenteeseen perustuvan OneRecord-ajattelun rakennetta vertauskuvallisesti metsän avulla. Selitetään sen keskeiset osat vaiheittain:

🌲 1. Metsä = koko tietokokonaisuus

Vasemmalla näkyy Forest (Metsä), joka koostuu monista Documents (asiakirjoista).

Jokainen puu (dokumentti) edustaa yhtä liiketoimintasanomaa, kuten tilaus (Order), toimitusilmoitus (DespatchAdvice) tai lasku (Invoice).

📄 2. Dokumentti = puu

Yksi puu vastaa yhtä OneRecord-rakennetta eli yksittäistä dokumenttia.

Puun rakenne kuvaa tietohierarkiaa:

Runko ja oksat (branch) = tietorakenteen aggregaattielementtejä (cac)

Lehdet = perusarvoja (cbc) kuten nimi, osoite, tunniste jne.

🌿 3. Rakenteen logiikka

"Aggregate = branch = cac" tarkoittaa, että cac (Common Aggregate Component) on UBL:n rakenneosa, joka koostuu muista elementeistä. → Se on kuin oksa, joka sisältää pienempiä oksia ja lopulta lehtiä.

"Basic = leaves = cbc" tarkoittaa, että cbc (Common Basic Component) on yksittäinen arvo eli “lehti” tietopuussa. → Esimerkiksi cbc:Name, cbc:StreetName, cbc:PostalZone ovat arvoja, eivät rakenteita.

🧩 4. Esimerkki keskellä olevasta taulukosta

Kuvassa näkyvä rakenne on esimerkiksi osa UBL-asiakirjaa, kuten:

cac:BuyerCustomerParty cac:Party cbc:EndpointID cac:PartyIdentification cbc:ID cac:PartyName cbc:Name cac:PostalAddress cbc:StreetName cbc:CityName cbc:PostalZone cbc:Country

Jokainen cac:-rivi on “oksa” (rakenne), ja jokainen cbc:-rivi on “lehti” (perusarvo).

🧾 5. OneRecord

OneRecord on käsite, jossa yksi standardoitu tietue sisältää kaikki kyseisen dokumentin olennaiset tiedot yhdenmukaisessa muodossa.

Ajatuksena on, että kaikki dokumentit (puut) muodostavat datan metsän, mutta jokainen yksittäinen dokumentti noudattaa samaa loogista UBL-puurakennetta.

🔢 6. “Unic Value?”

Oikealla oleva sininen laatikko viittaa kysymykseen uniikista arvosta – esimerkiksi yksilöllisestä tunnisteesta (cbc:ID), jolla tietue voidaan erottaa muista.

Tämä on tärkeä, kun dokumentteja linkitetään toisiinsa (esim. tilaus–toimitus–lasku).

🧠 Yhteenveto Vertaus UBL-termi Selitys Metsä Dokumenttijoukko Kaikki UBL-dokumentit (esim. Order, Invoice) Puu Dokumentti Yksittäinen liiketoimintasanoma Oksa cac: Rakenne- eli aggregaattielementti Lehti cbc: Perusarvo, kuten nimi tai osoite Uniikki arvo cbc:ID tms. Dokumentin tai osan yksilöivä tunniste

# 2. OneRecord use case story

**Use Case Example:** Ontology-Based Transaction Data Exchange in the Construction Industry

**Objective:**
To enable interoperable and reusable transaction data exchange between the parties of a construction project by utilizing the Peppol network and an ontology-based data model.

**Actors:**
Sender – Receiver (e.g., Construction product supplier / contractor, Construction product supplier / manufacturer).

**Use Case:**
As a construction product supplier, I want to send and receive standardized electronic business documents (e.g., order, despatch advice, receipt acknowledgment, logistics messages) through the Peppol network so that a shared ontology ensures data consistency and previously generated data can be reused in later stages of the process (design – manufacturing – delivery – installation).


$\color{blue}{\textsf{Same same in Finnish}}$ :finland:


**Käyttötapausesimerkki:** Ontologiaan perustuva transaktiotiedonvaihto rakennusalalla

**Tavoite:**
Mahdollistaa yhteentoimiva ja uudelleenkäytettävä transaktiotiedonvaihto rakennusprojektin osapuolten välillä hyödyntämällä Peppol-verkkoa ja ontologiaan perustuvaa tietomallia.

**Toimija:**
Lähettäjä - vastaanottaja (esim. Rakennustuotetoimittaja/urakoitsija, Rakennustuotetoimittaja/tuotevalmistaja).

**Käyttötapaus:**
Rakennustuotetoimittajana haluan lähettää ja vastaanottaa standardoituja sähköisiä liiketoimintasanomia (esim. tilaus, lähetysilmoitus, vastaanottokuittaus, logistiikkasanomat) Peppol-verkon kautta siten, että yhteinen ontologia varmistaa tietojen yhdenmukaisuuden ja aiemmin luotua dataa voidaan hyödyntää prosessin myöhemmissä vaiheissa (suunnittelu–valmistus–toimitus–asennus).

---

# 3. OneRecord ontology

Intro

The interoperability of information from design to operations is a well-recognized challenge in the architecture, engineering, and construction (AEC) industry. As a potential solution to these interoperability issues, there has been growing interest in applying linked data and semantic web technologies to establish an extensible data model. Although several semantic web ontologies have been developed for the AEC domain, a comprehensive ontology for representing the reusable, generated, and enriched transaction information throughout supply chain processes is still lacking.

The Peppol network provides an international communication infrastructure that enables organizations to exchange electronic business documents securely and efficiently. In the Nordic countries, e-invoices are currently the most widely used standardized electronic business documents within the AEC sector. However, similar developments are now emerging for other types of electronic business documents, such as catalogues, orders, delivery information exchanges, and receipt responses.

---

So far, we have two candidate ontology representations.

**1. Interoperability platform**
[Finnish Construction Industry One Record](https://tietomallit.suomi.fi/model/fcior?ver=0.0.1)




<br>

**2. Concept draft of OneRecord ontology**

![WhatsApp-Kuva 2025-10-22 klo 17 19 27_e4c49276](https://github.com/user-attachments/assets/73b67127-799c-4c3e-a4a5-92f9ed1cdf29)




| Aspect                               | FCIOR Model                                                                                                                                              | The Proposed Model                                                                                                                                                              |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Document coverage**                | The FCIOR model covers the *Catalogue → Order → Despatch Advice → Invoice* document chain, following the UBL 2.4 structure.                              | The proposed model extends this scope by covering the *Order → OrderRespond → OrderFinance → Invoice* chain and additionally includes *TransportOrder* and *Delivery* elements. |
| **Concepts**                         | The model primarily employs UBL-type concepts such as *Order*, *Despatch*, and *Invoice*.                                                                | The proposed model introduces AEC- and supply chain–specific concepts, including *Transport*, *PricedItem*, *Total*, and *OrderFinance*.                                        |
| **Relationships**                    | Relationships are not explicitly represented as a graph but are based on UBL’s semantic relations (e.g., *OrderLine*, *SupplierParty*, *DeliveryTerms*). | The proposed model defines explicit RDF-type relationships such as `one:hasOrder`, `one:hasDelivery`, `one:hasPrice`, and `one:hasTotal`.                                       |
| **Transactional and financial data** | Financial elements such as *Price*, *Tax*, and *Amount* are embedded within UBL document structures.                                                     | In contrast, the proposed model introduces a distinct financial layer (`OrderFinance`, `Total`, `Price`) that links both *Order* and *Transport* levels.                        |
| **Transport information**            | The FCIOR model includes references to *Despatch Advice* and *Transport Handling Unit* but lacks a separate *TransportOrder* structure.                  | The proposed model explicitly defines *TransportOrder*, *TransportItem*, and *Transport* classes, each containing dedicated *hasTotal* and *hasPrice* properties.               |
| **Ontological extensibility**        | The FCIOR model aims to integrate existing UBL documents into a unified semantic framework.                                                              | The proposed model represents an ontologically extensible framework that connects business documents (Peppol) with supply chain transaction data.                               |

