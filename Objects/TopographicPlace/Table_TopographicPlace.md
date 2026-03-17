# TopographicPlace

## Structure Overview

```text
TopographicPlace
  ├─ @id (1..1)
  ├─ @version (1..1)
  ├─ Descriptor (1..1)
  │  ├─ Name (1..1)
  │  └─ ShortName (0..1)
  ├─ TopographicPlaceType (0..1)
  └─ CountryRef/@ref (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the topographic place | TopographicPlace/@id |
| @version | String | Version number for change tracking | TopographicPlace/@version |
| Descriptor | Element | Container for name information | TopographicPlace/Descriptor |
| Name | String | Full name of the geographic area | TopographicPlace/Descriptor/Name |
| ShortName | String | Abbreviated name of the geographic area | TopographicPlace/Descriptor/ShortName |
| TopographicPlaceType | Enum | Classification of the area (e.g., city, municipality, county) | TopographicPlace/TopographicPlaceType |
| CountryRef/@ref | Reference | ISO country code reference (e.g., no) | TopographicPlace/CountryRef/@ref |
