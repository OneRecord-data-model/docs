# OneRecord for Construction Industry

## What is OneRecord?

A shared vision for interoperable data exchange in construction supply chains

🌍 Background

Construction industry data flows are still fragmented across organizations, systems, and project boundaries.
Each actor maintains its own ERP, TMS, CRM, and financial systems, resulting in multiple overlapping document formats and limited interoperability.

Although Peppol BIS / UBL 2.4 enables standardized document exchange (eOrders, eInvoices, etc.),
in practice every implementation interprets data elements differently.

OneRecord for Construction proposes a system-level solution:
A harmonized, traceable, and semantically unified data model built on top of Peppol/UBL, designed specifically for construction supply chains.

🧩 What is OneRecord?

OneRecord connects all Peppol/UBL-based business documents into a single interoperable dataset,
a digital “thread” of the supply chain linking design, procurement, logistics, and finance.

From fragmented documents → to an interconnected record of transactions and product data.

Each document (Order, Despatch Advice, Invoice, etc.) contributes new and reused data.
By identifying which document originally created a data element and where it is reused,
we can remove duplicates and enable consistent traceability across systems and organizations.

📘 Conceptual Model
| Concept             | Description                                                   |
| ------------------- | ------------------------------------------------------------- |
| **cbc (Basic)**     | Individual data leaf that carries a unique value and meaning. |
| **cac (Aggregate)** | Logical branch grouping related basic data elements.          |
| **OneRecord**       | The unified data model combining all documents and processes. |


ERP → Peppol Document → OneRecord → Interoperability Platform



Each cbc element has

a unique definition and content

a known origin (sender–receiver process)

a reuse rule (which later documents inherit the same data)

| Document        | Sender | Receiver | Data                          | Reuse in           |
| --------------- | ------ | -------- | ----------------------------- | ------------------ |
| Order           | Buyer  | Seller   | Item ID, Price, Delivery Date | Invoice, Despatch  |
| Despatch Advice | Seller | Buyer    | Package, Weight               | Transport Status   |
| Invoice         | Seller | Buyer    | Total, OrderRef               | Finance, Reporting |

🔗 Data and Process Integration

OneRecord enables systematic linkage between

eProcurement: Order, Order Response, Catalogue, Invoice

eLogistics: Despatch Advice, Transport Plan, Waybill, IoT weight data

Regulatory Data: eFTI, Customs, Environmental reporting

Product Data: DPP (Digital Product Passport), EPD (Environmental Product Declaration)

Each record connects business, product, and process data through shared identifiers (ItemID, ProjectID, OrderRef, etc.)
and links to external sources such as catalogue providers (CPC) or classification systems.

💡 Why OneRecord?
| Challenge                    | OneRecord Solution                               |
| ---------------------------- | ------------------------------------------------ |
| Fragmented data ownership    | Shared, traceable data model across actors       |
| Duplicate information        | Unique element definitions with reuse mapping    |
| Difficult ERP–Peppol mapping | Common cbc-based reference content               |
| Limited visibility           | End-to-end digital record from order to delivery |
| Slow connector development   | Faster, standardized integration points          |

⚙️ Technical Vision

Built on UBL 2.4 and Peppol BIS (no new standard needed)

Extensible for industry-specific requirements (construction, prefabrication, logistics)

Interoperable across Web2 (ERP–ERP) and Web3 (DLT-based) environments

Ledger-ready enabling verified storage and smart contracts for future decentralized use cases

Peppol Web2 stores messages in ERP backends.
Peppol Web3 stores verified messages in decentralized ledgers (“wallets”).
OneRecord ensures that both use the same data semantics.

🧭 Roadmap

Define OneRecord mapping between UBL 2.4 documents (Excel/JSON schema)

Publish localized Peppol BIS extensions for construction use cases (FI/SE/NO)

Demonstrate ERP–Peppol mapping examples for procurement and logistics

