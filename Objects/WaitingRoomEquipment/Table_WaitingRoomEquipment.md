# WaitingRoomEquipment

## Structure Overview

```text
WaitingRoomEquipment
  ├─ @id (1..1)
  ├─ @version (1..1)
  └─ ValidBetween (0..1)
     ├─ FromDate (1..1)
     └─ ToDate (1..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the waiting room equipment | WaitingRoomEquipment/@id |
| @version | String | Version number for change tracking | WaitingRoomEquipment/@version |
| ValidBetween | Period | Validity period for the equipment | WaitingRoomEquipment/ValidBetween |
| FromDate | DateTime | Start date of the validity period | WaitingRoomEquipment/ValidBetween/FromDate |
| ToDate | DateTime | End date of the validity period | WaitingRoomEquipment/ValidBetween/ToDate |
