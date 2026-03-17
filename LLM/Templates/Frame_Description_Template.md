# `<FrameName>` — Description Template

## Overview

This template defines the structure for all Frame description files in the NeTEx profile.
Frame descriptions are simpler than Object descriptions because Frames are containers that group
related Objects rather than carrying rich domain data themselves.

All description files must follow this 4-section format in the exact order specified below.

---

## Mandatory Section Order

**Sections 1–3 are required. Section 4 is optional.**
All sections must appear in this exact sequence.

---

## 1. Purpose

**Required.** A short (2–3 sentence) explanation of the frame's role, scope, and what kind of data it contains.
Should clarify where the frame sits in the NeTEx delivery structure (e.g., child of CompositeFrame).

**Example:**
> A **ServiceFrame** contains the network and route definitions for a public transport delivery. It groups Lines, Routes, JourneyPatterns, ScheduledStopPoints, and DestinationDisplays — the structural elements that describe where and how services run.

---

## 2. Contained Elements

**Required.** A bulleted list of the key collections and elements carried by this frame.
Each item should name the container element and briefly describe what it holds, with links to
the relevant Object Table files where they exist.

**Example:**
- **lines** – Collection of [Line](../../Objects/Line/Table_Line.md) definitions
- **routes** – Collection of [Route](../../Objects/Route/Table_Route.md) definitions
- **journeyPatterns** – Collection of [JourneyPattern](../../Objects/JourneyPattern/Table_JourneyPattern.md) definitions
- **scheduledStopPoints** – Collection of [ScheduledStopPoint](../../Objects/ScheduledStopPoint/Table_ScheduledStopPoint.md) definitions
- **destinationDisplays** – Collection of [DestinationDisplay](../../Objects/DestinationDisplay/Table_DestinationDisplay.md) definitions

---

## 3. Frame Relationships

**Required.** Describe how this frame relates to other frames in a typical NeTEx delivery.
Include which frames it depends on and which frames depend on it.

**Example:**
> ServiceFrame depends on **ResourceFrame** for Operator and Authority definitions.
> **TimetableFrame** depends on ServiceFrame for JourneyPatterns and Lines.
> All frames are typically wrapped in a **CompositeFrame** within a PublicationDelivery.

---

## 4. Usage Notes (optional)

**Optional.** Any additional guidance on how to use the frame correctly.
Include only when there are non-obvious constraints, ordering requirements, or common mistakes.

**Example:**
> - The ServiceFrame must always appear after ResourceFrame in the CompositeFrame when Operators are referenced by Lines.
> - A single delivery may contain multiple ServiceFrames if they cover different codespaces.

---

## Section Rules & Constraints

1. **Sections 1–3 are mandatory.** All must be present and in order.
2. **Section 4 is optional.** Omit if not relevant.
3. **No additional top-level sections.** Keep frame descriptions concise.
4. **Use relative markdown links** to reference Object Table files: `[ObjectName](../../Objects/ObjectName/Table_ObjectName.md)`
5. **Link to the frame's Table file** at the end of the description if one exists.

---

## Quality Checklist

Before finalizing a frame description file, verify:

- [ ] **Purpose** is 2–3 sentences and clearly states the frame's role
- [ ] **Contained Elements** lists all key collections from the XML example
- [ ] **Contained Elements** links to existing Object Table files where available
- [ ] **Frame Relationships** describes dependencies upstream and downstream
- [ ] **Usage Notes** (if present) provides actionable, non-obvious guidance
- [ ] **No sections beyond the 4 defined here**
- [ ] **All relative links** are functional
