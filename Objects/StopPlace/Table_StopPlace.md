## Structure Overview

```text
StopPlace (Monomodal)
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ TransportMode (1..1)
 ├─ StopPlaceType (0..1)
 ├─ TopographicPlaceRef/@ref (0..1)
 ├─ Centroid (0..1)
 ├─ tariffZones (0..n)
 └─ quays (1..n)

StopPlace (Multimodal Parent)
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
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
