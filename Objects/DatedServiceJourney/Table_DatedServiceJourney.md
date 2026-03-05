# DatedServiceJourney — Schema vs Profile requirements

This table explicitly distinguishes the NeTEx XSD (schema) cardinality from the profile-level requirements used for day-specific timetable publications.

| Element | Schema (XSD) cardinality | Profile requirement (day-specific timetable publication) | Description |
|---|---|---|---|
| DatedServiceJourney (container in TimetableFrame/vehicleJourneys) | 0..* | As needed | Day-specific instance of a ServiceJourney. |
| @id | required | required | ERP scoped identifier, e.g. ERP:DatedServiceJourney:2026-01-01-12345 |
| @version | required | required | Use profile-compliant versioning. |
| JourneyRef | 1 | required | Reference to the underlying ServiceJourney. |
| OperatingDayRef | 1 | required | Operating day of this DatedServiceJourney. |
| ServiceAlteration | 0..1 | optional | Status of the journey (e.g. cancellation, replacement, reinforcement). |
| DatedCalls | 0..1 (optional in XSD) | REQUIRED for day-specific timetable publications; MAY be omitted if ServiceAlteration=cancellation and no stop-level data are published | Container for one or more DatedCall elements. |
| DatedCall | 0..* | When DatedCalls is present: at least the stop sequence relevant to the publication must be included | Stop-level dated timing and references. |

Notes
- Schema vs profile: DatedCalls is optional in the NeTEx XSD, but this profile requires DatedCalls for day-specific timetable publications. A cancelled DatedServiceJourney may be published without DatedCalls provided that ServiceAlteration is set to cancellation.
- Codespace: All identifiers must use the ERP codespace.