Pilot interoperability platform with OneRecord-based traceability

Prepare Web3 integration for DLT-enabled data sharing and apps ecosystem

<img width="1972" height="1653" alt="2025-10-21_Kuva2" src="https://github.com/user-attachments/assets/6f9f4711-09a9-4e4f-8157-fc66ce87fcc0" />

<img width="1972" height="1653" alt="2025-10-21_Kuva2" src="https://github.com/user-attachments/assets/ddd0e69f-0d4c-47a6-8a4c-f0bf2ff75e6d" />


Kuva havainnollistaa UBL (Universal Business Language) -rakenteeseen perustuvan OneRecord-ajattelun rakennetta vertauskuvallisesti metsän avulla.
Selitetään sen keskeiset osat vaiheittain:

🌲 1. Metsä = koko tietokokonaisuus

Vasemmalla näkyy Forest (Metsä), joka koostuu monista Documents (asiakirjoista).

Jokainen puu (dokumentti) edustaa yhtä liiketoimintasanomaa, kuten tilaus (Order), toimitusilmoitus (DespatchAdvice) tai lasku (Invoice).

📄 2. Dokumentti = puu

Yksi puu vastaa yhtä OneRecord-rakennetta eli yksittäistä dokumenttia.

Puun rakenne kuvaa tietohierarkiaa:

Runko ja oksat (branch) = tietorakenteen aggregaattielementtejä (cac)

Lehdet = perusarvoja (cbc) kuten nimi, osoite, tunniste jne.

🌿 3. Rakenteen logiikka

"Aggregate = branch = cac" tarkoittaa, että cac (Common Aggregate Component) on UBL:n rakenneosa, joka koostuu muista elementeistä.
→ Se on kuin oksa, joka sisältää pienempiä oksia ja lopulta lehtiä.

"Basic = leaves = cbc" tarkoittaa, että cbc (Common Basic Component) on yksittäinen arvo eli “lehti” tietopuussa.
→ Esimerkiksi cbc:Name, cbc:StreetName, cbc:PostalZone ovat arvoja, eivät rakenteita.

🧩 4. Esimerkki keskellä olevasta taulukosta

Kuvassa näkyvä rakenne on esimerkiksi osa UBL-asiakirjaa, kuten:

cac:BuyerCustomerParty
    cac:Party
        cbc:EndpointID
        cac:PartyIdentification
            cbc:ID
        cac:PartyName
            cbc:Name
        cac:PostalAddress
            cbc:StreetName
            cbc:CityName
            cbc:PostalZone
            cbc:Country


Jokainen cac:-rivi on “oksa” (rakenne),
ja jokainen cbc:-rivi on “lehti” (perusarvo).

🧾 5. OneRecord

OneRecord on käsite, jossa yksi standardoitu tietue sisältää kaikki kyseisen dokumentin olennaiset tiedot yhdenmukaisessa muodossa.

Ajatuksena on, että kaikki dokumentit (puut) muodostavat datan metsän, mutta jokainen yksittäinen dokumentti noudattaa samaa loogista UBL-puurakennetta.

🔢 6. “Unic Value?”

Oikealla oleva sininen laatikko viittaa kysymykseen uniikista arvosta – esimerkiksi yksilöllisestä tunnisteesta (cbc:ID), jolla tietue voidaan erottaa muista.

Tämä on tärkeä, kun dokumentteja linkitetään toisiinsa (esim. tilaus–toimitus–lasku).

🧠 Yhteenveto
Vertaus	UBL-termi	Selitys
Metsä	Dokumenttijoukko	Kaikki UBL-dokumentit (esim. Order, Invoice)
Puu	Dokumentti	Yksittäinen liiketoimintasanoma
Oksa	cac:	Rakenne- eli aggregaattielementti
Lehti	cbc:	Perusarvo, kuten nimi tai osoite
Uniikki arvo	cbc:ID tms.	Dokumentin tai osan yksilöivä tunniste
