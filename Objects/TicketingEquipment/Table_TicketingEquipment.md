# TicketingEquipment

## Structure Overview

```text
TicketingEquipment
  ├─ @id (1..1)
  ├─ @version (1..1)
  ├─ VehicleModes (0..1)
  ├─ TicketMachines (0..1)
  ├─ NumberOfMachines (0..1)
  ├─ TicketingFacilityList (0..1)
  ├─ TicketOffice (0..1)
  ├─ PaymentMethods (0..1)
  ├─ TicketTypesAvailable (0..1)
  └─ ScopeOfTicketsAvailable (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the ticketing equipment | TicketingEquipment/@id |
| @version | String | Version number for change tracking | TicketingEquipment/@version |
| VehicleModes | String | Vehicle modes served by this equipment | TicketingEquipment/VehicleModes |
| TicketMachines | Boolean | Whether ticket machines are available | TicketingEquipment/TicketMachines |
| NumberOfMachines | Integer | Number of ticket machines | TicketingEquipment/NumberOfMachines |
| TicketingFacilityList | String | List of ticketing facilities | TicketingEquipment/TicketingFacilityList |
| TicketOffice | Boolean | Whether a staffed ticket office is present | TicketingEquipment/TicketOffice |
| PaymentMethods | String | Accepted payment methods | TicketingEquipment/PaymentMethods |
| TicketTypesAvailable | String | Types of tickets that can be purchased | TicketingEquipment/TicketTypesAvailable |
| ScopeOfTicketsAvailable | String | Scope of tickets available (local, regional, etc.) | TicketingEquipment/ScopeOfTicketsAvailable |
