# TicketingEquipment

## Structure Overview

```text
TicketingEquipment
  ├─ @id (1..1)
  ├─ @version (1..1)
  └─ ValidBetween (0..1)
     ├─ FromDate (1..1)
     └─ ToDate (1..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the ticketing equipment | TicketingEquipment/@id |
| @version | String | Version number for change tracking | TicketingEquipment/@version |
| ValidBetween | Period | Validity period for the equipment | TicketingEquipment/ValidBetween |
| FromDate | DateTime | Start date of the validity period | TicketingEquipment/ValidBetween/FromDate |
| ToDate | DateTime | End date of the validity period | TicketingEquipment/ValidBetween/ToDate |
