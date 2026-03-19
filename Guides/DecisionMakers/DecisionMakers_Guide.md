# 📊 NeTEx for Decision Makers

## 1. 🎯 What Is NeTEx?

**NeTEx** (Network Timetable Exchange) is a European standard (CEN TS 16614) for exchanging public transport data in XML format. It covers the full lifecycle of public transport information — from network topology and timetables to fares, vehicle scheduling, and passenger information.

NeTEx is built on **Transmodel**, the European reference data model for public transport. Where Transmodel defines the *concepts*, NeTEx defines the *exchange format*.

```text
+------------------+     defines concepts     +------------------+
|   Transmodel     | -----------------------> |     NeTEx        |
|   (data model)   |                          |  (XML exchange)  |
+------------------+                          +------------------+
        |                                            |
        |  also informs                              |  exchanges data as
        v                                            v
+------------------+                          +------------------+
|     SIRI         |                          |   XML files      |
| (real-time data) |                          |   between systems|
+------------------+                          +------------------+
```

---

## 2. 🗂️ What Does NeTEx Cover?

NeTEx is organised into three parts, each covering a different aspect of public transport:

| Part | Scope | Key Data |
|------|-------|----------|
| **Part 1 — Network** | Topology and timetables | Lines, Routes, Stops, JourneyPatterns, ServiceJourneys, Timetables |
| **Part 2 — Scheduling** | Vehicle operations and calendar | Vehicle scheduling, Blocks, DayTypes, OperatingPeriods |
| **Part 3 — Fares** | Ticketing and pricing | Fare products, Tariff zones, Sales channels, Travel rights |

Most implementations start with **Part 1** (the timetable and stop data that passengers see), then expand to Part 2 (operations) and Part 3 (fares) as needed.

### Data Domains

```text
+-------------------------------------------------------------------+
|                        NeTEx Data Domains                         |
|                                                                   |
|  +------------------+  +------------------+  +------------------+ |
|  | WHAT runs        |  | WHERE it stops   |  | WHO operates     | |
|  | Lines, Routes,   |  | StopPlaces,      |  | Authorities,     | |
|  | Journeys         |  | Quays, Platforms |  | Operators        | |
|  +------------------+  +------------------+  +------------------+ |
|                                                                   |
|  +------------------+  +------------------+  +------------------+ |
|  | WHEN it runs     |  | WITH what        |  | HOW MUCH it      | |
|  | DayTypes,        |  | VehicleTypes,    |  | costs             | |
|  | Calendar,        |  | Blocks, Fleet    |  | Fares, Tariffs,  | |
|  | Timetables       |  | assignments      |  | Tickets          | |
|  +------------------+  +------------------+  +------------------+ |
+-------------------------------------------------------------------+
```

---

## 3. 🔗 NeTEx in the Ecosystem

NeTEx doesn't operate in isolation. It fits into a broader landscape of public transport standards:

| Standard | Purpose | Relationship to NeTEx |
|----------|---------|----------------------|
| **Transmodel** | Conceptual reference model | NeTEx implements Transmodel as an XML schema |
| **SIRI** | Real-time information | Shares Transmodel concepts; NeTEx provides the planned data that SIRI updates in real-time |
| **GTFS** | Simple schedule exchange | Simpler but less expressive; NeTEx covers the same ground plus fares, accessibility, vehicle scheduling |
| **IFOPT** | Stop place infrastructure | Incorporated into NeTEx Part 1 (SiteFrame, StopPlace, Quay) |
| **EPIP** | European Passenger Information Profile | A NeTEx profile mandated by EU regulation for cross-border data exchange |

### How They Work Together

```text
  Planning phase                    Operations phase
+------------------+            +------------------+
|  NeTEx           |            |  SIRI            |
|  (planned data)  | ---------> |  (real-time)     |
|  Timetable,      |  provides  |  Delays,         |
|  Stops, Fares    |  baseline  |  Cancellations,  |
|                  |  for       |  Vehicle position|
+------------------+            +------------------+
         |                               |
         v                               v
+--------------------------------------------------+
|            Journey Planner / App                  |
|  Combines planned + real-time for passenger info  |
+--------------------------------------------------+
```

---

## 4. 📜 Regulatory Context

NeTEx adoption is driven by European regulation:

- **EU Delegated Regulation 2017/1926** (Multimodal Travel Information Services) requires EU member states to provide public transport data through National Access Points (NAPs) in NeTEx or equivalent format.
- **EPIP** (European Passenger Information Profile) defines the subset and rules for cross-border NeTEx data exchange.
- National profiles (like the Nordic Profile documented in this repository) extend EPIP with region-specific rules.

