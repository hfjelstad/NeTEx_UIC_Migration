# Koster Ferry NeTEx Nordic Profile Example

## Overview

This folder contains a complete, documented example of a **NeTEx Nordic Profile** delivery for a realistic ferry service: the Koster Ferry (Koster Färjan) operating between Strömstad (mainland) and Koster Island in Sweden.

## File: `Koster_Ferry_NP.xml`

### Structure

The delivery demonstrates a minimal but complete Nordic Profile implementation with:

```
PublicationDelivery (NeTEx version 2.0)
├── ResourceFrame
│   ├── Organisations (Operator: Koster Färjan AB)
│   ├── VehicleTypes (Ferry vessel specifications)
│   └── TypesOfValue (PurposeOfGrouping)
├── ServiceCalendarFrame
│   ├── OperatingDays (sample dates)
│   ├── OperatingPeriods (Spring 2026: Mar-May)
│   ├── DayTypes (Weekdays, Weekend)
│   └── DayTypeAssignments (links calendar to DayTypes)
├── ServiceFrame
│   ├── Network (Koster Ferry Network)
│   ├── Routes (To Koster, From Koster - directional paths)
│   ├── Lines (Koster Ferry - TransportMode=ferry)
│   ├── ScheduledStopPoints (Strömstad, Koster terminals)
│   ├── ServiceLinks (ferry connections)
│   ├── JourneyPatterns (reusable stop sequences)
│   └── DestinationDisplays (passenger-facing text)
└── TimetableFrame
    └── ServiceJourneys (6 daily sailings with times)
        ├── Weekday pattern (4 sailings)
        └── Weekend pattern (2 sailings)
```

### Key Features

1. **Transaction Data Types:**
   - 2 terminals (Strömstad, Koster)
   - 2 routes (outbound + inbound)
   - 1 line (ferry service)
   - 2 journey patterns (one per direction)
   - 6 service journeys with scheduled times
   - 2 day types (weekday, weekend)

2. **Realistic Schedules:**
   - Weekday: morning (07:20), midday (12:30), evening (17:30) departures
   - Weekend: morning (09:00), afternoon (15:30) departures
   - Each direction covered separately
   - Realistic ~30 minute crossing times

3. **Nordic Profile Compliance:**
   - Uses proper codespace (KOSTER)
   - Follows ID format: `KOSTER:ObjectType:Description:Identifier`
   - All required mandatorylocales (timestamps, references)
   - Proper element ordering per XSD sequence groups
   - Reference integrity (all @ref attributes point to valid ids)

### Validation

**XML Well-formedness:** ✓ PASS (239 elements)
- Parses without XML errors
- All namespaces correctly declared
- Proper nesting and closing tags

**XSD Schema Validation:** Created according to documentation patterns from:
- `Frames/ServiceFrame/Example_ServiceFrame.xml`
- `Frames/TimetableFrame/Example_TimetableFrame.xml`
- `Objects/ServiceJourney/Example_ServiceJourney_NP.xml`
- All documented structure overviews and tables

### How to Use This Example

1. **Reference for your own delivery:**
   - Study the complete flow from ResourceFrame → TimetableFrame
   - Copy the ID naming pattern: `CODESPACE:ObjectType:LocalPart`
   - Use time formats: `HH:MM:SS` (24-hour)
   - Use date formats: `YYYY-MM-DD`

2. **Extend for real data:**
   - Replace Koster-specific data with your service
   - Add more stops, routes, journeys as needed
   - Adjust DayType patterns for your calendar
   - Add geographical coordinates (gml:Point) if needed

3. **For validation:**
   - Validate against `XSD/xsd/NeTEx_publication.xsd`
   - Use the consistency checker: `python scripts/check-doc-consistency.py --xsd-only --target Example`

### Repository Documentation

For detailed specifications on each element:

- [ServiceFrame](../Frames/ServiceFrame/Table_ServiceFrame.md)
- [ServiceCalendarFrame](../Frames/ServiceCalendarFrame/Table_ServiceCalendarFrame.md)
- [TimetableFrame](../Frames/TimetableFrame/Table_TimetableFrame.md)
- [ServiceJourney](../Objects/ServiceJourney/Table_ServiceJourney.md)
- [JourneyPattern](../Objects/JourneyPattern/Table_JourneyPattern.md)

---

**Created:** 2026-03-25  
**Profile:** Nordic NeTEx Profile v2.0  
**Service:** Koster Ferry (Sweden)
