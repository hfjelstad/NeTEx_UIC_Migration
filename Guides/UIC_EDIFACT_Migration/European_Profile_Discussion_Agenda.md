# 🚆 European NeTEx Timetable Profile for Rail — Discussion Agenda

**Meeting:** 2-day working session, April 2026  
**Context:** Alignment between the Nordic Profile / this repo and the emerging European timetable profile for rail (input document: *Thoughts on the European timetable profile for rail*)

Each topic below includes: the question to be resolved, the current Nordic Profile stance, and the decision options.

---

## 🔗 Theme A — The ServiceJourney: identity, numbering, and coupling (Topics 1–3)

> Topics 1, 2, and 3 form a logical whole and should be decided together. The answer to *"what is a ServiceJourney?"* (Topic 1) directly determines *how train numbers attach to it* (Topic 2) — because a ServiceJourney defined by carriage continuity may span several train numbers through working, and a single train number may produce multiple ServiceJourneys after a split. Both consequences are then expressed structurally via `JourneyPartCouple` / `CoupledJourney` (Topic 3). Deciding Topic 1 without Topics 2 and 3 in view will produce inconsistencies.

---

## Topic 1 — ServiceJourney semantics: carriage continuity vs train number

**Why this matters most:** This is the biggest conceptual gap between EDIFACT and NeTEx, and the most likely source of misimplementation across European operators.

### The question
In EDIFACT, one service number (PRD) = one train service. Should NeTEx follow the same 1:1 mapping, or adopt the richer Transmodel definition?

### Nordic Profile stance
A `ServiceJourney` represents a **travel opportunity defined by carriage continuity** — a passenger can remain seated from origin to destination without relocating. This is independent of the train number:

- A single train number may become **multiple ServiceJourneys** after a split (each carriage group that continues to a different destination is its own ServiceJourney)
- A single ServiceJourney may span **multiple train numbers** through working
- The physical coupling on a shared segment is expressed via `JourneyPartCouple` inside a `CoupledJourney`

### Decision options
| Option | Description | Trade-off |
|--------|-------------|-----------|
| **A — Transmodel semantics** | ServiceJourney = carriage continuity, JourneyPartCouple for shared segments | Semantically correct, requires operators to decompose train numbers |
| **B — EDIFACT-compatible** | ServiceJourney = train number, coupling not modelled | Easy migration, loses richness needed for passenger information |
| **C — Both, profiled** | Mandate A for new data, allow B as a transitional pattern | Pragmatic, but complicates consumers |

> *See also Topics 2 and 3.*

---

## Topic 2 — Train number representation

**Why this matters:** Multiple systems (CRS, PIS, crew, passengers) all reference train numbers differently. The right model here depends directly on the outcome of Topic 1: if a ServiceJourney can span multiple train numbers through working, a single `PrivateCode` field is insufficient.

### The question
The input document (section 12) defines a `trainNumbers/TrainNumber` container with `ForAdvertisement` and `ForProduction` fields. The Nordic Profile uses `PrivateCode` and `PublicCode` directly on `ServiceJourney`.

### Nordic Profile stance
Store the operational number as `PrivateCode` and the passenger-facing number as `PublicCode` on `ServiceJourney`. These cover the two most common cases without requiring a separate container.

### Decision options
| Option | Description | Trade-off |
|--------|-------------|-----------|
| **A — PrivateCode / PublicCode on ServiceJourney** | Simple, direct | Limited to two codes; cannot express multiple train number ranges on a through-working journey |
| **B — trainNumbers/TrainNumber container** | Explicit `ForAdvertisement` / `ForProduction` semantics; multiple entries possible | More expressive, especially for through-working where the train number changes en route |
| **C — Both** | Use B when multiple numbers apply, A for the simple case | Increases implementation complexity for consumers |

> *See also Topics 1 and 3.*

---

## Topic 3 — Coupled trains and splits: `JourneyPartCouple` vs `JourneyMeeting`

**Why this matters:** The European profile input document (section 13) includes `JourneyMeetings` as a distinct concept. The Nordic approach handles the same physical reality with a different mechanism — and the two concepts are not interchangeable.