---

## 5. ✅ Why Adopt NeTEx?

| Benefit | Explanation |
|---------|-------------|
| **Interoperability** | Standardised format means systems from different vendors can exchange data without custom mappings |
| **Completeness** | Covers the full public transport domain — no need to combine multiple incompatible formats |
| **Regulatory compliance** | Required or recommended by EU regulation for national access points |
| **Expressiveness** | Models complex scenarios (interchanges, accessibility, flexible services, fare structures) that simpler formats cannot |
| **Separation of concerns** | Different organisational units can publish and update their data independently |
| **Versioning** | Every object carries a version, enabling change tracking and incremental updates |

### When NeTEx May Be More Than You Need

- **Simple, single-operator bus networks** with no fare complexity may find GTFS sufficient
- **Real-time only** use cases are better served by SIRI alone
- **Internal systems** that never exchange data externally may not need a standardised format

> 💡 **Tip:** Even if you start with GTFS, consider NeTEx as your canonical format. GTFS can be generated from NeTEx, but the reverse conversion loses information.

---

## 6. 🏗️ How NeTEx Data Is Structured

NeTEx organises data into **Frames** — logical containers that group related objects:

```text
PublicationDelivery (the XML document)
 └── CompositeFrame (groups frames for one delivery)
      ├── ResourceFrame:     Authorities, Operators, Vehicle types
      ├── SiteFrame:         StopPlaces, Quays, Accessibility
      ├── ServiceFrame:      Lines, Routes, JourneyPatterns, Stops
      ├── ServiceCalendarFrame: DayTypes, Operating periods
      ├── TimetableFrame:    ServiceJourneys, Passing times
      ├── VehicleScheduleFrame: Blocks, Vehicle assignments
      └── FareFrame:         Tariffs, Fare products, Sales packages
```

Each frame can be **versioned and published independently** — a timetable change doesn't require republishing stop infrastructure, and vice versa.

---

## 7. 🚀 Getting Started as an Organisation

### Step 1: Choose Your Scope

Decide which NeTEx parts you need:

| If you need to exchange... | You need... |
|---------------------------|------------|
| Timetables and stops | Part 1 (Network) |
| Vehicle scheduling and operations | Part 1 + Part 2 (Scheduling) |
| Fares and ticketing | Part 1 + Part 3 (Fares) |
| Everything | All three parts |

### Step 2: Choose or Define a Profile

A profile defines which elements are mandatory, optional, or unused for your context. Options:
- **EPIP** — European baseline for cross-border exchange
- **Nordic Profile (NP)** — Nordic countries extension of EPIP
- **Custom profile** — Extend EPIP for your national or regional needs

### Step 3: Set Up Tooling

- XML editors with NeTEx schema support
- Validation tools (schema + profile validation)
- See the [Tools Guide](../Tools/Tools_Guide.md) and [Validation Guide](../Validation/Validation.md) for specifics

### Step 4: Start Small

Begin with the core chain — a single line from stop to timetable — then expand:

```text
Authority → Operator → Line → Route → JourneyPattern → ServiceJourney
```

See the [Get Started Guide](../GetStarted/GetStarted_Guide.md) and [Journey Lifecycle Guide](../JourneyLifecycle/JourneyLifecycle_Guide.md) for hands-on walkthroughs.

---

## 8. 🔗 Related Resources

### Guides in This Repository
- [Get Started](../GetStarted/GetStarted_Guide.md) -- Hands-on introduction for developers
- [Journey Lifecycle](../JourneyLifecycle/JourneyLifecycle_Guide.md) -- The core data chain
- [Organisational Governance](../OrganisationalGovernance/OrganisationalGovernance_Guide.md) -- Authority and Operator setup
- [Tools](../Tools/Tools_Guide.md) -- Editors, validators, and development workflow
- [Validation](../Validation/Validation.md) -- Schema validation and common errors

### External
- [NeTEx CEN Standard](https://www.netex-cen.eu/) -- Official specification and schemas
- [Transmodel](https://www.transmodel-cen.eu/) -- The underlying conceptual model
- [SIRI](https://www.siri-cen.eu/) -- Real-time companion standard
- [EU Delegated Regulation 2017/1926](https://eur-lex.europa.eu/eli/reg_del/2017/1926/oj) -- Regulatory basis for NeTEx adoption
