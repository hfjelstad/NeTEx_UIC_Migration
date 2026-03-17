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
 ├─ Description (0..1)
 ├─ PrivateCode (0..1)
 ├─ CompassBearing (0..1)
 ├─ AccessibilityAssessment (0..1)
 │  ├─ MobilityImpairedAccess (1..1)
 │  └─ limitations (0..1)
 │     └─ AccessibilityLimitation (1..n)
 │        ├─ WheelchairAccess (0..1)
 │        └─ StepFreeAccess (0..1)
 ├─ placeEquipments (0..1)
 └─ boardingPositions (0..1)
    └─ BoardingPosition (1..n)
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
| PrivateCode | String | Internal platform identifier (may have type attribute) | Quay/PrivateCode |
| CompassBearing | Decimal | Compass bearing of the quay in degrees (0-360) | Quay/CompassBearing |
| AccessibilityAssessment | Element | Accessibility evaluation of the quay | Quay/AccessibilityAssessment |
| MobilityImpairedAccess | Enum | Overall mobility access status (true, false, unknown) | Quay/AccessibilityAssessment/MobilityImpairedAccess |
| limitations | Container | Collection of specific accessibility limitations | Quay/AccessibilityAssessment/limitations |
| AccessibilityLimitation | Element | Specific accessibility limitation assessment | Quay/AccessibilityAssessment/limitations/AccessibilityLimitation |
| WheelchairAccess | Enum | Wheelchair accessibility (true, false, unknown) | Quay/AccessibilityAssessment/limitations/AccessibilityLimitation/WheelchairAccess |
| StepFreeAccess | Enum | Step-free access availability (true, false, unknown) | Quay/AccessibilityAssessment/limitations/AccessibilityLimitation/StepFreeAccess |
| placeEquipments | Container | Equipment installed at the quay | Quay/placeEquipments |
| boardingPositions | Container | Collection of boarding positions within the quay | Quay/boardingPositions |
| BoardingPosition | Element | Specific boarding position with location | Quay/boardingPositions/BoardingPosition |
