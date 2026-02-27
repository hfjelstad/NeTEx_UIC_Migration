# DatedServiceJourney.OperatingDayRef – Profile Rule Harmonisation (2026-02-27)

Decision: Alternative (1)
- The profile explicitly allows cross-frame resolution for OperatingDayRef within the same CompositeFrame. A DatedServiceJourney in a TimetableFrame MAY reference an OperatingDay defined in a ServiceCalendarFrame, provided both frames are members of the same CompositeFrame.

Field table correction (OperatingDayRef)
- Replace previous wording "MUST resolve within the same TimetableFrame" with:
  - "MUST resolve within the same CompositeFrame; MAY resolve across frames (TimetableFrame → ServiceCalendarFrame). MUST NOT resolve outside the current CompositeFrame."

Validation rules (OperatingDayRef)
- If present, OperatingDayRef MUST reference an existing OperatingDay with a matching id within the same CompositeFrame.
- Cross-frame reference is permitted only within the CompositeFrame that contains the DatedServiceJourney. Referencing OperatingDay from a different CompositeFrame is not allowed.
- Codespace: All identifiers in examples use the ERP codespace.

Examples
- Added example that demonstrates cross-frame resolution: Objects/DatedServiceJourney/Example_DatedServiceJourney_Extended_05_CrossFrame_OperatingDayRef.xml
- The example defines OperatingDay in a ServiceCalendarFrame and references it from a DatedServiceJourney in a TimetableFrame under the same CompositeFrame.

Implementation note (XSD/model)
- NeTEx allows references between objects contained by the same CompositeFrame. This clarification aligns the field table with the frame model and avoids requiring a local OperatingDay inside TimetableFrame.
