## Structure Overview

```text
ScheduledStopPoint
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (0..1)
 └─ TimingPointStatus (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the ScheduledStopPoint | ScheduledStopPoint/@id |
| @version | String | Version label | ScheduledStopPoint/@version |
| Name | String | Human-readable name of the stop point | ScheduledStopPoint/Name |
| TimingPointStatus | Enum | Whether this is a timing point (timingPoint, notTimingPoint) | ScheduledStopPoint/TimingPointStatus |
