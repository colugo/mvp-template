---
layout: reference
---




## Data Model of [gs_cargo/CargoExports](/user/gs_cargo/CargoExports/v/working)

![Data Model of gs_cargo/CargoExports]({{ site.jargon.staticFiles }}gs_cargo_CargoExports_dataModel.svg)
## Data Definitions of [gs_cargo/CargoExports](/user/gs_cargo/CargoExports/v/working)

### Message

Property | Definition | Type
--- | --- | ---
id | The unique transaction identifier for request. | Text
senderReference | The Senders Reference is a unique business-level reference number assigned by the document owner. | Text
reportingPartyId | Default value is the ABN/CCID (Australian Business Number/Customs Client Identifier) of the reporting party. | Text


### Consignment

```
A consignment is a transport order for the movement of goods made between a transport service buyer (who could be the importer or the exproter depending on incoterms) and a transport service seller (who could be a freight forwarder or a carrier). It is identified by a bill naumber that can can be at house level (house airway bill or house bill of lading) or at master level (master airway bill or ocean bill of lading).
```

Property | Definition | Type
--- | --- | ---
billNumber | A unique identifier. | Text
customsAuthorityNumber | A Customs Authority Number (CAN) will be created by the Integrated Cargo System to identify various Export Documents. If these goods have had a contingency Customs authority number issued to them, enter the contingency CAN here instead.The CAN is 9 characters long with a format of AAAAAAAAZ where **A** represents the Sequence Character and Zrepresents the Check Digit Character.Note: a Contingency CAN can only be used if the Exempt Code is EXCC. | Text
exemptGoodsDeclaration | An exempt goods declaration is required for any goods that have not already been delcared in an Export Declaration - for any of the reasons listed in the exemptionCode (usually for low value goods).  | [ExemptGoods](#exemptgoods)
destinationCountryCode | The UN country code for the country the cargo is going to be delivered to. | Code (countryCode)
packageCount | Number of packages that the goods are packed into, does not include packages packed into a container. | Numeric
containerCount | Number of containers the goods are packed into. | Numeric
status | Consignment status is a read-only structure that is returned by customs together with all API responses that include the Consignment object. The full status history is provided as an array of cargo status objects. | [ConsignmentStatus](#consignmentstatus)


### ConsignmentStatus

```
Consignment status is a read-only structure that is returned by customs together with all API responses that include the Consignment object. 
```

Property | Definition | Type
--- | --- | ---
statusCode | The status code of the export consignment.  Status values are defined by the cargoExport state lifecycle  | Code (cargoExportStatus)
statusDescription | Full description of the corresponding status code. | Text
statusDate | the date and time at which the status changed to this value. | DateTime


### ExemptGoods

```
An exempt goods declaration is required for any goods that have not already been delcared in an Export Declaration - for any of the reasons listed in the exemptionCode (usually for low value goods). 
```

Property | Definition | Type
--- | --- | ---
exemptionCode | The code that defines the basis for the goods being exempt from export declaration reporting (eg EXLV for low value goods). Allowed values are defined in the exemption code enumeration | Code (exemptionCode)
goodsOwnerPartyId | The ABN or CCID of the owner of the goods. | Text
goodsDescription | A plain text description of the cargo. | Text
goodsOwnerName | If the owner does not have an ABN/CCID, enter the owner name. | Text


### Consolidation

```
A consolidaiton is a collection of individual consignments(usually house level) that are consonoldated into a single consignment (usually at master level)
```

Property | Definition | Type
--- | --- | ---
id |  | Text
messageHeader |  | [Message](#message)
consolidationReferenceNumber | A Consolidation Reference Number (CRN) is the number assigned by Customs to a submanifest when the submanifest has been validated and processed by the ICS. The CRN remains unchanged even if the submanifest is subsequently amended, withdrawn or cancelled.The CRN is a Customs Authority Number (CAN), that is, a number that can be shown on other documents as a reference to the authority to deal with the goods listed on the submanifest. The CRN is not sufficient evidence that there is authority to deal with the consolidation, but is necessary evidence of authority to deal with an export consolidation.Like other CANs, the CRN is a string of nine alphanumeric characters. | Text
consignments |  | [Consignment](#consignment)
totalPackageCount | The package count for the entire consolidation (ie all contained consignments). | Numeric
totalContainerCount | The total number of containers in the consolidation (submanifest). | Numeric
emptyContainerCount | Number of empty containers that this report contains. Only applicable to Sea Cargo. | Numeric
nilCargoReportIndicator | Indicates whether any cargo is carried on the flight or the voyage of the vessel.Note: the Nil Cargo Indicator field cannot have a value of TRUE when consignments data exists. | Indicator
establishmentId | The identifier issued by the Department to an approved/licensed premises for loading/unloading of goods under Customs control until clearance is issued. | Text


### Manifest

```
The manifest is an abstract class for an air or sea manifest - that lists all consignments on a given flight or voyage.
```

Property | Definition | Type
--- | --- | ---
id |  | Text
manifestNumber | An identifier issued by the Department to identify Export Main Manifests. | Text
movementDetails |  | [ActualDeparture](#actualdeparture)
consignments |  | [Consignment](#consignment)
emptyContainerCount |  | Numeric


### Flight

```
The movement of a flight, between a series of ports, leaving and arriving on specific dates.
```

Property | Definition | Type
--- | --- | ---
movementLegs |  | Unset
id | The unique transaction identifier for request. | Text
flightNumber | A unique reference assigned by a carrier to identify a specific journey of an aircraft. | Text
airlineCode | A common code (issued by IATA) that identifies an airline/carrier. e.g.. QF = Qantas. | Text


### Voyage

```
The movement of a ship, between a series of ports, leaving and arriving on specific dates.
```

Property | Definition | Type
--- | --- | ---
movementLegs |  | Unset
id | The unique transaction identifier for request. | Text
voyageNumber | This is the Voyage Number of the vessel used to transport goods moving Underbond by Sea. | Text
vesselRegistrationNumber | The identifier, either a Lloyds Number or a Customs Ship Number, of a vessel. | Text
carrierPartyId | A Party ID assigned by the Department to carriers of Export goods. | Text


### AirManifest

```
The manifest is an abstract class for an air or sea manifest - that lists all consignments on a given flight or voyage.
```

Property | Definition | Type
--- | --- | ---
messageHeader |  | [Message](#message)
flight |  | [Flight](#flight)
id |  | Text
manifestNumber | An identifier issued by the Department to identify Export Main Manifests. | Text
movementDetails |  | [ActualDeparture](#actualdeparture)
consignments |  | [Consignment](#consignment)
emptyContainerCount |  | Numeric


### SeaManifest

```
The manifest is an abstract class for an air or sea manifest - that lists all consignments on a given flight or voyage.
```

Property | Definition | Type
--- | --- | ---
messageHeader |  | [Message](#message)
voyage |  | [Voyage](#voyage)
id |  | Text
manifestNumber | An identifier issued by the Department to identify Export Main Manifests. | Text
movementDetails |  | [ActualDeparture](#actualdeparture)
consignments |  | [Consignment](#consignment)
emptyContainerCount |  | Numeric


### TerminalMovement

```
The terminal movement is an abstract class for either a receival at or withdrawal from a termnial of a collection of consignments 
```

Property | Definition | Type
--- | --- | ---
id |  | Text
establishmentId | The identifier issued by the Department to an approved/licensed premises for loading/unloading of goods under Customs control until clearance is issued. | Text
transportMode |  | Code (transportModeCode)
consignments | The list of consignment items in this consolidation - each identified by a house bill number. | [Consignment](#consignment)


### TerminalWithdrawal

```
The terminal movement is an abstract class for either a receival at or withdrawal from a termnial of a collection of consignments 
```

Property | Definition | Type
--- | --- | ---
messageHeader |  | [Message](#message)
exemptGoodsDeclaration |  | Unset
id |  | Text
establishmentId | The identifier issued by the Department to an approved/licensed premises for loading/unloading of goods under Customs control until clearance is issued. | Text
transportMode |  | Code (transportModeCode)
consignments | The list of consignment items in this consolidation - each identified by a house bill number. | [Consignment](#consignment)


### TerminalReceival

```
The terminal movement is an abstract class for either a receival at or withdrawal from a termnial of a collection of consignments 
```

Property | Definition | Type
--- | --- | ---
messageHeader |  | [Message](#message)
id |  | Text
establishmentId | The identifier issued by the Department to an approved/licensed premises for loading/unloading of goods under Customs control until clearance is issued. | Text
transportMode |  | Code (transportModeCode)
consignments | The list of consignment items in this consolidation - each identified by a house bill number. | [Consignment](#consignment)


### Subscription

```
A unique relation to a topic by a subscriber that indicates it should receive updates for that topic. A subscription's unique key is the tuple (Topic URL, Subscriber Callback URL). Subscriptions may (at the hub's decision) have expiration times akin to DHCP leases which must be periodically renewed.
```

Property | Definition | Type
--- | --- | ---
id | The unique transaction identifier for request. | Text
hub | The Hub for this subscription | [Hub](#hub)


### Test

```
A step along the movement. Represented by a pair of from and to ports.
```

Property | Definition | Type
--- | --- | ---
scheduledDepartureDateTime |  | Unset
arrivalEstablishmentId |  | Unset
scheduledArrivalDateTime |  | Unset
actualArrivalDateTime |  | Unset
departureCountryCode |  | Unset
departurePortCode | The UNLOCODE of the port from which the goods covered by this departure report will leave/have left. | Code (unlocode)
departureEstablishmentId |  | Text
actualDepartureDateTime | The date, time, date time or other date time value of the actual departure related to this transport event. | Text
destinationCountryCode |  | Text
destinationPortCode | The UNLOCODE of the next port of destination of the vessel or aircraft carrying the goods. | Code (unlocode)


### Flight

```
The movement of a flight, between a series of ports, leaving and arriving on specific dates.
```

Property | Definition | Type
--- | --- | ---
id | The unique transaction identifier for request. | Text
flightNumber | A unique reference assigned by a carrier to identify a specific journey of an aircraft. | Text
airlineCode | A common code (issued by IATA) that identifies an airline/carrier. e.g.. QF = Qantas. | Text
movementLegs | An array of legs along this movement. Legs are a pair of from and to port identifiers. | [MovementLeg](#movementleg)


### Voyage

```
The movement of a ship, between a series of ports, leaving and arriving on specific dates.
```

Property | Definition | Type
--- | --- | ---
id | The unique transaction identifier for request. | Text
voyageNumber | This is the Voyage Number of the vessel used to transport goods moving Underbond by Sea. | Text
vesselRegistrationNumber | The identifier, either a Lloyds Number or a Customs Ship Number, of a vessel. | Text
carrierPartyId | A Party ID assigned by the Department to carriers of Export goods. | Text
movementLegs | An array of legs along this movement. Legs are a pair of from and to port identifiers. | [MovementLeg](#movementleg)


### Subscription

```
A unique relation to a topic by a subscriber that indicates it should receive updates for that topic. A subscription's unique key is the tuple (Topic URL, Subscriber Callback URL). Subscriptions may (at the hub's decision) have expiration times akin to DHCP leases which must be periodically renewed.
```

Property | Definition | Type
--- | --- | ---
id | The unique transaction identifier for request. | Text
hub | The Hub for this subscription | [Hub](#hub)




