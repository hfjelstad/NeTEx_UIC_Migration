# Parking

## Structure Overview

```text
Parking
  ├─ @id (1..1)
  ├─ @version (1..1)
  ├─ Name (1..1)
  ├─ keyList (0..1)
  │  └─ KeyValue (0..*)
  ├─ Description (0..1)
  ├─ Centroid (0..1)
  │  └─ Location (1..1)
  │     ├─ Longitude (1..1)
  │     └─ Latitude (1..1)
  ├─ Covered (0..1)
  ├─ ParentSiteRef/@ref (0..1)
  ├─ ParkingType (0..1)
  ├─ ParkingVehicleTypes (0..1)
  ├─ ParkingLayout (0..1)
  ├─ TotalCapacity (0..1)
  ├─ RechargingAvailable (0..1)
  ├─ ParkingPaymentProcess (0..1)
  └─ parkingProperties (0..1)
     └─ ParkingProperties (0..*)
        └─ spaces (0..1)
           └─ ParkingCapacity (0..*)
              ├─ ParkingUserType (1..1)
              ├─ NumberOfSpaces (0..1)
              └─ NumberOfSpacesWithRechargePoint (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the parking facility | Parking/@id |
| @version | String | Version number for change tracking | Parking/@version |
| Name | String | Human-readable name of the parking facility | Parking/Name |
| keyList | Container | Arbitrary key/value metadata | Parking/keyList |
| KeyValue | Element | Key-value pair | Parking/keyList/KeyValue |
| Description | String | Free-text description of the parking facility | Parking/Description |
| Centroid | Element | Geographic location | Parking/Centroid |
| Location | Element | Coordinate container | Parking/Centroid/Location |
| Longitude | Decimal | WGS84 longitude | Parking/Centroid/Location/Longitude |
| Latitude | Decimal | WGS84 latitude | Parking/Centroid/Location/Latitude |
| Covered | Enum | Whether parking is covered (e.g., outdoors) | Parking/Covered |
| ParentSiteRef/@ref | Reference | Reference to the parent StopPlace | Parking/ParentSiteRef/@ref |
| ParkingType | Enum | Type of parking (e.g., parkAndRide, urbanParking) | Parking/ParkingType |
| ParkingVehicleTypes | String | Types of vehicles accepted (e.g., car, pedalCycle) | Parking/ParkingVehicleTypes |
| ParkingLayout | Enum | Layout of the parking (e.g., openSpace) | Parking/ParkingLayout |
| TotalCapacity | Integer | Total number of parking spaces | Parking/TotalCapacity |
| RechargingAvailable | Boolean | Whether electric vehicle recharging is available | Parking/RechargingAvailable |
| ParkingPaymentProcess | String | Payment process description | Parking/ParkingPaymentProcess |
| parkingProperties | Container | Collection of parking property definitions | Parking/parkingProperties |
| ParkingProperties | Element | Parking property definition | Parking/parkingProperties/ParkingProperties |
| spaces | Container | Collection of parking capacity definitions | Parking/parkingProperties/ParkingProperties/spaces |
| ParkingCapacity | Element | Capacity for a specific user type | Parking/parkingProperties/ParkingProperties/spaces/ParkingCapacity |
| ParkingUserType | Enum | User type (allUsers, registeredDisabled) | Parking/parkingProperties/ParkingProperties/spaces/ParkingCapacity/ParkingUserType |
| NumberOfSpaces | Integer | Number of parking spaces for this user type | Parking/parkingProperties/ParkingProperties/spaces/ParkingCapacity/NumberOfSpaces |
| NumberOfSpacesWithRechargePoint | Integer | Spaces with electric recharging | Parking/parkingProperties/ParkingProperties/spaces/ParkingCapacity/NumberOfSpacesWithRechargePoint |
