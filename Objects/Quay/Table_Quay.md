## Structure Overview

```text
Quay
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ PublicCode (0..1)
 ├─ StopPlaceRef/@ref (1..1)
 ├─ Centroid (1..1)
 │  └─ Location (1..1)
 │     ├─ Longitude (1..1)
 │     └─ Latitude (1..1)
 └─ Description (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the Quay (e.g., ERP:Quay:1001) | Quay/@id |
| @version | String | Version label | Quay/@version |
| Name | String | Passenger-facing quay name | Quay/Name |
| PublicCode | String | Short public code printed on signage | Quay/PublicCode |
| [StopPlace](../StopPlace/Table_StopPlace.md)@ref | Reference | Reference to parent StopPlace | Quay/StopPlaceRef/@ref |
| Longitude | Decimal | WGS84 longitude | Quay/Centroid/Location/Longitude |
| Latitude | Decimal | WGS84 latitude | Quay/Centroid/Location/Latitude |
| Description | String | Optional free-text description | Quay/Description |
