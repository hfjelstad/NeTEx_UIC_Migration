# DestinationDisplay

## Structure Overview

```text
DestinationDisplay
  ├─ @id (1..1)
  ├─ @version (1..1)
  ├─ Name (0..1)
  ├─ FrontText (1..1)
  └─ SideText (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the destination display | DestinationDisplay/@id |
| @version | String | Version number for change tracking | DestinationDisplay/@version |
| Name | String | Internal name for the destination display definition | DestinationDisplay/Name |
| FrontText | String | Text shown on the vehicle's destination display | DestinationDisplay/FrontText |
| SideText | String | Text shown on the side display of a vehicle | DestinationDisplay/SideText |