### The question
`JourneyMeeting` in the input document describes a scheduled encounter between two journeys (e.g. a connection at a passing loop — an operational scheduling dependency with no direct passenger relevance). `JourneyPartCouple` describes two `ServiceJourney`s running as a **physically coupled unit** on a shared segment, where at least one carriage is continuous across both journeys.

These are distinct concepts and may both be needed:

| Situation | Mechanism |
|-----------|-----------|
| Two train sets physically joined; passengers stay seated | `JourneyPartCouple` inside `CoupledJourney` |
| Two trains scheduled to meet at a loop; no passenger relevance | `JourneyMeeting` |

### Nordic Profile stance
Model coupled/split services using `JourneyPartCouple` / `CoupledJourney`. `JourneyMeeting` is considered operational scheduling data outside the passenger timetable profile scope.

### Key questions for discussion
- Is `JourneyMeeting` in scope for the European timetable profile, or is it operational data?
- If in scope, what is the minimum mandatory content (from/to journey, location, reason)?
- Does the European profile need to cover both concepts explicitly, or can `JourneyMeeting` be deferred to an operational data profile?

> *See also Topics 1 and 2.*

---

## Topic 4 — `calls/Call` vs `passingTimes/TimetabledPassingTime`

**Why this matters:** Every timetable implementation is built around one of these two patterns. Standardising on the wrong one has long-term consequences.

### The question
The European profile input document defines stop times using `calls/Call` (section 10). The Nordic Profile uses `passingTimes/TimetabledPassingTime`. Which should the European profile mandate?

### What `calls` actually is in NeTEx
`calls/Call` is formally defined in the NeTEx model as a **view** — a derived, read-optimised projection over the underlying `passingTimes` + `JourneyPattern` data. It is not a parallel creation mechanism. Producing the `calls` view natively forces the implementer to fully inline all the implicit JourneyPattern logic (boarding/alighting rules, stop sequencing, destination displays) into each Call element, making correct implementation significantly more demanding.

### Nordic Profile stance
Use `passingTimes/TimetabledPassingTime`. The calls view may be offered as a derived output for consumers that prefer it, but it should not be the production source format.

### Decision options
| Option | Description | Trade-off |
|--------|-------------|-----------|
| **A — passingTimes** | Production path; JourneyPattern carries boarding/alighting/display logic | Correct separation of concerns, requires understanding of JourneyPattern |
| **B — calls** | All stop data inlined per journey | Consumer-friendly, ~2× richer per stop, but ~10× harder to produce correctly; conceptually misleads implementers about the NeTEx model |
| **C — calls as optional derived output** | Profile mandates passingTimes; allows calls as a parallel derived view | Best of both worlds if consumers need flat stop data |

---

## Topic 5 — Calendar model: bitmask vs expanded per-date objects

**Why this matters:** The choice determines whether per-date exceptions (cancellations, alterations, extra journeys) can be expressed natively.

### The question
The input document retains the EDIFACT bitmask approach via `UicOperatingPeriod`/`ValidDayBits`. The Nordic Profile expands each operating date into individual `OperatingDay` + `DatedServiceJourney` records.

### Nordic Profile stance
Expand to individual `OperatingDay` + `DatedServiceJourney` per date. This enables:
- `ServiceAlteration` on individual `DatedServiceJourney` (cancellation, replacement, extra journey)
- Per-date variant selection (e.g. Sunday pattern vs weekday pattern)
- Unambiguous cross-referencing of real-time data to a specific service on a specific date

### Decision options
| Option | Description | Trade-off |
|--------|-------------|-----------|
| **A — Expanded (OperatingDay + DatedServiceJourney)** | One record per date | Verbose, but enables cancellations/alterations natively |
| **B — Bitmask (UicOperatingPeriod + ValidDayBits)** | Compact, preserves EDIFACT thinking | Cannot express per-date exceptions without additional structure |
| **C — Both** | Bitmask for regular service, expanded for exceptions | Flexible, but consumers must handle both patterns |

---

## Topic 6 — Identifier strategy: EU-wide ID vs operator codespace

**Why this matters:** IDs are forever. Getting this wrong creates long-term interoperability debt.

### The question
The input document repeatedly raises "EU-ID ???" — whether a centrally issued EU identifier should form the numeric part of `@id` on objects like ScheduledStopPoint, StopPlace, and ServiceJourney. The Nordic Profile uses operator codespace prefixes (`VR:ScheduledStopPoint:001002326`).

