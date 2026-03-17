# TicketingEquipment

## 1. Purpose

The **TicketingEquipment** describes ticket machines, validators, or other ticketing infrastructure available at a stop place or station. It communicates the availability and validity of ticketing facilities to passengers and journey planners.

## 2. Structure Overview

```
📄 TicketingEquipment
  ├─ 📄 @id (1..1)
  ├─ 📄 @version (1..1)
  └─ 📁 ValidBetween (0..1)
     ├─ 📄 FromDate (1..1)
     └─ 📄 ToDate (1..1)
```

## 3. Key Elements

- **@id**: Unique identifier following the `{CODESPACE}:TicketingEquipment:{LocalId}` pattern.
- **@version**: Version number for tracking changes.
- **ValidBetween**: Defines the period during which the ticketing equipment is available, useful for temporary installations or maintenance periods.

## 4. References

- [StopPlace](../StopPlace/Table_StopPlace.md) -- ticketing equipment is typically located at a StopPlace.
- [Quay](../Quay/Table_Quay.md) -- ticket machines may be accessible from specific quays.

## 5. Usage Notes

### 5a. Consistency Rules

- TicketingEquipment should only be defined for locations where ticketing facilities actually exist.
- When ValidBetween is used, `FromDate` must precede `ToDate`.

### 5b. Validation Requirements

- **@id is mandatory** -- must follow the NeTEx identifier pattern.
- **@version is mandatory** -- must be provided for change tracking.
- **FromDate must precede ToDate** -- when ValidBetween is present.

### 5c. Common Pitfalls

- **Confusing equipment types**: TicketingEquipment is specifically for ticket machines and validators; do not use it for general passenger information displays.
- **Omitting validity periods during maintenance**: Use ValidBetween when equipment is temporarily out of service.

## 6. Additional Information

See [Table_TicketingEquipment.md](Table_TicketingEquipment.md) for detailed attribute specifications.

Example XML: [TicketingEquipment.xml](TicketingEquipment.xml)
