# ShelterEquipment

## Structure Overview

```text
ShelterEquipment
  ├─ @id (1..1)
  ├─ @version (1..1)
  ├─ Seats (0..1)
  ├─ StepFree (0..1)
  └─ Enclosed (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the shelter equipment | ShelterEquipment/@id |
| @version | String | Version number for change tracking | ShelterEquipment/@version |
| Seats | Integer | Number of seats in the shelter | ShelterEquipment/Seats |
| StepFree | Boolean | Whether the shelter has step-free access | ShelterEquipment/StepFree |
| Enclosed | Boolean | Whether the shelter is enclosed | ShelterEquipment/Enclosed |
