# WaitingRoomEquipment

## Structure Overview

```text
WaitingRoomEquipment
  ├─ @id (1..1)
  ├─ @version (1..1)
  ├─ Seats (0..1)
  ├─ StepFree (0..1)
  ├─ Heated (0..1)
  └─ Sanitary (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the waiting room equipment | WaitingRoomEquipment/@id |
| @version | String | Version number for change tracking | WaitingRoomEquipment/@version |
| Seats | Integer | Number of seats in the waiting room | WaitingRoomEquipment/Seats |
| StepFree | Boolean | Whether the waiting room has step-free access | WaitingRoomEquipment/StepFree |
| Heated | Boolean | Whether the waiting room is heated | WaitingRoomEquipment/Heated |
| Sanitary | String | Sanitary facility description | WaitingRoomEquipment/Sanitary |
