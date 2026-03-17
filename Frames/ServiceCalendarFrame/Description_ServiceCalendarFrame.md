# ServiceCalendarFrame

## 1. Purpose

A **ServiceCalendarFrame** groups calendar definitions that describe when services operate. It provides reusable day patterns, operating periods, and day-type assignments that TimetableFrame journeys reference to determine their days of operation.

## 2. Structure Overview

```text
📄 @id (1..1)
📄 @version (1..1)
📁 dayTypes (0..1)
   └── 📄 DayType (0..n)
       ├── 📄 Name (0..1)
       └── 📁 properties (0..1)
           └── 📄 PropertyOfDay (0..n)
               └── 📄 DaysOfWeek (0..1)
📁 operatingPeriods (0..1)
   └── 📄 OperatingPeriod (0..n)
       ├── 📄 FromDate (1..1)
       └── 📄 ToDate (1..1)
📁 dayTypeAssignments (0..1)
   └── 📄 DayTypeAssignment (0..n)
       ├── 🔗 OperatingPeriodRef/@ref (0..1)
       ├── 📄 Date (0..1)
       ├── 🔗 DayTypeRef/@ref (1..1)
       └── 📄 isAvailable (0..1)
```

## 3. Contained Elements

- **dayTypes** – Collection of [DayType](../../Objects/DayType/Table_DayType.md) definitions describing reusable day patterns (e.g., Weekdays, Weekend) with DaysOfWeek properties
- **operatingPeriods** – Collection of OperatingPeriod definitions specifying date-time windows (FromDate/ToDate) during which services apply
- **dayTypeAssignments** – Collection of DayTypeAssignment definitions binding DayTypes to OperatingPeriods or specific dates, with isAvailable to include/exclude days

## 4. Frame Relationships

ServiceCalendarFrame is referenced by **TimetableFrame** — ServiceJourneys use DayTypeRef to determine their operating days. It is independent of ServiceFrame and SiteFrame but must be present in the same CompositeFrame as the TimetableFrame that references its DayTypes.

## 5. Usage Notes

- DayTypeAssignments can reference either an OperatingPeriodRef (for date ranges) or a specific Date element (for individual days).
- Use `isAvailable` set to `false` on a DayTypeAssignment to create exception dates (e.g., public holidays).
- The `order` attribute on DayTypeAssignment controls evaluation order when multiple assignments overlap.

For the full structural specification, see [Table — ServiceCalendarFrame](Table_ServiceCalendarFrame.md).
Example XML: [Example_ServiceCalendarFrame.xml](Example_ServiceCalendarFrame.xml)
