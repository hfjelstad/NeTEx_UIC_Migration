# DatedServiceJourney – NeTEx 2.0 Validation Status

This page records schema validation results for the DatedServiceJourney example set, using the NeTEx 2.0 XSDs under "XSD 2.0/xsd" and the procedure in Guides/Validation.md.

Validation summary
- Entry point schema: XSD 2.0/xsd/NeTEx_publication_timetable.xsd
- Relevant object schemas: 
  - XSD 2.0/xsd/netex_part_2/part2_journeyTimes/netex_datedVehicleJourney_support.xsd
  - XSD 2.0/xsd/netex_part_2/part2_journeyTimes/netex_datedVehicleJourney_version.xsd
- Codespace used in examples: ERP

Pass/Fail table (per example)

| Example | Result | Notes |
|---|---|---|
| Objects/DatedServiceJourney/Example_DatedServiceJourney.xml | Fail | Not a complete PublicationDelivery document; provide minimal PublicationDelivery envelope and appropriate frame for XSD resolution (see Guides/Validation.md). |
| Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_01_Reinforcement.xml | Fail | Fragment only; requires PublicationDelivery envelope and frame context. |
| Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_02_Replacement.xml | Fail | Fragment only; requires PublicationDelivery envelope and frame context. |
| Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_03_BlockLinked.xml | Fail | Fragment only; requires PublicationDelivery envelope and frame context. |
| Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_04_MultiRef.xml | Fail | Fragment only; requires PublicationDelivery envelope and frame context. |

Notes
- Validation is performed against NeTEx 2.0 publication schemas. For part 2 constructs such as DatedVehicleJourney, validation should use NeTEx_publication_timetable.xsd as entry point.
- If an example is intended as a fragment, temporarily wrap it in a PublicationDelivery envelope when validating (do not commit the temporary file). See Guides/Validation.md for a ready-to-copy envelope template.

Changelog
- 2026-02-27: Added validation table, XSD pointers, and notes. Initial status marked as Fail for examples that are fragments pending addition of a minimal PublicationDelivery envelope and required frame for schema resolution.
