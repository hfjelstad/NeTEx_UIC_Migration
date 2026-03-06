| Element | Type (NeTEx) | XSD Cardinality | ERP Cardinality | Description |
|---|---|---|---|---|
| @id | xs:ID | 1 | 1 | Unique identifier of the DatedServiceJourney. |
| @version | Version | 1 | 1 | Version of the DatedServiceJourney. |
| ServiceJourneyRef | ServiceJourneyRefStructure | 1 | 1 | Reference to the planned ServiceJourney this instance derives from. |
| OperatingDayRef | OperatingDayRefStructure | 1 | 1 | Reference to the OperatingDay (service date). |
| LineRef | LineRefStructure | 0..1 | 0..1 | Reference to the Line operated by the journey. |
| BlockRef | BlockRefStructure | 0..1 | 0..1 | Reference to the vehicle Block linking consecutive journeys. |
| DatedCalls | DatedCallStructure | 1..* | 1..* | Sequence of stop calls for this dated journey. |
| DayTypeRef | DayTypeRefStructure | 0..* | 0..* | Reference to DayType(s) that additionally classify the journey (if used). |
