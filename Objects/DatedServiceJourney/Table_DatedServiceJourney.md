# DatedServiceJourney — Field Table (Profile)

This table lists the minimum set of fields for a DatedServiceJourney in this profile, with cardinalities, concise descriptions, and profile-specific notes. See cross-links at the end for the conceptual description and lifecycle notes.

- See concept: Objects/DatedServiceJourney/Description_DatedServiceJourney.md
- See lifecycle: Objects/DatedServiceJourney/Lifecylce_DatedServiceJourney.md

| Field | Cardinality | Type | Description |
|------|-------------|------|-------------|
| id | 1..1 | Identifier | Globally unique identifier within codespace (use ERP). Example: ERP:DSJ:12345. |
| version | 1..1 | Version | Version of this DatedServiceJourney. Increment on any material change. |
| ServiceJourneyRef | 1..1 | Ref to ServiceJourney | Reference to the planned ServiceJourney on which this dated journey is based. Must resolve within the same TimetableFrame. |
| OperatingDayRef | 1..1 | Ref to OperatingDay | Reference to the calendar day on which this dated journey runs. Must resolve within the same TimetableFrame. |
| ServiceAlteration | 0..1 | Enum (planned | replaced | extraJourney) | Operational status of this dated journey. Default when omitted: planned. |
| BlockRef | 0..1 | Ref to Block/TrainBlock | Optional reference to a Block (or TrainBlock in rail) to chain work for vehicles/crews. |
| replacedJourneys | 0..1 | Container | Optional container listing the dated journeys that are replaced by this journey. |
| └─ DatedVehicleJourneyRef | 0..* | Ref to DatedServiceJourney | Reference(s) to the replaced dated journey(s). Each must resolve to a valid dated journey id. |

Validation rules (profile)
- ServiceJourneyRef and OperatingDayRef are both required and MUST resolve within the same TimetableFrame.
- If ServiceAlteration is absent, treat it as planned.
- Each DatedVehicleJourneyRef in replacedJourneys MUST resolve to a valid existing dated journey identifier.
- id MUST be unique and stable within the ERP codespace; version MUST be coherent across updates.
- If BlockRef is present, the referenced Block/TrainBlock MUST exist and be consistent with the scheduled sequence of journeys.

Common pitfalls and clarifications
- Do not confuse DatedServiceJourney with ServiceJourney: the former is a dated instance for a specific OperatingDay; the latter is the planned template.
- Sequence and timing come from the underlying JourneyPattern and the referenced ServiceJourney; do not redefine the stop sequence here.
- Do not confuse OperatingDay (a specific calendar date) with DayType (a reusable set of operating rules such as weekdays/holidays).
- Do not use DatedServiceJourneyRef in this profile for replacements; use DatedVehicleJourneyRef under replacedJourneys.

Cross-links and consistency
- Conceptual description: Objects/DatedServiceJourney/Description_DatedServiceJourney.md
- Lifecycle notes: Objects/DatedServiceJourney/Lifecylce_DatedServiceJourney.md
- Terms and reference names in this table align with the profile usage: ServiceJourneyRef, OperatingDayRef, BlockRef, ServiceAlteration, replacedJourneys/DatedVehicleJourneyRef.

Examples in this profile
- Minimal example: Objects/DatedServiceJourney/Example_DatedServiceJourney.xml (codespace ERP)
- Extended examples:
  - 01 Reinforcement (extraJourney): Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_01_Reinforcement.xml
  - 02 Replacement (replaced): Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_02_Replacement.xml
  - 03 Block-linked: Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_03_BlockLinked.xml
  - 04 Multi-ref: Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_04_MultiRef.xml
