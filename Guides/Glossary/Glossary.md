# Glossary

Core terms used in this NeTEx profile, organised alphabetically.
Each entry gives a short definition and a link to the full documentation.

<!-- entur-terms-ready: format maps to SKOS prefLabel + definition -->

---

## AlternativeName

Additional name variant for a NeTEx object - such as an official registration, translation, or abbreviation.

→ [Full documentation](../../Objects/AlternativeName/Description_AlternativeName.md)

---

## AlternativeText

Supplementary textual description attached to any NeTEx object.

→ [Full documentation](../../Objects/AlternativeText/Description_AlternativeText.md)

---

## Authority

A public transport organisation responsible for planning, organising, and managing public transport services within a specific geographical area.

→ [Full documentation](../../Objects/Authority/Description_Authority.md)

---

## Codespace

The namespace definition used for all NeTEx `@id` and `@ref` values within a dataset, ensuring identifier uniqueness across producers.

→ [Full documentation](../../Objects/Codespace/Description_Codespace.md)

---

## CompositeFrame

A container frame that groups multiple typed frames (ServiceFrame, TimetableFrame, etc.) into a single coherent delivery.

→ [Full documentation](../../Frames/CompositeFrame/Description_CompositeFrame.md)

---

## Contract

A legal or commercial agreement governing responsibilities between an Authority (contractee) and an Operator (contractor) for providing public transport services.

→ [Full documentation](../../Objects/Contract/Description_Contract.md)

---

## DatedServiceJourney

A specific operational instance of a ServiceJourney on a particular calendar day, including day-specific modifications such as cancellations, replacements, or reinforcements.

→ [Full documentation](../../Objects/DatedServiceJourney/Description_DatedServiceJourney.md)

---

## DayType

A classification of days on which a specific set of transport services operates (e.g., "Weekdays", "Saturdays", "Public Holidays").

→ [Full documentation](../../Objects/DayType/Description_DayType.md)

---

## DayTypeAssignment

The binding between a DayType and a specific date or date range (OperatingPeriod), determining when that DayType is active - including exception handling via `isAvailable=false`.

→ [Full documentation](../../Objects/DayTypeAssignment/Description_DayTypeAssignment.md)

---

## DestinationDisplay

The text shown on the front or side of a public transport vehicle to indicate its destination, including via-points and variant labels.

→ [Full documentation](../../Objects/DestinationDisplay/Description_DestinationDisplay.md)

---

## FareContract

A customer-facing agreement for the right to travel and consume fare products, defined within a SalesTransactionFrame (NeTEx Part 3 - Sales).

→ [Full documentation](../../Objects/FareContract/Description_FareContract.md)

---

## FareZone

A geographic zone used to determine ticket prices in public transport, grouping stop points for fare calculation.

→ [Full documentation](../../Objects/FareZone/Description_FareZone.md)

---

## FlexibleServiceProperties

The scheduling and operational characteristics of a flexible (demand-responsive) transport service, attached to a ServiceJourney.

→ [Full documentation](../../Objects/FlexibleServiceProperties/Description_FlexibleServiceProperties.md)

---

## GroupOfLines

A logical grouping of multiple Line objects for common management, branding, distribution, or filtering.

→ [Full documentation](../../Objects/GroupOfLines/Description_GroupOfLines.md)

---

## Interchange

A planned transfer opportunity between two ServiceJourneys at a shared stop point, modelled as `ServiceJourneyInterchange` in XML.

→ [Full documentation](../../Objects/Interchange/Description_Interchange.md)

---

## JourneyPattern

The ordered sequence of ScheduledStopPoints that a transport service follows for a specific variant of a Route.

→ [Full documentation](../../Objects/JourneyPattern/Description_JourneyPattern.md)

---

## Line

A public transport service line, representing a marketed route with a name, transport mode, and operator.

→ [Full documentation](../../Objects/Line/Description_Line.md)

---

## LinkSequenceProjection

The geographic representation of a ServiceLink, carrying GML geometry (typically a LineString) describing the spatial path between two consecutive ScheduledStopPoints.

→ [Full documentation](../../Objects/LinkSequenceProjection/Description_LinkSequenceProjection.md)

---

## Notice

Informational or regulatory text associated with public transport services, displayed to passengers.

→ [Full documentation](../../Objects/Notice/Description_Notice.md)

---

## OperatingDay

A specific calendar date on which transport services operate, referenced by DatedServiceJourney to anchor a journey to a concrete day.

→ [Full documentation](../../Objects/OperatingDay/Description_OperatingDay.md)

---

## OperatingPeriod

A continuous date range (FromDate-ToDate) during which a set of transport services may operate, used by DayTypeAssignment.

→ [Full documentation](../../Objects/OperatingPeriod/Description_OperatingPeriod.md)

---

## Operator

An organisation that provides public transport services under contract with an Authority.

→ [Full documentation](../../Objects/Operator/Description_Operator.md)

---

## Parking

A parking facility associated with public transport - such as a park-and-ride lot, bike parking, or car park at a station.

→ [Full documentation](../../Objects/Parking/Description_Parking.md)

---

## PassengerStopAssignment

