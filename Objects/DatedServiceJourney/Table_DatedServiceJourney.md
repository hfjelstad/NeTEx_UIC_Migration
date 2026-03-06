| Element | Description | Cardinality | NeTEx Type | Example |
|---|---|---|---|---|
| @id | Unique identifier of the DatedServiceJourney. | 1 | xs:ID | ERP:DSJ:12345 |
| @version | Version of the DatedServiceJourney. | 1 | Version | any |
| ServiceJourneyRef | Reference to the planned ServiceJourney this instance derives from. | 1 | ServiceJourneyRefStructure | ERP:SJ:67890 |
| OperatingDayRef | Reference to the OperatingDay (service date). | 1 | OperatingDayRefStructure | ERP:OD:2025-03-01 |
| LineRef | Reference to the Line operated by the journey. | 0..1 | LineRefStructure | ERP:Line:10 |
| BlockRef | Reference to the vehicle Block linking consecutive journeys. | 0..1 | BlockRefStructure | ERP:Block:55 |
| DatedCalls | Sequence of stop calls for this dated journey. | 1..* | DatedCallStructure | — |
| DayTypeRef | Reference to DayType(s) that additionally classify the journey (if used). | 0..* | DayTypeRefStructure | ERP:DT:WEEKDAY |
