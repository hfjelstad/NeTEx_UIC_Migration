# SanitaryEquipment

## Structure Overview

```text
SanitaryEquipment
  ├─ @id (1..1)
  ├─ @version (1..1)
  └─ ValidBetween (0..1)
     ├─ FromDate (1..1)
     └─ ToDate (1..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the sanitary equipment | SanitaryEquipment/@id |
| @version | String | Version number for change tracking | SanitaryEquipment/@version |
| ValidBetween | Period | Validity period for the equipment | SanitaryEquipment/ValidBetween |
| FromDate | DateTime | Start date of the validity period | SanitaryEquipment/ValidBetween/FromDate |
| ToDate | DateTime | End date of the validity period | SanitaryEquipment/ValidBetween/ToDate |
