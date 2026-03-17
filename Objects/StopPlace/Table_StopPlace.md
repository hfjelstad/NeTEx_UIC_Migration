## Structure Overview

```text
StopPlace (Monomodal)
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ Description (0..1)
 ├─ PrivateCode (0..1)
 ├─ TransportMode (1..1)
 ├─ OtherTransportModes (0..1)
 ├─ StopPlaceType (0..1)
 ├─ Weighting (0..1)
 ├─ TopographicPlaceRef/@ref (0..1)
 ├─ Centroid (0..1)
 ├─ AccessibilityAssessment (0..1)
 │  ├─ MobilityImpairedAccess (1..1)
 │  └─ limitations (0..1)
 │     └─ AccessibilityLimitation (1..n)
 │        ├─ WheelchairAccess (0..1)
 │        └─ StepFreeAccess (0..1)
 ├─ placeEquipments (0..1)
 ├─ tariffZones (0..n)
 ├─ adjacentSites (0..1)
 │  └─ SiteRef/@ref (1..n)
 └─ quays (1..n)

StopPlace (Multimodal Parent)
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ Description (0..1)
 ├─ TopographicPlaceRef/@ref (0..1)
 └─ (NO quays; NO TransportMode)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier (e.g., ERP:StopPlace:1001) | StopPlace/@id |
| @version | String | Version number | StopPlace/@version |
| @created | DateTime | Creation date | StopPlace/@created |
| @changed | DateTime | Last modification date | StopPlace/@changed |
| @modification | String | Modification type (e.g., delete for decommissioning) | StopPlace/@modification |
| Name | String | Name of the stop place | StopPlace/Name |
| AlternativeName | String | Alternative names or aliases | StopPlace/alternativeNames/AlternativeName |
| TransportMode | Enum | Primary mode (bus, rail, metro, tram, water, etc.) | StopPlace/TransportMode |
| BusSubmode / RailSubmode / ... | Enum | Optional submode category | StopPlace/BusSubmode |
| StopPlaceType | Enum | Functional type (onstreetBus, railStation, metroStation, busStation, etc.) | StopPlace/StopPlaceType |
| [TopographicPlace](../TopographicPlace/Table_TopographicPlace.md)@ref | Reference | Reference to city or region | StopPlace/TopographicPlaceRef/@ref |
| ParentSiteRef/@ref | Reference | Reference to multimodal parent StopPlace | StopPlace/ParentSiteRef/@ref |
| KeyValue | KeyValue | Alternative keys (e.g., external IDs) | StopPlace/keyList/KeyValue |
| Centroid | Location | Geographic point representation | StopPlace/Centroid/Location |
| TariffZoneRef/@ref | Reference | References to tariff zones | StopPlace/tariffZones/TariffZoneRef/@ref |
| [Quay](../Quay/Table_Quay.md) | Quay | Boarding/alighting positions (not on multimodal parent) | StopPlace/quays/Quay |
| ValidBetween | Period | Validity period (FromDate, ToDate) | StopPlace/ValidBetween |
| Description | String | Free-text description of the stop place | StopPlace/Description |
| PrivateCode | String | Internal identifier code | StopPlace/PrivateCode |
| Weighting | Enum | Interchange weighting (e.g., interchangeAllowed) | StopPlace/Weighting |
| OtherTransportModes | String | Additional transport modes served | StopPlace/OtherTransportModes |
| AccessibilityAssessment | Element | Accessibility evaluation of the stop place | StopPlace/AccessibilityAssessment |
| MobilityImpairedAccess | Enum | Overall mobility access status (true, false, unknown) | StopPlace/AccessibilityAssessment/MobilityImpairedAccess |
| limitations | Container | Collection of specific accessibility limitations | StopPlace/AccessibilityAssessment/limitations |
| AccessibilityLimitation | Element | Specific accessibility limitation assessment | StopPlace/AccessibilityAssessment/limitations/AccessibilityLimitation |
| WheelchairAccess | Enum | Wheelchair accessibility (true, false, unknown) | StopPlace/AccessibilityAssessment/limitations/AccessibilityLimitation/WheelchairAccess |
| StepFreeAccess | Enum | Step-free access availability (true, false, unknown) | StopPlace/AccessibilityAssessment/limitations/AccessibilityLimitation/StepFreeAccess |
| placeEquipments | Container | Equipment installed at the stop place | StopPlace/placeEquipments |
| adjacentSites | Container | References to adjacent stop places | StopPlace/adjacentSites |
| SiteRef/@ref | Reference | Reference to an adjacent StopPlace | StopPlace/adjacentSites/SiteRef/@ref |
