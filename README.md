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

**OneRecord ontology**

Intro

The interoperability of information from design to operations is a well-recognized challenge in the architecture, engineering, and construction (AEC) industry. As a potential solution to these interoperability issues, there has been growing interest in applying linked data and semantic web technologies to establish an extensible data model. Although several semantic web ontologies have been developed for the AEC domain, a comprehensive ontology for representing the reusable, generated, and enriched transaction information throughout supply chain processes is still lacking.

The Peppol network provides an international communication infrastructure that enables organizations to exchange electronic business documents securely and efficiently. In the Nordic countries, e-invoices are currently the most widely used standardized electronic business documents within the AEC sector. However, similar developments are now emerging for other types of electronic business documents, such as catalogues, orders, delivery information exchanges, and receipt responses.

---

So far, we have two candidate ontology representations.

**Interoperability platform**
[Finnish Construction Industry One Record](https://tietomallit.suomi.fi/model/fcior?ver=0.0.1)

**Concept draft of OneRecord ontology**

![WhatsApp-Kuva 2025-10-22 klo 17 19 27_e4c49276](https://github.com/user-attachments/assets/73b67127-799c-4c3e-a4a5-92f9ed1cdf29)




| Aspect                               | FCIOR Model                                                                                                                   | Your Model                                                                                                                                          |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Document coverage**                | Covers the *Catalogue → Order → Despatch Advice → Invoice* chain according to the UBL 2.4 structure.                          | Covers the *Order → OrderRespond → OrderFinance → Invoice* chain, and additionally includes *TransportOrder* and *Delivery*.                        |
| **Concepts**                         | Primarily uses UBL-type concepts (Order, Despatch, Invoice).                                                                  | Includes AEC- and supply chain–specific concepts such as *Transport*, *PricedItem*, *Total*, and *OrderFinance*.                                    |
| **Relationships**                    | Not represented as a clear graph but refer to UBL’s semantic relations (e.g., OrderLine, SupplierParty, DeliveryTerms).       | Depicts explicit RDF-type relationships such as `one:hasOrder`, `one:hasDelivery`, `one:hasPrice`, `one:hasTotal`, etc.                             |
| **Transactional and financial data** | Financial elements (Price, Tax, Amount) are embedded within UBL document structures.                                          | Finance is modeled as a separate layer (`OrderFinance`, `Total`, `Price`), linked to both *Order* and *Transport* levels.                           |
| **Transport information**            | FCIOR includes references to *Despatch Advice* and *Transport Handling Unit* but lacks a distinct *TransportOrder* structure. | Your model explicitly defines *TransportOrder*, *TransportItem*, and *Transport* classes, each with their own *hasTotal* and *hasPrice* properties. |
| **Ontological extensibility**        | Aims to integrate existing UBL documents into a unified semantic model.                                                       | Represents an ontologically extensible model that connects business documents (Peppol) with supply chain transactions.                              |


| Osa-alue                        | FCIOR-malli                                                                                                                  | Kuvasi malli                                                                                                                           |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Dokumenttien kattavuus**      | Kattaa *Catalogue → Order → Despatch Advice → Invoice* -ketjun UBL 2.4 -rakenteen mukaisesti.                                | Kattaa *Order → OrderRespond → OrderFinance → Invoice* -ketjun ja lisäksi *TransportOrder* ja *Delivery*.                              |
| **Käsitteet**                   | Käyttää pääasiassa UBL-tyyppisiä käsitteitä (Order, Despatch, Invoice).                                                      | Sisältää AEC- ja toimitusketjukohtaisia käsitteitä kuten *Transport*, *PricedItem*, *Total*, *OrderFinance*.                           |
| **Relaatiot**                   | Eivät näy selkeänä graafina, mutta viittaavat UBL:n semanttisiin suhteisiin (esim. OrderLine, SupplierParty, DeliveryTerms). | Kuva esittää eksplisiittiset RDF-tyyppiset relaatiot: `one:hasOrder`, `one:hasDelivery`, `one:hasPrice`, `one:hasTotal`, jne.          |
| **Transaktiotieto ja talous**   | Taloudelliset elementit (Price, Tax, Amount) sisältyvät UBL:n dokumenttien sisälle.                                          | Talous on erillisenä kerroksena (`OrderFinance`, `Total`, `Price`) ja liitetty sekä *Order* että *Transport* -tasoille.                |
| **Kuljetustieto**               | FCIOR sisältää viittauksia *Despatch Advice* ja *Transport Handling Unit*, mutta ei erillistä *TransportOrder*-rakennetta.   | Kuvasi mallissa *TransportOrder*, *TransportItem* ja *Transport* ovat eksplisiittisiä luokkia, joilla on oma *hasTotal* ja *hasPrice*. |
| **Ontologinen laajennettavuus** | Tavoitteena yhdistää olemassa olevat UBL-dokumentit yhteen semanttiseen malliin.                                             | Esittää ontologisesti laajennettavan mallin, joka yhdistää liiketoimintasanomat (Peppol) ja toimitusketjun transaktiot.                |

