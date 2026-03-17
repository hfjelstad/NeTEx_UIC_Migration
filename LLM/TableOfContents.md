# Repository Navigation Guide (Table of Contents)

This table of contents is intended to help quickly navigate the documentation and resources in this repository.
Keep this table "up-to-date", never delete anything in this table, only mark things that are removed.

Quick links:
- [Validate XML](#validate-xml)
- [Interchange only](#interchange-only)
- [Frames](#frames)
- [Objects](#objects)
- [Examples](#examples)

## Root
High-level entry points to the repository.
- [README.md](../README.md)
- [TableOfContents.md](TableOfContents.md) (you are here)

## Guides
How-to guides, conceptual overviews, and validation instructions.
- [README](../Guides/README.md) — overview of the guides section.
- [Get Started Guide](../Guides/GetStarted_Guide.md) — minimal steps to begin working with the profile.
- [Frames Overview](../Guides/FramesOverview.md) — explains the purpose and relationships of the various Frames.
- [Validation](../Guides/Validation.md) — how to validate NeTEx XML against schemas and rules.
- [Separation of Concerns](../Guides/SeparationOfConcerns.md) — clarifies responsibilities and boundaries between components.
- Interchange Only
  - [README](../Guides/InterchangeOnly/README.md) — scope and intent of the Interchange-only profile.
  - [Mandatory Interchange Guide](../Guides/InterchangeOnly/MandatoryInterchange_Guide.md) — required elements and constraints.
- [NeTEx Conventions](../Guides/NeTEx_Conventions.md) — casing rules (lowerCamelCase for lists) and a minimal example.

## Frames
Model-specific frame directories used to organize data and documentation.
- [FareFrame](../Frames/FareFrame/)
- [ResourceFrame](../Frames/ResourceFrame/)
- [SalesTransactionFrame](../Frames/SalesTransactionFrame/)
- [ServiceCalendarFrame](../Frames/ServiceCalendarFrame/)
- [ServiceFrame](../Frames/ServiceFrame/)
- [SiteFrame](../Frames/SiteFrame/)
- [TimetableFrame](../Frames/TimetableFrame/)
- [VehicleScheduleFrame](../Frames/VehicleScheduleFrame/)

## Objects
Core NeTEx object categories, grouped for discoverability.
- [AlternativeName](../Objects/AlternativeName/)
- [AlternativeText](../Objects/AlternativeText/)
- [Authority](../Objects/Authority/)
- [Codespace](../Objects/Codespace/)
- [Contract](../Objects/Contract/)
- [DatedServiceJourney](../Objects/DatedServiceJourney/)
- [DayType](../Objects/DayType/)
- [DestinationDisplay](../Objects/DestinationDisplay/)
- [FareContract](../Objects/FareContract/)
- [FareZone](../Objects/FareZone/)
- [FlexibleServiceProperties](../Objects/FlexibleServiceProperties/)
- [GroupOfLines](../Objects/GroupOfLines/)
- [Interchange](../Objects/Interchange/)
- [JourneyPattern](../Objects/JourneyPattern/)
- [Line](../Objects/Line/)
- [LinkSequenceProjection](../Objects/LinkSequenceProjection/)
- [Notice](../Objects/Notice/)
- [OperatingPeriod](../Objects/OperatingPeriod/)
- [Operator](../Objects/Operator/)
- [Parking](../Objects/Parking/)
- [PassengerStopAssignment](../Objects/PassengerStopAssignment/)
- [PurposeOfGrouping](../Objects/PurposeOfGrouping/)
- [Quay](../Objects/Quay/)
- [ResponsibilitySet](../Objects/ResponsibilitySet/)
- [Route](../Objects/Route/)
- [SanitaryEquipment](../Objects/SanitaryEquipment/)
- [ScheduledStopPoint](../Objects/ScheduledStopPoint/)
- [ServiceJourney](../Objects/ServiceJourney/)
- [ShelterEquipment](../Objects/ShelterEquipment/)
- [StopPlace](../Objects/StopPlace/)
- [TariffZone](../Objects/TariffZone/)
- [TicketingEquipment](../Objects/TicketingEquipment/)
- [TopographicPlace](../Objects/TopographicPlace/)
- [TrainBlock](../Objects/TrainBlock/)
- [Vehicle](../Objects/Vehicle/)
- [VehicleType](../Objects/VehicleType/)
- [WaitingRoomEquipment](../Objects/WaitingRoomEquipment/)

## LLM
AI assistance materials and examples that complement the documentation.
- [Table of Examples](TableOfExamples.md) — prompt and response examples for common tasks.
- [Validated XML Example](Validatet_XML_Example.xml) — a small, valid NeTEx XML snippet for reference/testing.

## Continuous Integration
Automation for validating XML and ensuring quality.
- GitHub Actions: [validate-netex-xml.yml](../.github/workflows/validate-netex-xml.yml)

---

## Validate XML
- How-to: see [Validation guide](../Guides/Validation.md).
- Sample: use [Validated XML Example](Validatet_XML_Example.xml).
- CI: run or inspect [.github/workflows/validate-netex-xml.yml](../.github/workflows/validate-netex-xml.yml).
- Schemas: see [XSD folder](../XSD%202.0/xsd/).

## Interchange only
- Overview: [Interchange-only README](../Guides/InterchangeOnly/README.md).
- Mandatory fields: [Mandatory Interchange Guide](../Guides/InterchangeOnly/MandatoryInterchange_Guide.md).
- Related objects: [Interchange](../Objects/Interchange/) and [ServiceJourney](../Objects/ServiceJourney/).

## Examples
- Prompt and response examples for LLM: [Table of Examples](TableOfExamples.md).
- Best-practice PublicationDelivery XML: [Frames/Example_PublicationDelivery.xml](../Frames/Example_PublicationDelivery.xml).
