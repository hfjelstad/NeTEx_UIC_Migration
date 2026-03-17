# ServiceCalendarFrame

## Structure Overview

```text
ServiceCalendarFrame
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ dayTypes (0..1)
 │   └─ DayType (0..n)
 │       ├─ Name (0..1)
 │       └─ properties (0..1)
 │           └─ PropertyOfDay (0..n)
 │               └─ DaysOfWeek (0..1)
 ├─ operatingPeriods (0..1)
 │   └─ OperatingPeriod (0..n)
 │       ├─ FromDate (1..1)
 │       └─ ToDate (1..1)
 └─ dayTypeAssignments (0..1)
     └─ DayTypeAssignment (0..n)
         ├─ @order (0..1)
         ├─ OperatingPeriodRef/@ref (0..1)
         ├─ Date (0..1)
         ├─ DayTypeRef/@ref (1..1)
         └─ isAvailable (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the ServiceCalendarFrame | ServiceCalendarFrame/@id |
| @version | String | Version number for change tracking | ServiceCalendarFrame/@version |
| dayTypes | Container | Collection of day type definitions | ServiceCalendarFrame/dayTypes |
| [DayType](../../Objects/DayType/Table_DayType.md) | Element | Reusable day pattern (e.g., Weekdays, Weekend) | ServiceCalendarFrame/dayTypes/DayType |
| Name | String | Human-readable name of the day type | ServiceCalendarFrame/dayTypes/DayType/Name |
| properties | Container | Collection of day properties | ServiceCalendarFrame/dayTypes/DayType/properties |
| PropertyOfDay | Element | Day-of-week specification | ServiceCalendarFrame/dayTypes/DayType/properties/PropertyOfDay |
| DaysOfWeek | String | Space-separated list of day names | ServiceCalendarFrame/dayTypes/DayType/properties/PropertyOfDay/DaysOfWeek |
| operatingPeriods | Container | Collection of operating period definitions | ServiceCalendarFrame/operatingPeriods |
| OperatingPeriod | Element | Date-time window of validity | ServiceCalendarFrame/operatingPeriods/OperatingPeriod |
| FromDate | DateTime | Start of the operating period | ServiceCalendarFrame/operatingPeriods/OperatingPeriod/FromDate |
| ToDate | DateTime | End of the operating period | ServiceCalendarFrame/operatingPeriods/OperatingPeriod/ToDate |
| dayTypeAssignments | Container | Collection of day type assignment definitions | ServiceCalendarFrame/dayTypeAssignments |
| DayTypeAssignment | Element | Binds a DayType to a period or date | ServiceCalendarFrame/dayTypeAssignments/DayTypeAssignment |
| @order | Integer | Evaluation order for overlapping assignments | ServiceCalendarFrame/dayTypeAssignments/DayTypeAssignment/@order |
| OperatingPeriodRef/@ref | Reference | Reference to an OperatingPeriod | ServiceCalendarFrame/dayTypeAssignments/DayTypeAssignment/OperatingPeriodRef/@ref |
| Date | Date | Specific date for the assignment | ServiceCalendarFrame/dayTypeAssignments/DayTypeAssignment/Date |
| DayTypeRef/@ref | Reference | Reference to a DayType | ServiceCalendarFrame/dayTypeAssignments/DayTypeAssignment/DayTypeRef/@ref |
| isAvailable | Boolean | Whether the day type is available (false for exceptions) | ServiceCalendarFrame/dayTypeAssignments/DayTypeAssignment/isAvailable |
