# Table: DatedServiceJourney

| Element | Type | XSD Cardinality | ERP Cardinality | Description |
| --- | --- | --- | --- | --- |
| @id | xsd:ID | 1:1 | 1:1 | Unique identifier for the DatedServiceJourney. Use ERP codespace (e.g., ERP:DatedServiceJourney:OSL-BGN:2026-04-01). |
| @version | xsd:integer | 1:1 | 1:1 | Version number of the object instance. |
| ServiceJourneyRef | ServiceJourneyRef | 1:1 | 1:1 | Reference to the generic ServiceJourney from which journey details (e.g., JourneyPatternRef and passing times) are derived. |
| OperatingDayRef | OperatingDayRef | 1:1 | 1:1 | The OperatingDay on which this dated journey runs. |
| ServiceAlteration | ServiceAlterationEnumeration | 0:1 |  | Planned alteration type (planned, replaced, extraJourney). If omitted, treat as planned. |
| BlockRef | BlockRef | 0:1 |  | Reference to an operational Block/TrainBlock that links dated runs operationally. |
| replacedJourneys | ReplacedJourneys | 0:1 |  | Container for references to dated journeys being replaced or reinforced. |
| DatedVehicleJourneyRef | DatedVehicleJourneyRef | 0:* |  | Reference to a dated journey being replaced or reinforced by this one. |
| DatedCalls | DatedCalls | 0:1 | 1:1 | Container for dated calls (stops and times) specific to this dated journey. |
| DatedCall | DatedCall | 0:* | 1:* | Individual dated call. Includes stop reference and scheduled times. |
| StopPlaceRef | StopPlaceRef | 0:1 | 0:1 | Stop reference (alternative to StopPointInJourneyPatternRef for call location). |
| StopPointInJourneyPatternRef | StopPointInJourneyPatternRef | 0:1 | 0:1 | Alternative call location reference aligned to the underlying JourneyPattern. |
| ArrivalTime | xsd:time | 0:1 | 0:1 | Scheduled arrival time at the call (dayOffset may apply). |
| DepartureTime | xsd:time | 0:1 | 0:1 | Scheduled departure time at the call (dayOffset may apply). |

Notes
- Deprecated DatedServiceJourneyRef has been removed from this table. The profile uses replacedJourneys with DatedVehicleJourneyRef instead.
- ERP Cardinality cells are intentionally left blank for elements not present in at least one of the three maintained examples (MIN, ERP, NP). This reflects the requested rule to leave cardinality blank when an element is not present in an example, while keeping the XSD Cardinality for structural context.
