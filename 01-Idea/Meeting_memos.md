


---


# BETK Working Group Discussion – April 24, 2025

The BETK working group is modifying Peppol procurement documents for use in the construction industry. In addition to individual documents, the group is developing a unified semantic data model called OneRecord (based on Peppol/UBL).
Core Concept: OneRecord
OneRecord combines all procurement-related Peppol documents into a single logical data model. Instead of assigning basic content (cbc) values independently per document, each data element receives a unique and context-specific content value across the entire OneRecord structure.
Documents Included in OneRecord:
Catalogue
Catalogue Response
Order
Order Response
Despatch Advice
Invoice


The aggregate components (cac) and basic elements (cbc) of these documents are merged into a unified schema, “OneRecord.”
Objective: Semantic-Based ERP Integration Mapping
The goal is to enable ERP-to-standard mappings based on actual data content rather than just schema structure. The process includes:
Companies should have a OneRecord model containing all elements and the unique example values (cbc).


The company then generates its documents (e.g., order, invoice) using the same unique values.


Comparing outputs enables the identification of corresponding elements in the ERP and UBL models. This forms a mapping between the systems.
When unic values (identifiers/examples) are human-readable, they are also AI machine-readable.


The result is a simple Excel-based mapping model that can be used across different ERP and integration tools.
Excel
A graphical tool which establishes mapping in JSON format
 
UBL does not have a graphical illustration. Mikael af Hällström from Finnish Tax has established a graphical illustration of OneRecord using this method.  


Why This Approach?
Traditional data model integration between ERP systems and standards, such as UBL, EDI, and RosettaNet, is often complex due to differing logic and implementations. By basing the mapping on example values, the process becomes more intuitive, even for those without expertise.
How do we create OneRecord?
A document has a sender and a receiver, i.e. a process
Original data (Unic)
In which document (sender - receiver(s) a new and original data was created
How is this data having a unique name (only one in OneRecord)
Data reused
How is this original data reused, and in which documents
OneRecord Excel has all documents (sender-receiver), i.e. processes
Are there duplicates that we should remove from the OneRecord Excel 
How is this operated in the Interoperability platform
OneRecord and the Interoperability platform need to be compliant


AI: Idea for OneRecord 
Perfect 👍 Here’s the English version of the PEPPOL document process for the  element example, with the same logic:

🔹 PEPPOL Process for a Wall Element
1. Catalogue
Green (new unique value):


Product: Wall element 3x6 m (product code, description, dimensions, price)


Links: DPP (Digital Product Passport), EPD (Environmental Product Declaration)
Supplier (element factory)


This creates the baseline → all following steps reference these values.



2. Order
Blue (reused information):


Reference to product code (from catalogue)
Reference to supplier
Links to DPP/EPD


Green (new unique value):


Buyer (construction company) appears for the first time
Delivery address and requested delivery date



3. Order Response
Blue (reused information):


Product code and links to DPP/EPD
Buyer and supplier


Green (new unique value):


Final confirmed delivery date
Batch/lot number (traceability starts here)



4. Transport Document
Blue (reused information):


Product code, buyer, supplier
Link to DPP → includes handling and transport requirements


Green (new unique value):


Logistics provider appears for the first time
Transport vehicle, route, and schedule



5. Despatch Advice
Blue (reused information):


Product code and quantities
Batch/lot number (from order response)
Links to DPP/EPD
Buyer, supplier, logistics provider


No new actors, just confirmation of shipment.



6. Receiving Advice
Blue (reused information):


Reference to despatch advice, product code, batch/lot number
Links to DPP/EPD (can be checked at reception)
Buyer and supplier


Green (new unique value):


Reception status (OK / missing / damaged)



7. Invoice
Blue (reused information):


Product code, order number, delivery number
Links to DPP/EPD (for archiving and traceability)
Buyer, supplier


Green (new unique value):


Payment terms (e.g., 14 days net, late interest rate)



🔑 Core Logic
New unique values (green) are introduced in the catalogue (product, DPP/EPD, supplier) and later when new actors or process-specific data appear (buyer, logistics provider, batch number, reception status, payment terms).


Reused values (blue) ensure that product, actor, and reference data flow consistently through the entire chain without being re-entered.




Graphical tool for OneRecord

AI-Assisted Integration
The working group plans to utilise AI tools to assist in mapping generation and automation, further simplifying interoperability across systems.
