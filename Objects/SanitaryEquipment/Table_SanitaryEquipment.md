# SanitaryEquipment

## Structure Overview

```text
SanitaryEquipment
  ├─ @id (1..1)
  ├─ @version (1..1)
  ├─ Gender (0..1)
  ├─ SanitaryFacilityList (0..1)
  ├─ NumberOfToilets (0..1)
  └─ PaymentMethods (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the sanitary equipment | SanitaryEquipment/@id |
| @version | String | Version number for change tracking | SanitaryEquipment/@version |
| Gender | Enum | Gender designation (e.g., both, male, female) | SanitaryEquipment/Gender |
| SanitaryFacilityList | String | List of sanitary facilities available | SanitaryEquipment/SanitaryFacilityList |
| NumberOfToilets | Integer | Total number of toilets | SanitaryEquipment/NumberOfToilets |
| PaymentMethods | String | Accepted payment methods | SanitaryEquipment/PaymentMethods |
