## Structural Overview

This overview shows the primary relationships of DatedServiceJourney and where the referenced objects are documented.

```
DatedServiceJourney
├─ ServiceJourneyRef (1) → ServiceJourney
├─ OperatingPeriodRef (0..1) → OperatingPeriod
├─ DayTypeRef (0..*) → DayType
├─ BlockRef (0..1) → TrainBlock
└─ ResponsibilitySetRef (0..1) → ResponsibilitySet
```

Related object documentation:
- ServiceJourney: ../ServiceJourney/Description_ServiceJourney.md
- OperatingPeriod: ../OperatingPeriod/Description_OperatingPeriod.md
- DayType: ../DayType/Description_DayType.md
- TrainBlock: ../TrainBlock/Description_TrainBlock.md
- ResponsibilitySet: ../ResponsibilitySet/Description_ResponsibilitySet.md

Legend:
- (1) means required, (0..1) optional, (0..*) zero or more.
- “Ref” indicates a reference to another object defined elsewhere in the profile.

---

<!-- Existing content below remains unchanged -->
