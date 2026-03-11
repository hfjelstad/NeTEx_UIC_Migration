# DatedServiceJourney – Elements Table

The table below summarises the DatedServiceJourney structure and the required/optional elements across MIN, ERP and NP profiles. Attribute rows are prefixed with @.

| Element | Type | MIN Cardinality | ERP Cardinality | NP Cardinality | Description |
|---|---|---:|---:|---:|---|
| DatedServiceJourney | element | 1..1 | 1..1 | 1..1 | Root element representing an operational run on a specific operating day. |
| @id | xs:string | 1..1 | 1..1 | 1..1 | Unique identifier in the publishing codespace. |
| @version | xs:integer | 1..1 | 1..1 | 1..1 | Version of the element. |
| ServiceJourneyRef | element | 1..1 | 1..1 | 1..1 | Reference to the planned ServiceJourney. |
| ServiceJourneyRef/@ref | xs:anyURI | 1..1 | 1..1 | 1..1 | Identifier of the referenced ServiceJourney. |
| OperatingDayRef | element | 1..1 | 1..1 | 1..1 | Reference to the OperatingDay for which this journey is valid. |
| OperatingDayRef/@ref | xs:anyURI | 1..1 | 1..1 | 1..1 | Identifier of the referenced OperatingDay. |
| DatedCalls | element | 1..1 | 1..1 | 1..1 | Container of dated calls (stop times) for this journey. |
| DatedCall | element | 1..* | 1..* | 1..* | A stop-specific timing instance on the dated journey. |
| StopPointInJourneyPatternRef | element | 1..1 | 1..1 | 1..1 | Reference to the StopPointInJourneyPattern that this call corresponds to. |
| StopPointInJourneyPatternRef/@ref | xs:anyURI | 1..1 | 1..1 | 1..1 | Identifier of the referenced StopPointInJourneyPattern. |
| AimedArrivalTime | xs:dateTime | 0..1 | 0..1 | 0..1 | Targeted arrival time at the stop for the dated journey. |
| AimedDepartureTime | xs:dateTime | 0..1 | 0..1 | 0..1 | Targeted departure time at the stop for the dated journey. |
| BlockRef | element | 0..0 | 0..1 | 0..1 | Link to the operational block this DatedServiceJourney is part of (when applicable). |
| BlockRef/@ref | xs:anyURI | 0..0 | 0..1 | 0..1 | Identifier of the referenced Block. |
