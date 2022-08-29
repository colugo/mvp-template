


## Data Model of [jargon/CustomsDeclaration](/user/jargon/CustomsDeclaration/v/3.0.0)

![Data Model of jargon/CustomsDeclaration]({{ site.jargon.staticFiles }}jargon_CustomsDeclaration_dataModel.svg)
## State Diagram of [Declaration](/user/jargon/CustomsDeclaration/v/3.0.0#artefacts)

![State Diagram of jargon/CustomsDeclaration/Declaration]({{ site.jargon.staticFiles }}jargon_CustomsDeclaration_Declaration_lifeCycle.svg)
## State Diagram of [Invoice](/user/jargon/CustomsDeclaration/v/3.0.0#artefacts)

![State Diagram of jargon/CustomsDeclaration/Invoice]({{ site.jargon.staticFiles }}jargon_CustomsDeclaration_Invoice_lifeCycle.svg)
## Open API Specification of [jargon/CustomsDeclaration](/user/jargon/CustomsDeclaration/v/3.0.0)

This specification is available in different forms:
- As a [JSON specification]({{ site.jargon.staticFiles }}jargon_CustomsDeclaration_openapi.json)
- As a [browsable Swagger Ui page]({{ site.jargon.staticFiles }}jargon_CustomsDeclaration_openapi.json)
## Data Definitions of [jargon/CustomsDeclaration](/user/jargon/CustomsDeclaration/v/3.0.0)

### DeclarationHeader

Property | Definition | Type
--- | --- | ---
declarantAgentParty | The name, expressed as text, for this trade product group. | Text
identificationId | The unique identifier of this logistics label. | Text


### ExportDeclaration

Property | Definition | Type
--- | --- | ---
sender |  | [SenderDetails](#senderdetails)
expectedDateOfExport | The date, time, date time or other date time value when this supply chain consignment will exit, or has exited from the last port, airport, or border post of the country of export. | Text
warehouseId | The unique identifier of this logistics label. | Text
branchId | The unique identifier of this logistics label. | Text
customableExciseIndicator | Identifies if this export is excisable. | Indicator
goodsOwner |  | [PartyDetails](#partydetails)
confirmingExportType | An identifier assigned to indicate conformity with a regulation or standard for this trade product, such as "CE" which declares that the product conforms with the essential requirements of the applicable EC directives. | Text
transport |  | [TransportDetails](#transportdetails)
goodsDetails |  | [GoodsDetail](#goodsdetail)
invoiceDetails |  | [InvoiceDetail](#invoicedetail)
theItems |  | [ItemDetails](#itemdetails)
declarantAgentParty | The name, expressed as text, for this trade product group. | Text
identificationId | The unique identifier of this logistics label. | Text


### ItemDetails

Property | Definition | Type
--- | --- | ---
globalId | A globally unique identifier of this trade party. | Text
description | A textual description of this supply chain schedule. | Text
weight | The measure of the gross weight (mass) of this referenced logistics package and its contents. | Text
unitValue | A monetary value of the unit of this trade price. | Text
quantity | The number of packages in this subordinate line trade delivery. | Text


### InvoiceDetail

Property | Definition | Type
--- | --- | ---
currencyCode | The code specifying the source currency of a trade related currency conversion. | Text
FOBCurrencyCode | The code specifying the source currency of a trade related currency conversion. | Text
totalFOBValue | The monetary value of all freight and other service charges for this supply chain consignment item. | Text


### GoodsDetail

Property | Definition | Type
--- | --- | ---
exportGoodsType | The code specifying the type of specification query. | Text
totalPackages | The number of packages in this subordinate line trade delivery. | Text
totalContainers | The number of packages in this subordinate line trade delivery. | Text


### TransportDetails

Property | Definition | Type
--- | --- | ---
consigneeName | The name, expressed as text, for this trade product group. | Text
consigneeCity | The name, expressed as text, of the city, town or village of this trade address. | Text
portOfLoading | The name, expressed as text, for this trade product group. | Text
firstPortOfDischarge | The name, expressed as text, for this trade product group. | Text
finalDestinationCountryCode | The unique identifier of this logistics label. | Text
modeOfTransport | The type, as expressed as text, of the logistics transport movement. | Text
vesselId | The unique identifier of this logistics label. | Text
voyageNumber | A unique identifier for this logistics transport movement, such as a voyage number, flight number, or trip number, as stated in a schedule. | Text
flightNumber | A unique identifier for this logistics transport movement, such as a voyage number, flight number, or trip number, as stated in a schedule. | Text


### SenderDetails

Property | Definition | Type
--- | --- | ---
partyDetails |  | [PartyDetails](#partydetails)
senderReference | The sender-recipient sequence identifier for this supply chain trade transaction. | Text


### PartyDetails

Property | Definition | Type
--- | --- | ---
id | The unique Business Entity Identifier (BEI) as defined by ISO 9362 (Banking telecommunication messages, Bank Identifier Codes) for this requesting party. | Text




