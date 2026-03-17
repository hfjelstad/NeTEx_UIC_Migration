## Structure Overview

```text
Route
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ ShortName (0..1)
 ├─ PublicCode (0..1)
 ├─ Description (0..1)
 ├─ PrivateCode (0..1)
 ├─ LineRef/@ref (1..1)
 ├─ DirectionType (0..1)
 └─ PointsInSequence (1..1)
    └─ PointOnRoute (1..n)
       ├─ @order (1..1)
       └─ ScheduledStopPointRef/@ref (1..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the Route | Route/@id |
| @version | String | Version label | Route/@version |
| Name | String | Display name for the route | Route/Name |
| ShortName | String | Short name or number | Route/ShortName |
| PublicCode | String | Public-facing code or number | Route/PublicCode |
| Description | String | Extended description | Route/Description |
| PrivateCode | String | Internal code | Route/PrivateCode |
| [Line](../Line/Table_Line.md)@ref | Reference | Reference to the Line this route belongs to | Route/LineRef/@ref |
| DirectionType | Enum | Direction indicator (inbound, outbound, clockwise, counterclockwise) | Route/DirectionType |
| @order | Integer | Sequence number for the point in the route | Route/pointsInSequence/PointOnRoute/@order |
| [ScheduledStopPoint](../ScheduledStopPoint/Table_ScheduledStopPoint.md)@ref | Reference | Reference to a ScheduledStopPoint | Route/pointsInSequence/PointOnRoute/ScheduledStopPointRef/@ref |
