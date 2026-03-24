# ServiceFrame

> *→ [Glossary definition](../../Guides/Glossary/Glossary.md#serviceframe)*

## 1. Purpose

A **ServiceFrame** contains the network and route definitions for a public transport delivery. It groups Lines, Routes, JourneyPatterns, ScheduledStopPoints, DestinationDisplays, and PassengerStopAssignments — the structural elements that describe where and how services run.

## 2. Structure Overview

```text
📄 @id (1..1)
📄 @version (1..1)
📁 lines (0..1)
   └── 📄 Line (0..n)
📁 routes (0..1)
   └── 📄 Route (0..n)
📁 journeyPatterns (0..1)
   └── 📄 JourneyPattern (0..n)
📁 routePoints (0..1)
   └── 📄 RoutePoint (0..n)
📁 scheduledStopPoints (0..1)
   └── 📄 ScheduledStopPoint (0..n)
📁 serviceLinks (0..1)
   └── 📄 ServiceLink (0..n)
📁 stopAssignments (0..1)
   └── 📄 PassengerStopAssignment (0..n)
📁 destinationDisplays (0..1)
   └── 📄 DestinationDisplay (0..n)
📁 notices (0..1)
   └── 📄 Notice (0..n)
📄 Network (0..1)
```

## 3. Contained Elements

- **lines** – Collection of [Line](../../Objects/Line/Table_Line.md) definitions describing transport services
- **groupOfLines** – Collection of [GroupOfLines](../../Objects/GroupOfLines/Table_GroupOfLines.md) definitions grouping related lines together
- **routes** – Collection of [Route](../../Objects/Route/Table_Route.md) definitions describing the geographical course of a line
- **journeyPatterns** – Collection of [JourneyPattern](../../Objects/JourneyPattern/Table_JourneyPattern.md) definitions describing ordered sequences of stop points for journeys
- **scheduledStopPoints** – Collection of [ScheduledStopPoint](../../Objects/ScheduledStopPoint/Table_ScheduledStopPoint.md) definitions representing logical stop points in a schedule
- **stopAssignments** – Collection of [PassengerStopAssignment](../../Objects/PassengerStopAssignment/Table_PassengerStopAssignment.md) definitions linking ScheduledStopPoints to physical StopPlace/Quay
- **destinationDisplays** – Collection of [DestinationDisplay](../../Objects/DestinationDisplay/Table_DestinationDisplay.md) definitions describing destination text shown to passengers
- **notices** – Collection of [Notice](../../Objects/Notice/Table_Notice.md) definitions providing informational messages associated with services

## 4. Frame Relationships

ServiceFrame depends on **ResourceFrame** for Operator and Authority definitions referenced by Lines. **TimetableFrame** depends on ServiceFrame for JourneyPatterns and Lines used by ServiceJourneys. **SiteFrame** provides the physical stop infrastructure (StopPlaces, Quays) that PassengerStopAssignments link to. All frames are typically wrapped in a **CompositeFrame** within a PublicationDelivery.

For the full structural specification, see [Table — ServiceFrame](Table_ServiceFrame.md).
Example XML: [Example_ServiceFrame.xml](Example_ServiceFrame.xml)
