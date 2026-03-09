# DatedServiceJourney — Practical example (Oslo S → Bergen)

This folder contains a practical, profile-compliant example for a DatedServiceJourney between Oslo S and Bergen using the ERP codespace for all identifiers. The example demonstrates the required linkage between ServiceJourney, OperatingDay, and the dated instance with DatedCalls (only Oslo S and Bergen for simplicity).

Important: See the existing XML examples in this folder (e.g., Example_DatedServiceJourney.xml) for a full reference shape that conforms to NeTEx v2.0 and this profile.


## Minimum fields required by the profile (summary)

The following fields are the minimum typically required to represent a dated train journey instance in this profile. Field names follow NeTEx element names.

| Object | Field | Purpose |
|---|---|---|
| OperatingDay | OperatingDay.id (ERP:OperatingDay:YYYY-MM-DD) | Unambiguous calendar date anchor for the dated operation |
| OperatingDay | CalendarDate | The ISO date of operation (e.g., 2026-04-01) |
| ServiceJourney | ServiceJourney.id (ERP:ServiceJourney:OSL-BGN:1) | Logical journey pattern reference for the dated instance |
| ServiceJourney | Name | Human-readable label (e.g., "Oslo S - Bergen") |
| DatedVehicleJourney | DatedVehicleJourney.id (ERP:DatedServiceJourney:OSL-BGN:YYYY-MM-DD) | Unique identifier of the dated instance |
| DatedVehicleJourney | derivedFromRef → ServiceJourneyRef | Connects the dated instance to the logical ServiceJourney |
| DatedVehicleJourney | operatingDayRef | Binds the dated instance to the OperatingDay |
| DatedCall (1) | Order=1 | First call (Oslo S) |
| DatedCall (1) | StopPlaceRef OR StopPointInJourneyPatternRef | Stop reference (Oslo S) |
| DatedCall (1) | DepartureTime | Scheduled departure from Oslo S |
| DatedCall (2) | Order=2 | Last call (Bergen) |
| DatedCall (2) | StopPlaceRef OR StopPointInJourneyPatternRef | Stop reference (Bergen) |
| DatedCall (2) | ArrivalTime | Scheduled arrival to Bergen |

Note: All identifiers should use the ERP codespace prefix (e.g., ERP:OperatingDay:..., ERP:ServiceJourney:...). Additional elements (e.g., JourneyPattern, ScheduledStopPoint) may be required depending on the surrounding frames and organizational rules; see the existing examples for a complete structure.


## How-to — Recreate this setup

Follow these steps to create a dated instance for the Oslo S → Bergen train using the ERP codespace. The steps align with the structure demonstrated by the examples already present in this folder.

1) Create an OperatingDay
   - id: ERP:OperatingDay:2026-04-01
   - CalendarDate: 2026-04-01

2) Ensure there is a logical ServiceJourney for Oslo S → Bergen
   - id: ERP:ServiceJourney:OSL-BGN:1
   - Name: Oslo S - Bergen
   - (If your setup requires it) reference a JourneyPattern consisting of two points: Oslo S then Bergen.

3) Create the dated instance (DatedVehicleJourney)
   - id: ERP:DatedServiceJourney:OSL-BGN:2026-04-01
   - derivedFromRef: ERP:ServiceJourney:OSL-BGN:1 (versionRef=1)
   - operatingDayRef: ERP:OperatingDay:2026-04-01 (versionRef=1)

4) Add the two DatedCalls
   - DatedCall #1 (Order=1)
     - Stop reference: Oslo S (StopPlaceRef or StopPointInJourneyPatternRef)
     - DepartureTime: 08:25:00
   - DatedCall #2 (Order=2)
     - Stop reference: Bergen (StopPlaceRef or StopPointInJourneyPatternRef)
     - ArrivalTime: 14:57:00

5) Validate against NeTEx v2.0
   - Always validate the raw XML text before committing.
   - After committing a .xml file, validate the committed file as well.

6) Use ERP codespace consistently
   - Prefix all identifiers with ERP: and follow the object naming conventions as shown above.


## Where to look in this repository

- Objects/DatedServiceJourney/Example_DatedServiceJourney.xml — base example
- Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_*.xml — extended scenarios (e.g., replacement, block linked)

These examples illustrate the canonical structure expected by the profile, including how the dated instance relates to its ServiceJourney and operating day. Adjust identifiers and times as needed for your specific operating date(s).