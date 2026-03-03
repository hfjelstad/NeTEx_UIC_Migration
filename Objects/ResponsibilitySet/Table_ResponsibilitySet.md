# ResponsibilitySet – Structure Table

| Element | Type | Cardinality | Notes |
|---|---|---|---|
| ResponsibilitySet | Class | 1 | Container for role assignments that define responsibilities. Keys: id, version. Placement: ResourceFrame. |
| members | Container | 0..1 | Holds ResponsibilityRoleAssignment elements. |
| ResponsibilityRoleAssignment | Class | 0..* | Associates a responsibility role with a responsible organisation. Uses OrganisationRef. |
| ResponsibleOrganisationRef | Reference | 1 | Reference to an Authority or an Operator (or other Organisation). |
| TypeOfResponsibilityRoleRef | Reference | 0..1 | Optional reference to the role type that qualifies the responsibility. |
| ResponsibilitySetAssignment | Class | 0..* | Binds a ResponsibilitySet to a scope (e.g., a Frame). Uses ResponsibilitySetRef and may include ContractRef. Typically placed under ResourceFrame.responsibilitySetAssignments. |
| ResponsibilitySetRef | Reference | 1 | Reference used from ResponsibilitySetAssignment to the ResponsibilitySet. |
| ContractRef | Reference | 0..1 | Optional reference to a Contract under which the responsibility applies. |
| ResourceFrame | Frame | 1 | Typical placement for ResponsibilitySet and ResponsibilitySetAssignment. |
