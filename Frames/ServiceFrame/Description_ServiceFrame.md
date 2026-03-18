# ServiceFrame

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

## 4. Frame Relationships

ServiceFrame depends on **ResourceFrame** for Operator and Authority definitions referenced by Lines. **TimetableFrame** depends on ServiceFrame for JourneyPatterns and Lines used by ServiceJourneys. **SiteFrame** provides the physical stop infrastructure (StopPlaces, Quays) that PassengerStopAssignments link to. All frames are typically wrapped in a **CompositeFrame** within a PublicationDelivery.

For the full structural specification, see [Table — ServiceFrame](Table_ServiceFrame.md).
Example XML: [Example_ServiceFrame.xml](Example_ServiceFrame.xml)
