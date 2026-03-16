# Table: DatedServiceJourney 

## Structural Overview

This overview shows the primary relationships of DatedServiceJourney and where the referenced objects are documented.

```
DatedServiceJourney
├─ ServiceJourneyRef (1) → ServiceJourney
├─ OperatingPeriodRef (0..1) → OperatingPeriod
├─ DayTypeRef (0..*) → DayType
├─ BlockRef (0..1) → TrainBlock
└─ ResponsibilitySetRef (0..1) → ResponsibilitySet
```

Related object documentation:
- [ServiceJourney](../ServiceJourney/Description_ServiceJourney.md)
- [OperatingPeriod](../OperatingPeriod/Description_OperatingPeriod.md)
- [DayType](../DayType/Description_DayType.md)
- [TrainBlock](../TrainBlock/Description_TrainBlock.md)
- [ResponsibilitySet](../ResponsibilitySet/Description_ResponsibilitySet.md)

| Element | Type | MIN | ERP | NP | Description |
|---|---|---|---|---|---|
| @id | xsd:NMTOKEN | 1..1 | 1..1 | 1..1 | Unique identifier for the dated journey instance. |
| @version | xsd:integer | 1..1  | 1..1 | 1..1 | Version number of the object. |
| ServiceJourneyRef | ServiceJourneyRef | 1..1 | 1..1 | 1..1 | Reference to the underlying ServiceJourney template. |
| OperatingDayRef | OperatingDayRef | 1..1 | 1..1 | 1..1 | Reference to the OperatingDay that anchors the date of operation. |
| BlockRef | BlockRef |  | 0..1 | 0..1 | Reference to an operational Block/TrainBlock. |
| ServiceAlteration | ServiceAlterationEnumeration |  | 0..1 | 0..1 | Planned/replaced/extraJourney; omitted implies planned. |
| replacedJourneys | replacedJourneys |  |  | 0..1 | Container for references to journeys being replaced or reinforced. |
| replacedJourneys/DatedVehicleJourneyRef | DatedVehicleJourneyRef |  |  | 0..* | Reference(s) to dated journey(ies) being replaced/reinforced. |
