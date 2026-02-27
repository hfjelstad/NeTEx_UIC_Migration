# ServiceCalendarFrame

ServiceCalendarFrame contains the calendar model for a dataset. It defines which services run on which days by declaring:

- DayType objects that describe patterns of days (e.g., Weekdays, Weekend) via PropertyOfDay and DaysOfWeek.
- OperatingPeriod intervals with explicit UTC date-time boundaries.
- DayTypeAssignment records that link DayType to OperatingPeriod or specific OperatingDay, toggling availability via isAvailable.

Scope and usage

- The frame is typically embedded inside a CompositeFrame together with other frames (e.g., Timetable, ServiceFrame). References to DayType from journeys or blocks resolve within the same dataset (PublicationDelivery) and CompositeFrame.
- Codespace: All identifiers in this profile use the ERP codespace prefix (e.g., ERP:ServiceCalendarFrame:1).

Key rules and recommendations

- DaysOfWeek must use the NeTEx enumerations such as Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday, Weekdays, Weekend, Everyday, none. Multiple values may be space-separated when the type permits, but combined aliases like "MondayToFriday" are not allowed.
- FromDate and ToDate in OperatingPeriod must be xs:dateTime, including time and timezone (e.g., 2026-01-01T00:00:00Z).
- DayTypeAssignment should set isAvailable=true for operation days; use additional assignments with isAvailable=false for exceptions if needed.

Example

See Example_ServiceCalendarFrame.xml in this folder for a minimal, validated example using the ERP codespace.
