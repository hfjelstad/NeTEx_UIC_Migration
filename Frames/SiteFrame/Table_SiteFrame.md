# SiteFrame

## Structure Overview

```text
SiteFrame
 ├─ @id (1..1)
 ├─ @version (1..1)
 └─ stopPlaces (0..1)
     └─ StopPlace (0..n)
         ├─ Name (0..1)
         └─ quays (0..1)
             └─ Quay (0..n)
                 └─ Name (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the SiteFrame | SiteFrame/@id |
| @version | String | Version number for change tracking | SiteFrame/@version |
| stopPlaces | Container | Collection of stop place definitions | SiteFrame/stopPlaces |
| [StopPlace](../../Objects/StopPlace/Table_StopPlace.md) | Element | Physical stop location with quays | SiteFrame/stopPlaces/StopPlace |
| Name | String | Name of the stop place | SiteFrame/stopPlaces/StopPlace/Name |
| quays | Container | Collection of quays within a stop place | SiteFrame/stopPlaces/StopPlace/quays |
| [Quay](../../Objects/Quay/Table_Quay.md) | Element | Individual boarding/alighting point | SiteFrame/stopPlaces/StopPlace/quays/Quay |
| Name | String | Name of the quay | SiteFrame/stopPlaces/StopPlace/quays/Quay/Name |