### Nordic Profile stance
Use operator codespace prefixes. Central registries (e.g. NSR/Tiamat) own their own codespace and IDs; operators reference those objects by ref without version. This works today without waiting for a central EU registry.

### Key questions for discussion
- Does a mandatory EU-ID registry exist or have a realistic delivery timeline?
- If EU-IDs are assigned centrally, do operators include them as a `keyList` KeyValue alongside their own codespace ID, or do they replace the codespace ID?
- How is identity maintained during the transition period before EU-IDs are assigned?

### Decision options
| Option | Description | Trade-off |
|--------|-------------|-----------|
| **A — Operator codespace only** | Works today, no dependency on central registry | IDs are operator-scoped; cross-operator deduplication requires external mapping |
| **B — EU-ID as primary @id** | Globally unique, registry-backed | Requires EU registry to be operational; blocks implementation until then |
| **C — Operator codespace + EU-ID in keyList** | EU-ID carried as metadata alongside operator ID | Pragmatic transition path; consumers can use whichever scope they need |

---

## Topic 7 — `DayType` in the model

**Why this matters:** DayType enables compact representation of recurring patterns but complicates the calendar model.

### The question
The input document (section 8) lists `dayTypes/DayTypeRef` as mandatory on `ServiceJourney`. The Nordic Profile uses `DatedServiceJourney` directly, with no `DayType`.

### Nordic Profile stance
Skip `DayType`. Go directly to one `DatedServiceJourney` per operating date. This is more verbose but unambiguous, and avoids the complexity of DayType resolution for consumers.

### Key questions for discussion
- Is `DayType` genuinely needed at European level, e.g. for recurring international services?
- Can it be optional — used when a service truly recurs without exception, omitted otherwise?

---

## Topic 8 — Scope of centrally managed elements

**Why this matters:** Defines who can create, update and reference which objects, and what a valid delivery looks like.

### The question
Which objects must come from a central registry, and which are produced by the operator? The input document raises this for organisations, location codes, and code lists.

### Nordic Profile stance

| Owned by central registry | Owned by operator delivery |
|---------------------------|---------------------------|
| StopPlace, Quay, TopographicPlace | Line, Route, JourneyPattern |
| Authority, Operator | ServiceJourney, DatedServiceJourney |
| TariffZone | ScheduledStopPoint, PassengerStopAssignment |

Operator references central objects by `@ref` **without** `@version`. Own objects include `@version`.

### Key questions for discussion
- Is there a single European registry for Operators/Authorities, or does each country maintain its own?
- How are discrepancies between national registries and the European layer resolved?
- What validation rules enforce the boundary?

---

## Topic 9 — `PassengerStopAssignment` vs `TrainStopAssignment`

**Why this matters:** The naming signals the intended use and affects which data must be present.

### The question
The input document (section 18) uses `PassengerStopAssignment` but asks "Why not TrainStopAssignment?" NeTEx supports both. For railway operations, the platform/track assignment is an operational fact, not inherently passenger-facing.

### Key questions for discussion
- Should the European rail profile use `PassengerStopAssignment`, `TrainStopAssignment`, or allow both?
- Is track/platform assignment in scope for the timetable profile, or only for real-time/operational data?

---

## Topic 10 — `CountryRef` on `ScheduledStopPoint`

**Why this matters:** Cross-border services need to attribute stops to countries for regulatory and billing purposes.

### The question
The input document (section 5) lists `CountryRef` on `scheduledStopPoint`. The Nordic Profile examples do not include it.

### Key questions for discussion
- Is `CountryRef` mandatory for international services only, or for all stops?
- Is it expressed on `ScheduledStopPoint`, on `StopPlace`, or both?
- What code list is used (ISO 3166-1 alpha-2)?

---

## Topic 11 — Where does the EU/ERA identifier live in the data model?

**Day 1 outcome:** The meeting established that a cross-border identifier for stops and stations must be expressible in NeTEx, but the precise mechanism is not yet decided.

### The question
A European-level identifier (e.g. an ERA station code, a future EU-ID, or the existing UIC code as a European reference) needs to attach to a `StopPlace` (and potentially `ScheduledStopPoint`). NeTEx offers several mechanisms. The choice affects interoperability, validation, and the data governance boundary between central registries and operator deliveries.

