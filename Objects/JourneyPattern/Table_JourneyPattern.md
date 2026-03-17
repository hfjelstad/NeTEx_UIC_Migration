## Structure Overview

```text
JourneyPattern
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (0..1)
 ├─ RouteRef/@ref (1..1)
 ├─ DirectionType (0..1)
 └─ pointsInSequence (1..1)
    └─ StopPointInJourneyPattern (1..n)
       ├─ @id (1..1)
       ├─ @version (1..1)
       ├─ @order (1..1)
       └─ ScheduledStopPointRef/@ref (1..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the JourneyPattern | JourneyPattern/@id |
| @version | String | Version label | JourneyPattern/@version |
| Name | String | Human-readable name of the pattern variant | JourneyPattern/Name |
| [Route](../Route/Table_Route.md)@ref | Reference | Reference to the Route this pattern belongs to | JourneyPattern/RouteRef/@ref |
| DirectionType | Enum | Direction classifier (inbound, outbound, clockwise, anticlockwise) | JourneyPattern/DirectionType |
| StopPointInJourneyPattern/@id | ID | Unique identifier for the stop point entry | JourneyPattern/pointsInSequence/StopPointInJourneyPattern/@id |
| StopPointInJourneyPattern/@version | String | Version label | JourneyPattern/pointsInSequence/StopPointInJourneyPattern/@version |
| StopPointInJourneyPattern/@order | Integer | Sequential position in the stop sequence (1, 2, 3...) | JourneyPattern/pointsInSequence/StopPointInJourneyPattern/@order |
| [ScheduledStopPoint](../ScheduledStopPoint/Table_ScheduledStopPoint.md)@ref | Reference | Reference to the logical stop point | JourneyPattern/pointsInSequence/StopPointInJourneyPattern/ScheduledStopPointRef/@ref |
