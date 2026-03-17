## Structure Overview

```text
PassengerStopAssignment
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ @order (1..1)
 ├─ ScheduledStopPointRef/@ref (1..1)
 ├─ QuayRef/@ref (1..1)
 ├─ StopPlaceRef/@ref (0..1)
 ├─ ForDatedVehicleJourneyRef/@ref (0..1)
 └─ ValidBetween (0..1)
    └─ FromDate (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the assignment | PassengerStopAssignment/@id |
| @version | String | Version label | PassengerStopAssignment/@version |
| @order | Integer | Technical sequence number | PassengerStopAssignment/@order |
| [ScheduledStopPoint](../ScheduledStopPoint/Table_ScheduledStopPoint.md)@ref | Reference | Reference to the logical timetable stop | PassengerStopAssignment/ScheduledStopPointRef/@ref |
| [Quay](../Quay/Table_Quay.md)@ref | Reference | Reference to the physical boarding platform | PassengerStopAssignment/QuayRef/@ref |
| [StopPlace](../StopPlace/Table_StopPlace.md)@ref | Reference | Reference to the parent stop location | PassengerStopAssignment/StopPlaceRef/@ref |
| [DatedServiceJourney](../DatedServiceJourney/Table_DatedServiceJourney.md)@ref | Reference | Override assignment for a specific dated journey | PassengerStopAssignment/ForDatedVehicleJourneyRef/@ref |
| ValidBetween | Period | Validity period for the assignment | PassengerStopAssignment/ValidBetween |
| FromDate | DateTime | Start date of validity | PassengerStopAssignment/ValidBetween/FromDate |
