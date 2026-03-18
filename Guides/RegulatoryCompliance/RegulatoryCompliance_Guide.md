# 📜 Regulatory Compliance — Delegated Regulation & NAP Submission

## 1. 🎯 Introduction

EU Delegated Regulation 2017/1926 requires public transport authorities and operators across Europe to provide scheduled transport data through National Access Points (NAPs). For a local or regional bus operator this can feel overwhelming — the regulation references broad data categories, and NeTEx is a large standard. This guide cuts through the complexity and maps the regulatory requirements to concrete NeTEx objects you need to produce.

In this guide you will learn:
- 📋 What data categories the Delegated Regulation requires
- 🏗️ How EPIP and the Nordic Profile relate to the regulation
- 📐 Which NeTEx frames and objects map to each requirement
- 🚌 A step-by-step checklist for a bus operator's minimum dataset
- 🌐 How NAP submission works in practice

---

## 2. 📋 What the Delegated Regulation Requires

Delegated Regulation 2017/1926 on Multimodal Travel Information Services defines data categories that EU member states must make available, grouped by implementation priority:

| Priority | Deadline | Data Categories | NeTEx Coverage |
|----------|----------|-----------------|----------------|
| **A** | Dec 2019 | Stop/station location, routes, timetables, accessibility | StopPlace, Line, ServiceJourney, AccessibilityAssessment |
| **B** | Dec 2021 | Fares, on-demand transport, trip plans | FareProduct, FlexibleServiceProperties, SalesOfferPackage |
| **C** | Dec 2023 | Disruptions, real-time, availability | Primarily SIRI (not NeTEx) |

Category C is mostly SIRI territory (real-time updates, disruptions). This guide focuses on NeTEx deliveries for categories A and B.

> 💡 **Tip:** Most bus operators start with Priority A data — stops, lines, timetables, and accessibility. This alone satisfies the core compliance requirement.

---

## 3. 🏗️ EPIP vs Nordic Profile

The Delegated Regulation does not mandate NeTEx directly — it requires data to be available in a standard format. In practice, EPIP (European Passenger Information Profile) is the EU-level NeTEx profile for cross-border exchange, and national profiles build on top of it.

| Aspect | EPIP (EU baseline) | Nordic Profile |
|--------|---------------------|----------------|
| Scope | Minimum for cross-border exchange | Full national dataset |
| StopPlace | Basic: Name, Location | + Quay, AccessibilityAssessment, Equipment |
| Governance | Authority, Operator | + ResponsibilitySet, Contract |
| Accessibility | Recommended | Mandatory at StopPlace and Quay level |
| Fares | Basic structure | Full product hierarchy |

> ⚠️ **Note:** EPIP is the legal minimum. National authorities typically require the national profile (e.g. Nordic Profile), which is stricter. Always check your NAP's specific requirements.

See the [Decision Makers](../DecisionMakers/DecisionMakers_Guide.md) guide (section 4) for a broader regulatory context overview.

---

## 4. 📐 Mapping Requirements to NeTEx

The table below maps each regulation requirement to the NeTEx frame and objects you need, with links to the guide that covers each topic in detail:

| Regulation Requirement | NeTEx Frame | Key Objects | Guide |
|------------------------|-------------|-------------|-------|
| Who operates | ResourceFrame | Authority, Operator, ResponsibilitySet | [OrganisationalGovernance](../OrganisationalGovernance/OrganisationalGovernance_Guide.md) |
| Where services stop | SiteFrame | StopPlace, Quay, PassengerStopAssignment | [StopInfrastructure](../StopInfrastructure/StopInfrastructure_Guide.md) |
| When services run | ServiceCalendarFrame | DayType, OperatingPeriod | [JourneyLifecycle](../JourneyLifecycle/JourneyLifecycle_Guide.md) |
| What services exist | ServiceFrame | Line, Route, JourneyPattern | [JourneyLifecycle](../JourneyLifecycle/JourneyLifecycle_Guide.md) |
| Timetables | TimetableFrame | ServiceJourney, TimetabledPassingTime | [JourneyLifecycle](../JourneyLifecycle/JourneyLifecycle_Guide.md) |
| Accessibility | SiteFrame | AccessibilityAssessment, AccessibilityLimitation | [Accessibility](../Accessibility/Accessibility_Guide.md) |
| Fares (Priority B) | FareFrame | TariffZone, PreassignedFareProduct, SalesOfferPackage | [FareModelling](../FareModelling/FareModelling_Guide.md) |

The minimum compliant delivery for Priority A looks like this:

```text
PublicationDelivery
 └── CompositeFrame
      ├── ResourceFrame ........... Authority + Operator
      ├── SiteFrame ............... StopPlace + Quay + Accessibility
      ├── ServiceCalendarFrame .... DayType
      ├── ServiceFrame ............ Line + Route + JourneyPattern
      └── TimetableFrame .......... ServiceJourney + passing times
```

