# ServiceFrame

## 1. Purpose

A **ServiceFrame** contains the network and route definitions for a public transport delivery. It groups Lines, Routes, JourneyPatterns, ScheduledStopPoints, DestinationDisplays, and PassengerStopAssignments — the structural elements that describe where and how services run.

## 2. Contained Elements

- **lines** – Collection of [Line](../../Objects/Line/Table_Line.md) definitions describing transport services

## 3. Frame Relationships

ServiceFrame depends on **ResourceFrame** for Operator and Authority definitions referenced by Lines. **TimetableFrame** depends on ServiceFrame for JourneyPatterns and Lines used by ServiceJourneys. **SiteFrame** provides the physical stop infrastructure (StopPlaces, Quays) that PassengerStopAssignments link to. All frames are typically wrapped in a **CompositeFrame** within a PublicationDelivery.

For the full structural specification, see [Table — ServiceFrame](Table_ServiceFrame.md).
Example XML: [Example_ServiceFrame.xml](Example_ServiceFrame.xml)
