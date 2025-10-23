# OneRecord use case story

**Käyttötapausesimerkki:** Ontologiaan perustuva transaktiotiedonvaihto rakennusalalla

**Tavoite:**
Mahdollistaa yhteentoimiva ja uudelleenkäytettävä transaktiotiedonvaihto rakennusprojektin osapuolten välillä hyödyntämällä Peppol-verkkoa ja ontologiaan perustuvaa tietomallia.

**Toimija:**
Lähettäjä - vastaanottaja (esim. Rakennustuotetoimittaja/urakoitsija, Rakennustuotetoimittaja/tuotevalmistaja).

**Käyttötapaus:**
Rakennustuotetoimittajana haluan lähettää ja vastaanottaa standardoituja sähköisiä liiketoimintasanomia (esim. tilaus, lähetysilmoitus, vastaanottokuittaus, logistiikkasanomat) Peppol-verkon kautta siten, että yhteinen ontologia varmistaa tietojen yhdenmukaisuuden ja aiemmin luotua dataa voidaan hyödyntää prosessin myöhemmissä vaiheissa (suunnittelu–valmistus–toimitus–asennus).




**OneRecord ontologia**
*  liiketoimintaan/toimitusketjuun liittyvät osapuolet (organisaatiot)
*  liiketoiminta-asiakirjojen (sanomien) sisällön (katalogi, tilaus, toimitus, logistiikka sanomat) udelleen käytettävä tieto (OneRecord excelin esittäminen graafina)
  * lähettäjä
  * vastaanottaja

  * luokkakaavio OWL-muodossa
  * --> Drawio muodossa esitetty

<img width="691" height="467" alt="Näyttökuva 2025-10-22 090556" src="https://github.com/user-attachments/assets/48e6a02d-b78f-4993-bd4c-ff89f4e19f2f" />

---

# OneRecord ontology

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

