# FareFrame

## 1. Purpose

A **FareFrame** contains fare data, products, and pricing rules for a public transport delivery. It groups Tariffs, ValidableElements, PreassignedFareProducts, and SalesOfferPackages — the elements that define what passengers can buy and at what price.

## 2. Contained Elements

- **tariffs** – Collection of Tariff definitions describing fare structures and pricing rules
- **validableElements** – Collection of ValidableElement definitions representing travel rights that can be validated
- **fareProducts** – Collection of fare product types:
  - PreassignedFareProduct – A pre-defined fare product (e.g., single ticket) with access rights and tariff references
- **salesOfferPackages** – Collection of SalesOfferPackage definitions bundling fare products for sale

## 3. Frame Relationships

FareFrame depends on **ResourceFrame** for organisational context. It may reference [TariffZone](../../Objects/TariffZone/Table_TariffZone.md) definitions. **SalesTransactionFrame** references fare products and sales offer packages defined here. FareFrame is typically wrapped in a **CompositeFrame** within a PublicationDelivery.

For the full structural specification, see [Table — FareFrame](Table_FareFrame.md).
Example XML: [Example_FareFrame.xml](Example_FareFrame.xml)
