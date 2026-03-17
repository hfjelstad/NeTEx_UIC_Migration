# VehicleScheduleFrame

## 1. Purpose

A **VehicleScheduleFrame** contains operational vehicle schedules — the blocks, vehicle services, and duty assignments that define how vehicles are allocated to journeys throughout the operating day.

## 2. Contained Elements

- **blocks** – Collection of block definitions grouping journeys assigned to a single vehicle:
  - [TrainBlock](../../Objects/TrainBlock/Table_TrainBlock.md) – Block specifically for train vehicle scheduling
- **vehicleServices** – Collection of VehicleService definitions describing a vehicle's complete service for a day

## 3. Frame Relationships

VehicleScheduleFrame depends on **TimetableFrame** for the ServiceJourneys and DatedServiceJourneys that blocks reference. It depends on **ResourceFrame** for Vehicle and VehicleType definitions. VehicleScheduleFrame is typically wrapped in a **CompositeFrame** within a PublicationDelivery.

For the full structural specification, see [Table — VehicleScheduleFrame](Table_VehicleScheduleFrame.md).
Example XML: [Example_VehicleScheduleFrame.xml](Example_VehicleScheduleFrame.xml)
