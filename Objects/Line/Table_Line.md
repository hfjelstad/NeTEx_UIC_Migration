## Structure Overview

```text
Line
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ TransportMode (1..1)
 ├─ TransportSubmode (0..1)
 │  ├─ BusSubmode (0..1)
 │  ├─ RailSubmode (0..1)
 │  ├─ WaterSubmode (0..1)
 │  ├─ TramSubmode (0..1)
 │  ├─ MetroSubmode (0..1)
 │  ├─ AirSubmode (0..1)
 │  ├─ CoachSubmode (0..1)
 │  └─ TelecabinSubmode (0..1)
 ├─ OperatorRef/@ref (1..1)
 ├─ PublicCode (0..1)
 ├─ PrivateCode (0..1)
 ├─ RepresentedByGroupRef/@ref (0..1)
 └─ Presentation (0..1)
    ├─ Colour (0..1)
    └─ TextColour (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the Line (e.g., ERP:Line:5) | Line/@id |
| @version | String | Version label | Line/@version |
| Name | String | Human-readable line name | Line/Name |
| TransportMode | Enum | Primary transport mode (bus, rail, water, tram, metro, air, coach, telecabin) | Line/TransportMode |
| TransportSubmode | Element | Transport submode container | Line/TransportSubmode |
| BusSubmode | Enum | Bus submode (localBus, regionalBus, expressBus, etc.) | Line/TransportSubmode/BusSubmode |
| RailSubmode | Enum | Rail submode (local, regionalRail, longDistance, etc.) | Line/TransportSubmode/RailSubmode |
| WaterSubmode | Enum | Water submode (localPassengerFerry, localCarFerry, etc.) | Line/TransportSubmode/WaterSubmode |
| TramSubmode | Enum | Tram submode (cityTram, localTram) | Line/TransportSubmode/TramSubmode |
| MetroSubmode | Enum | Metro submode | Line/TransportSubmode/MetroSubmode |
| AirSubmode | Enum | Air submode (domesticFlight, helicopterService) | Line/TransportSubmode/AirSubmode |
| CoachSubmode | Enum | Coach submode (internationalCoach, nationalCoach) | Line/TransportSubmode/CoachSubmode |
| TelecabinSubmode | Enum | Telecabin submode | Line/TransportSubmode/TelecabinSubmode |
| [Operator](../Operator/Table_Operator.md)@ref | Reference | Reference to the Operator running this Line | Line/OperatorRef/@ref |
| PublicCode | String | Public-facing line number or code | Line/PublicCode |
| PrivateCode | String | Internal non-public code | Line/PrivateCode |
| RepresentedByGroupRef/@ref | Reference | Reference to the Network or GroupOfLines this line belongs to | Line/RepresentedByGroupRef/@ref |
| Colour | String | Line colour as 6-digit uppercase hex (e.g., 005EB8) | Line/Presentation/Colour |
| TextColour | String | Text colour as 6-digit uppercase hex (e.g., FFFFFF) | Line/Presentation/TextColour |
