## Structure Overview

```text
DayType
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ Description (0..1)
 └─ properties (0..1)
    └─ PropertyOfDay (0..n)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the DayType | DayType/@id |
| @version | String | Version label | DayType/@version |
| Name | String | Human-readable name of the day classification | DayType/Name |
| Description | String | Additional description of the DayType | DayType/Description |
| PropertyOfDay | Element | Operational characteristic of the day type | DayType/properties/PropertyOfDay |
