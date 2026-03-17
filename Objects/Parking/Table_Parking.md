# Parking

## Structure Overview

```text
Parking
  ├─ @id (1..1)
  ├─ @version (1..1)
  ├─ Name (1..1)
  └─ ParkingType (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the parking facility | Parking/@id |
| @version | String | Version number for change tracking | Parking/@version |
| Name | String | Human-readable name of the parking facility | Parking/Name |
| ParkingType | Enum | Type of parking (e.g., parkAndRide, urbanParking) | Parking/ParkingType |
