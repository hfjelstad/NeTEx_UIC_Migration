# FareContract (Part 3 – Sales)

## Definition
A FareContract represents the legal agreement between a customer and a fare provider for one or more purchased travel products and associated rights to travel. It records the contractual terms for use, validity, and entitlements resulting from a sales transaction.

## Purpose
To capture the outcome of a sale in a machine-readable form that can be exchanged across systems. The FareContract binds the customer (via a CustomerAccount) to one or more CustomerPurchasePackage items and an optional TravelSpecification describing the intended use.

## Key elements
- FareContract: The root contract entity created as the result of a completed sale. Identifies the contract, the customer context, the type of contract, and the entries included.
- FareContractEntry: A line within a FareContract representing a purchased package (e.g., a ticket product). Each entry references the CustomerPurchasePackage to which the customer is entitled and may point to a TravelSpecification.
- TypeOfFareContract: Classifies the contract (e.g., standard, subscription, corporate). Referenced from FareContract via TypeOfFareContractRef to indicate the semantics and business rules for the contract.
- Relationships to CustomerPurchasePackage: Each FareContractEntry must reference a CustomerPurchasePackage (CustomerPurchasePackageRef) describing the specific rights and validity purchased.
- Relationship to TravelSpecification: A FareContract or its entries may reference a TravelSpecification (TravelSpecificationRef) describing the planned or permitted travel scope (e.g., origin–destination, zones, routes) that applies to the purchased package.
- Use of CustomerAccountRef: The contract associates to a customer context using CustomerAccountRef so that entitlements and after-sales actions can be managed for that customer.

## Relationships
- FareContract → FareContractEntry: 1..* entries that enumerate each purchased package within the contract.
- FareContract → TypeOfFareContractRef: 1 reference defining the contract category used.
- FareContract → CustomerAccountRef: 0..1 link to the customer’s account for identification and after-sales management.
- FareContractEntry → CustomerPurchasePackageRef: 1 reference to the purchased customer package (rights to travel).
- FareContractEntry → TravelSpecificationRef: 0..1 optional reference narrowing or describing the travel entitlement.

## Conformance notes
- Identifiers should use the ERP codespace (e.g., ERP:FareContract:FC_123) when creating ids and refs for this profile.
- The minimal exchange uses SalesTransactionFrame to carry contracts. See the example file and the SalesTransactionFrame documentation.

## Example(s)
See: Objects/FareContract/Example_FareContract_Minimal.xml