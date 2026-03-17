# ShelterEquipment

## Structure Overview

```text
ShelterEquipment
  ├─ @id (1..1)
  ├─ @version (1..1)
  └─ ValidBetween (0..1)
     ├─ FromDate (1..1)
     └─ ToDate (1..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the shelter equipment | ShelterEquipment/@id |
| @version | String | Version number for change tracking | ShelterEquipment/@version |
| ValidBetween | Period | Validity period for the equipment | ShelterEquipment/ValidBetween |
| FromDate | DateTime | Start date of the validity period | ShelterEquipment/ValidBetween/FromDate |
| ToDate | DateTime | End date of the validity period | ShelterEquipment/ValidBetween/ToDate |
