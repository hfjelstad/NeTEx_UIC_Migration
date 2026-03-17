# ServiceJourney

## 1. Purpose

A **ServiceJourney** represents a planned trip in the timetable operating on a recurring schedule. It defines the stop sequence via reference to a JourneyPattern, includes scheduled passing times, and specifies operational details such as operator and days of operation. Unlike DatedServiceJourney, which represents a concrete instance on a specific date, ServiceJourney is the reusable template used across multiple dates via DayType definitions.

## 2. Structure Overview

```text
📄 @id
📄 @version
📄 Name
📄 PrivateCode
📁 TransportMode
📁 TransportSubmode
🔗 JourneyPatternRef/@ref
🔗 LineRef/@ref
🔗 OperatorRef/@ref
📁 dayTypes
   └── 🔗 DayTypeRef/@ref (0..*)
📁 passingTimes
   └── 📄 TimetabledPassingTime (1..*)
       ├── 🔗 StopPointInJourneyPatternRef/@ref
       ├── 📄 ArrivalTime
       ├── 📄 DepartureTime
       └── 📄 ArrivalDayOffset / DepartureDayOffset
📄 KeyValue (0..*)
🔗 BlockRef/@ref
```

## 3. Key Elements

- **@id, @version** – Unique identifier and version label
- **JourneyPatternRef** – Reference to the stop sequence (mandatory; defines which stops are served)
- **passingTimes** – Collection of TimetabledPassingTime with ArrivalTime and DepartureTime for each stop
- **dayTypes** – DayType references specifying on which days the journey normally operates
- **OperatorRef** – Reference to the Operator responsible for this journey
- **LineRef** – Reference to the served Line
- **BlockRef** – Optional reference to a Block/TrainBlock for vehicle continuity

## 4. References

- [JourneyPattern](../JourneyPattern/Table_JourneyPattern.md) – Provides the authoritative stop sequence
- [DayType](../DayType/Table_DayType.md) – Specifies operational days
- [Operator](../Operator/Table_Operator.md) – Identifies the service provider
- [Line](../Line/Table_Line.md) – The public transport line being served
- [DatedServiceJourney](../DatedServiceJourney/Description_DatedServiceJourney.md) – Per-date instances and alterations of this journey
- [Block](../Block/Table_Block.md) – Optional vehicle/roster grouping

## 5. Usage Notes

- **Template vs. Instance:** ServiceJourney is the template; DatedServiceJourney represents concrete daily instances.
- **Consistency:** A ServiceJourney must reference exactly one JourneyPattern. The pattern's stop sequence is authoritative.
- **Stop Times:** Each stop in the referenced JourneyPattern must have exactly one TimetabledPassingTime entry with ArrivalTime and/or DepartureTime.
- **Day Governance:** DayType references control on which days the journey operates; per-date deviations belong to DatedServiceJourney.
- **Validation:** Ensure journeyPatternRef, lineRef, and operatorRef are consistent and reference existing objects.

## 6. Additional Information

For a complete list of all elements, attributes, cardinalities, and data types, see [Table — ServiceJourney](Table_ServiceJourney.md).

Example XML: [Example_ServiceJourney.xml](Example_ServiceJourney.xml) and [Example_ServiceJourney_MIN.xml](Example_ServiceJourney_MIN.xml)