### Options for identifier placement

| Mechanism | Where | Example | Considerations |
|-----------|-------|---------|----------------|
| **keyList / KeyValue** | `StopPlace/keyList/KeyValue` | `<Key>eraCode</Key><Value>ERA:0010:002326</Value>` | Already used for `uicCode`; extensible; key name must be standardised across all producers |
| **AlternativeName with purpose** | `StopPlace/alternativeNames/AlternativeName` | `<NameType>translation</NameType>` | Intended for name variants, not identifiers — semantically incorrect |
| **PrivateCode** | `StopPlace/PrivateCode` | `<PrivateCode>ERA:0010:002326</PrivateCode>` | Single slot only; already used for UIC code in Nordic examples — cannot hold two codes simultaneously |
| **Dedicated codespace @id** | `@id` on `StopPlace` | `ERA:StopPlace:0010002326` | Cleanest for interoperability; requires ERA to operate a live registry and assign IDs before producers can publish |
| **GroupOfStopPlaces** | `SiteFrame/groupsOfStopPlaces` | Group all national representations of one logical station | Allows grouping without changing the `@id` of existing StopPlace records; see Topic 12 |

### Nordic Profile current practice
UIC codes are stored as `keyList/KeyValue` with `Key=uicCode`. Extending this with an additional KeyValue (e.g. `Key=eraCode`) would require zero changes to the data model and is immediately implementable.

### Key questions for discussion
- Has ERA or another EU body committed to issuing a station/stop identifier registry? If so, what is the timeline?
- Should the key name be standardised in the profile (e.g. `eraCode`, `euStationId`) or left to producers?
- Should `ScheduledStopPoint` also carry the EU identifier via `keyList`, or is it sufficient to carry it only on `StopPlace`?
- Is the UIC code itself sufficient as the cross-border reference for rail, given it already exists on every station?

---

## Topic 12 — `GroupOfStopPlaces`: logical interchange grouping and regional grouping

**Day 1 outcome:** `GroupOfStopPlaces` was identified as needed but not yet documented for the European rail profile.

### The question
`GroupOfStopPlaces` allows multiple `StopPlace` records to be logically associated without changing their individual `@id` or ownership. In the rail context two distinct use cases emerged:

| Use case | Example | Purpose |
|----------|---------|---------|
| **Logical interchange** | Oslo S (rail) + Oslo Bussterminal (bus) grouped as "Oslo central interchange" | Passenger wayfinding, connection planning, journey planners |
| **Regional / country grouping** | All rail stations in Norway grouped for routing or tariff attribution | Network topology, `CountryRef` aggregation, ERA reporting |

Both use cases are served by the same NeTEx element. The distinction is expressed via `PurposeOfGroupingRef` pointing to a defined purpose (e.g. `interchange` vs `country`).

### Key questions for discussion
- Should `GroupOfStopPlaces` with purpose `interchange` be mandatory for any multi-operator hub (where rail + bus + metro StopPlaces co-exist)?
- Can `GroupOfStopPlaces` serve as the anchor for an EU-level cross-border identifier (see Topic 11), so that national StopPlace records are grouped under one EU-identified group rather than changing the `@id` of individual records?
- Who owns and maintains these groups — the national stop registry, a European registry, or the operator?

---

## Appendix: Quick reference — Nordic Profile vs European profile input

| Topic | Nordic Profile | European profile input doc |
|-------|---------------|---------------------------|
| Stop times | `passingTimes` / `TimetabledPassingTime` | `calls` / `Call` |
| Calendar | `OperatingDay` + `DatedServiceJourney` per date | `UicOperatingPeriod` / `ValidDayBits` bitmask |
| Train number | `PrivateCode` / `PublicCode` on ServiceJourney | `trainNumbers/TrainNumber` container |
| Recurring patterns | Not used (direct DSJ per date) | `DayType` mandatory |
| Coupled trains / splits | `JourneyPartCouple` / `CoupledJourney` (Topic 3) | `JourneyMeeting` (conflates two concepts) |
| Stop assignment | `PassengerStopAssignment` | `PassengerStopAssignment` (questioned) |
| Identifiers | Operator codespace prefix | EU-ID (undefined) |
