# Lifecycle for DatedServiceJourney

Purpose
- Describe how a DatedServiceJourney (DSJ) changes through the operational day and how ServiceAlteration and references should be used.

When to use
- Use this document when modelling day-specific variations of a ServiceJourney for a concrete OperatingDay, including reinforcement (extraJourney) and replacement scenarios.

Key lifecycle states (ServiceAlteration)
- planned (default): The DSJ runs as planned without special alteration. If ServiceAlteration is omitted, treat as planned.
- extraJourney: An additional DSJ not present in the timetable plan, typically to increase capacity (reinforcement).
- replaced: The DSJ replaces one or more existing dated journeys. Use replacedJourneys/DatedVehicleJourneyRef to point at the dated journeys being replaced.
- cancelled (profile-dependent): If supported in the profile, can be used to indicate cancellation for the day. If not supported, use operational data outside this profile to represent cancellations.

Relationships
- DatedServiceJourney must reference exactly one ServiceJourney (ServiceJourneyRef) from the same TimetableFrame.
- DatedServiceJourney must reference exactly one OperatingDay (OperatingDayRef) from the same TimetableFrame.
- DatedServiceJourney may reference a Block/TrainBlock using BlockRef to indicate vehicle/rail block chaining on the day.

Validation recommendations
- Resolve all references: ServiceJourneyRef and OperatingDayRef MUST resolve within the same TimetableFrame; BlockRef SHOULD resolve within a compatible operational frame in the same PublicationDelivery.
- Default semantics: If ServiceAlteration is missing, treat as planned (no change in semantics from the underlying ServiceJourney).
- Replacement mapping: For ServiceAlteration = replaced, every DatedVehicleJourneyRef in replacedJourneys MUST resolve to a dated journey ID present in the same delivery (or a referenced frame in the delivery).
- Consistent IDs: Use ERP codespace for all IDs and references (e.g., ERP:DSJ:..., ERP:SJ:..., ERP:OD:...).
- Versioning: Maintain version coherence across related objects (ServiceJourney, JourneyPattern, DayType, etc.). DSJ version increments when its own content changes for the day.

Common pitfalls
- Do not redefine stop sequence or timing in DSJ; the sequence comes from the JourneyPattern of the referenced ServiceJourney.
- Do not confuse OperatingDay (a calendar date) with DayType (a rule set). DSJ uses OperatingDayRef; occurrence is controlled by the day’s operation, not the DayType rules directly.
- Do not use DatedServiceJourneyRef for replacedJourneys; use DatedVehicleJourneyRef as per NeTEx.

References
- Description: ./Description_DatedServiceJourney.md
- Table: ./Table_DatedServiceJourney.md
