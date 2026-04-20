<!-- LLM AGENT: Use LLM/README.md as startingpoint  -->
# UIC EDIFACT to NeTEx Migration

![Urban transit at Jernbanetorget, Oslo](assets/images/Jernbanetorget.png)

A documentation hub for migrating **UIC EDIFACT railway timetable data** (SKDUPD/TSDUPD) to [NeTEx](https://github.com/NeTEx-CEN/NeTEx) XML, aligned with the **Nordic Profile**. Includes a step-by-step migration guide, segment-by-segment mapping, production examples, and a complete NeTEx reference library.

- 🚂 **Migrate** UIC EDIFACT schedules to NeTEx with concrete mapping guidance
- 🏷️ **Follow** Nordic Profile conventions for codespaces, IDs, and data ownership
- 🗂️ **Explore** validated XML examples built against the official XSD
- 🔎 **Reference** NeTEx frames, objects, element ordering, and cardinality

---

## 🚀 Start here

**Migrating from EDIFACT?** Go directly to the [**UIC EDIFACT Migration Guide**](Guides/UIC_EDIFACT_Migration/UIC_EDIFACT_Migration_Guide.md) — it maps every EDIFACT segment to NeTEx, provides a four-phase workflow, and includes before/after examples from real production data.

**New to NeTEx?** Start with the [**Get Started guide**](Guides/GetStarted/GetStarted_Guide.md) and the [**Network Timetable guide**](Guides/NetworkTimetable/NetworkTimetable_Guide.md) to understand frames, objects, and file structure before diving into the migration.

**Looking for a specific element?** Jump to the [**Table of Contents**](LLM/Indexes/TableOfContent.md) to find any frame, object, or guide.

---

## 🎯 What's Inside

### Migration

The [UIC EDIFACT Migration Guide](Guides/UIC_EDIFACT_Migration/UIC_EDIFACT_Migration_Guide.md) covers:

- Segment-by-segment mapping (PRD → ServiceJourney, POR → TimetabledPassingTime, POP → OperatingDay, etc.)
- Code translation tables for transport modes, brands, facilities, and boarding restrictions
- Nordic Profile conventions: operator codespaces, RICS codes, TypeOfService, external registry references
- File structure: shared data file + per-line timetable files
- Production examples from Finnish Railways (VR)

### NeTEx Reference Library

For every NeTEx frame and object:

- **`Description`** — purpose, structure overview, key elements, and relationships
- **`Table`** — element-level specification with types, cardinality per profile, and XSD paths
- **`Example`** — XML examples validated against the NeTEx 2.0 XSD

### Guides

Topic guides covering [stop infrastructure](Guides/StopInfrastructure/StopInfrastructure_Guide.md), [journey lifecycle](Guides/JourneyLifecycle/JourneyLifecycle_Guide.md), [calendar modelling](Guides/Calendar/Calendar_Guide.md), [vehicle scheduling](Guides/VehicleScheduling/VehicleScheduling_Guide.md), [interchange](Guides/InterchangeOnly/Interchange_Guide.md), [validation](Guides/Validation/Validation.md), and more — see the sidebar for the full list.

---

## 🗂️ Documentation Structure

```
📚 Guides
 └── UIC_EDIFACT_Migration/       ← Migration guide + EDIFACT examples
 └── <GuideName>/                 ← Topic guides (calendar, stops, journeys, …)

🏗️ Frames
 └── <FrameName>/
      ├── Description_<FrameName>.md
      ├── Table_<FrameName>.md
      └── Example_<FrameName>.xml

📦 Objects
 └── <ObjectName>/
      ├── Description_<ObjectName>.md
      ├── Table_<ObjectName>.md
      └── Example_<ObjectName>_<Profile>.xml

🤖 LLM
 └── Indexes/                     ← Ontologies, table of contents, example index
 └── AgentGuides/                 ← Operational guides for LLM agents
 └── Templates/                   ← Templates for new documentation
```