The bridge linking a logical ScheduledStopPoint to a physical Quay within a StopPlace, connecting timetable planning with physical infrastructure.

→ [Full documentation](../../Objects/PassengerStopAssignment/Description_PassengerStopAssignment.md)

---

## placeEquipments

A container within a StopPlace or Quay holding equipment items (shelters, waiting rooms, sanitary facilities, ticketing machines) that describe the physical amenities at the stop.

→ [Full documentation](../../Objects/placeEquipments/Description_placeEquipments.md)

---

## PublicationDelivery

The root element of every NeTEx XML document, wrapping one or more frames with metadata (timestamp, participant, description).

→ [Example](../../Frames/Example_PublicationDelivery.xml)

---

## PurposeOfGrouping

A classifier for the reason why NeTEx objects are grouped together (e.g., for presentation, regulation, or contract scope).

→ [Full documentation](../../Objects/PurposeOfGrouping/Description_PurposeOfGrouping.md)

---

## Quay

A specific boarding or alighting position (platform, stand, bay) within a StopPlace where passengers physically meet vehicles.

→ [Full documentation](../../Objects/Quay/Description_Quay.md)

---

## ResponsibilitySet

The set of roles and organisations responsible for managing data, operations, or contractual obligations within a defined scope.

→ [Full documentation](../../Objects/ResponsibilitySet/Description_ResponsibilitySet.md)

---

## Route

The logical geographic path definition for a Line with a specific direction.

→ [Full documentation](../../Objects/Route/Description_Route.md)

---

## SanitaryEquipment

Sanitary facilities (toilets, washrooms) available at a stop place, station, or onboard a vehicle.

→ [Full documentation](../../Objects/SanitaryEquipment/Description_SanitaryEquipment.md)

---

## ScheduledStopPoint

A logical stopping point in the timetable, used by JourneyPatterns and ServiceJourneys to define where vehicles stop.

→ [Full documentation](../../Objects/ScheduledStopPoint/Description_ScheduledStopPoint.md)

---

## ServiceAlteration

An enumeration on DatedServiceJourney indicating the deviation type. Allowed values: `planned`, `cancellation`, `replaced`, `extraJourney`. Omitted implies `planned`.

→ [DatedServiceJourney table](../../Objects/DatedServiceJourney/Table_DatedServiceJourney.md)

---

## ServiceJourney

A planned trip in the timetable operating on a recurring schedule, defining the stop sequence via a JourneyPattern, passing times, operator, and days of operation.

→ [Full documentation](../../Objects/ServiceJourney/Description_ServiceJourney.md)

---

## ShelterEquipment

Weather shelter facilities available at a stop place or quay, with properties such as seating, step-free access, and enclosure.

→ [Full documentation](../../Objects/ShelterEquipment/Description_ShelterEquipment.md)

---

## StopPlace

A named physical or virtual location where passengers can board or alight from public transport, containing one or more Quays.

→ [Full documentation](../../Objects/StopPlace/Description_StopPlace.md)

---

## TariffZone

A geographic fare zone used for ticketing and pricing, grouping stops and areas into zones that determine ticket prices.

→ [Full documentation](../../Objects/TariffZone/Description_TariffZone.md)

---

## TicketingEquipment

Ticket machines, validators, or other ticketing infrastructure available at a stop place or station.

→ [Full documentation](../../Objects/TicketingEquipment/Description_TicketingEquipment.md)

---

## TopographicPlace

A named geographic area such as a city, municipality, county, or region - used to provide spatial context for StopPlaces.

→ [Full documentation](../../Objects/TopographicPlace/Description_TopographicPlace.md)

---

## TrainBlock

A rail-specific specialisation of Block that represents an operational grouping for a single train on a given operating day.

→ [Full documentation](../../Objects/TrainBlock/Description_TrainBlock.md)

---

## Vehicle

A specific physical vehicle in the fleet used to operate public transport services.

→ [Full documentation](../../Objects/Vehicle/Description_Vehicle.md)

---

## VehicleType

A typified vehicle configuration (model or series) defining reusable characteristics such as capacity, dimensions, propulsion, and accessibility features.

→ [Full documentation](../../Objects/VehicleType/Description_VehicleType.md)

---

## View

In this profile, "View" is used in two complementary senses:

1. **Publication view** - The way data is selected and packaged inside a NeTEx PublicationDelivery for a specific purpose or audience (e.g., a Timetable publication view).
2. **Thematic view** - A conceptual grouping used in the profile to scope content and requirements (e.g., Timetable, Network, Fares).

Clarifications:
- DatedCalls are not a separate "view" - they are child elements of a DatedServiceJourney within a TimetableFrame.
- When in doubt, prefer the precise NeTEx model terms (PublicationDelivery, TimetableFrame, DatedServiceJourney).

→ [DatedServiceJourney](../../Objects/DatedServiceJourney/Description_DatedServiceJourney.md)

---

## WaitingRoomEquipment

Enclosed indoor waiting room facilities available at a stop place or station, with properties such as seating, step-free access, and heating.

→ [Full documentation](../../Objects/WaitingRoomEquipment/Description_WaitingRoomEquipment.md)