---

## 5. 🚌 What a Bus Operator Needs to Produce

Follow these steps to build a compliant dataset. Each step links to the guide that walks you through it:

1. **Define your organisation** — Create Authority and Operator in a ResourceFrame. See [OrganisationalGovernance](../OrganisationalGovernance/OrganisationalGovernance_Guide.md).

2. **Register your stops** — Model each stop as a StopPlace with Quays in a SiteFrame. Add an AccessibilityAssessment to each. See [StopInfrastructure](../StopInfrastructure/StopInfrastructure_Guide.md) and [Accessibility](../Accessibility/Accessibility_Guide.md).

3. **Define your calendar** — Create DayTypes for weekdays, weekends, and holidays in a ServiceCalendarFrame. See [JourneyLifecycle](../JourneyLifecycle/JourneyLifecycle_Guide.md).

4. **Model your network** — Define Line, Route, and JourneyPattern in a ServiceFrame. See [JourneyLifecycle](../JourneyLifecycle/JourneyLifecycle_Guide.md).

5. **Build your timetable** — Create ServiceJourneys with TimetabledPassingTimes in a TimetableFrame. See [JourneyLifecycle](../JourneyLifecycle/JourneyLifecycle_Guide.md).

6. **Validate against the schema** — Run XSD validation and profile checks before submission. See [Validation](../Validation/Validation.md).

7. **Submit to your NAP** — Package and upload your delivery (see next section).

> 💡 **Tip:** You do not need to produce everything at once. Start with stops and the network (steps 1–4), then add timetables. This gives you a valid, useful dataset even before the full production chain is complete.

See [Get Started](../GetStarted/GetStarted_Guide.md) for the basics of NeTEx document structure.

---

## 6. 🌐 NAP Submission Workflow

A National Access Point (NAP) is a national portal where transport data is published and made available to multimodal journey planners. Each EU member state operates its own NAP (e.g. data.entur.no in Norway, BODS in the UK, transport.data.gouv.fr in France).

The general submission workflow:

```text
1. PRODUCE          2. VALIDATE           3. SUBMIT          4. PUBLISH
   NeTEx XML   -->    Schema + Profile   -->  NAP portal   -->  Available to
                      validation               or API           journey planners
```

Validation is critical before submission — invalid data may be rejected outright or cause downstream errors in journey planners. Some NAPs accept only specific profiles, so check your NAP's documentation for format and profile requirements.

> ⚠️ **Note:** NAP submission processes vary significantly between countries. This guide covers the general workflow; consult your national NAP documentation for specific requirements, APIs, and delivery schedules.

---

## 7. ✅ Best Practices

1. **Start with Priority A data.** Stops, lines, timetables, and accessibility cover the core regulatory requirement and deliver immediate value.
2. **Validate early and often.** Run schema validation after every change, not just before submission. See [Validation](../Validation/Validation.md).
3. **Use the profile's cardinality rules.** Do not omit mandatory elements — the NAP will likely reject incomplete data.
4. **Version your data.** Every object should carry a `version` attribute so downstream systems can detect changes.
5. **Reuse existing stop registries.** Do not create duplicate StopPlace IDs if your country has a national stop registry (e.g. NSR in Norway).
6. **Follow the existing guides.** Each step in the production chain is documented in detail in a dedicated guide — use them rather than reinventing the structure.

---

## 8. 🔗 Related Resources

### Guides
- [Get Started](../GetStarted/GetStarted_Guide.md) — Introduction to NeTEx document structure
- [Journey Lifecycle](../JourneyLifecycle/JourneyLifecycle_Guide.md) — The core data chain from Line to ServiceJourney
- [Stop Infrastructure](../StopInfrastructure/StopInfrastructure_Guide.md) — StopPlace, Quay, and PassengerStopAssignment
- [Accessibility](../Accessibility/Accessibility_Guide.md) — AccessibilityAssessment and equipment
- [Organisational Governance](../OrganisationalGovernance/OrganisationalGovernance_Guide.md) — Authority, Operator, and ResponsibilitySet
- [Fare Modelling](../FareModelling/FareModelling_Guide.md) — Products, zones, and tariffs (Priority B)
- [Validation](../Validation/Validation.md) — Schema validation and common errors
- [Decision Makers](../DecisionMakers/DecisionMakers_Guide.md) — NeTEx overview and regulatory context

### External
- [EU Delegated Regulation 2017/1926](https://eur-lex.europa.eu/eli/reg_del/2017/1926/oj) — Full legal text
- [NeTEx CEN Standard](https://www.netex-cen.eu/) — Official specification
- [EPIP Documentation](https://netex-cen.eu/?page_id=29) — European Passenger Information Profile
