# NeTEx Profile Documentation – Canonical Entry Point

This repository contains the canonical, English-language documentation for the NeTEx profile used in this organization. All object documentation follows the master template in `LLM/README.md` and must adhere to its folder structure, file naming, required sections, description formatting, table formatting, and XML example formatting.

Link to master template: ./LLM/README.md

How to navigate the profile documentation
- Start at the top-level domain folders (e.g., Network, Timetable, Fares). Each object has its own folder and a README that strictly follows the template in `LLM/README.md`.
- Within each object folder, use the “Description”, “Table” (with all required fields), and the “XML example(s)” sections to understand how the profile constrains NeTEx.
- Look for cross-references to Frames (ServiceFrame, ResourceFrame, FareFrame, etc.) and to reusable example files in the `XSD 2.0/examples` tree.

Seat/space reservation modelling
The following guidance defines where to place booking rules, how to override them at the ServiceJourney level, how to express booking windows and contacts, how to represent capacity, and how to model the fares-side supplement for seat reservations.

Where BookingArrangement can be attached
- Operator: Use to define a network-wide default booking policy for all services run by the operator.
- Line: Use to define a default for a specific Line when it differs from the operator default.
- JourneyPattern: Use to set a pattern-level default when a subset of journeys on a line share the same booking rules.
- ServiceJourney: Use for the concrete departure (day/time-specific) policy and for overrides of higher-level defaults.
- Flexible vs fixed: For flexible/on-demand services, booking is typically mandatory and attached at the ServiceJourney (or via FlexibleServiceProperties) to ensure request/offer workflows are enabled. For fixed-schedule services, booking is often optional and inherited from Operator/Line/JourneyPattern, with specific ServiceJourney overrides as needed.

ServiceJourney-level overrides (examples)
- Example 1 (override default optional booking): Operator/Line policy allows optional booking until 2 hours before departure; one particular ServiceJourney is highly utilized and is set to mandatory booking with a latest booking time at 18:00 the previous day.
- Example 2 (temporary disruption): A set of ServiceJourneys on a Line are configured with a temporary rule requiring booking due to reduced capacity during works; the rule is attached directly to the affected ServiceJourneys.

Booking details to include
- BookingContact: Provide contact person/centre, phone, email, URL and any instructions for the customer.
- BookWhen: Specify when customers are allowed or required to book (e.g., in advance only, at time of travel, etc.).
- LatestBookingTime: Provide a cut-off time (e.g., HH:MM:SS) on or before the day of operation, aligned with the selected BookWhen policy.

Capacity modelling
- Use `VehicleType.PassengerCapacity` to state the operational capacity used in planning. This may include total capacity, seated capacity, standing capacity, and dedicated places (e.g., wheelchairs, prams, bicycles). ServiceJourney-level booking policies should be consistent with the available capacity on the referenced VehicleType.

Fares-side reservation supplement
- Model seat reservation as a `SupplementProduct` in the Fares domain.
- Mandatory vs optional:
  - Mandatory when a reservation must be purchased/held to travel on the ServiceJourney (e.g., long-distance or high-demand segments).
  - Optional when reservation is allowed for comfort/choice but not required to travel.
- Pricing, availability, and conditions for the `SupplementProduct` should be linked to the corresponding ServiceJourney(s), Lines, or Operator scope, depending on the rule that triggers the reservation requirement.

Cross-links to reservation-related examples
- Booking arrangements in a general frame: XSD 2.0/examples/functions/bookingArrangements/generalframe.xml
- TAP TSI-related reservation constructs: XSD 2.0/examples/standards/tap_tsi/

Note
- All object documentation must include at least one XML example using the `ERP` codespace and must strictly follow the template in `LLM/README.md`. Validate any raw XML examples against NeTEx 2.0 before committing.
