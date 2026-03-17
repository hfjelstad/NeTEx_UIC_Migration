# Line

## 1. Purpose
The **Line** represents a public transport service line within a ServiceFrame. It is a core organizational entity that groups together related routes and journeys providing the same public transport service (e.g., "Bus Line 5" or "Train Line 101"). A Line identifies the operator, provides visual presentation properties (colors), and serves as the container for route patterns and scheduled journeys.

## 2. Structure Overview
```
📄 Line
  ├─ 📄 @id (identifier, mandatory)
  ├─ 📄 @version (string)
  ├─ 📄 Name (mandatory)
  ├─ 🔗 OperatorRef (mandatory reference)
  └─ 📁 Presentation (optional)
     ├─ 📄 Colour (6-digit hex code)
     └─ 📄 TextColour (6-digit hex code)
```

## 3. Key Elements
- **Name**: Human-readable line identifier displayed in timetables and passenger information; must be unique within the service delivery scope.
- **OperatorRef**: Mandatory reference to the Operator responsible for running this Line; must resolve to an Operator defined in ResourceFrame.
- **Presentation**: Optional container for visual presentation properties; defines line color and text color for passenger-facing displays.
- **Colour**: Hexadecimal color code (6 uppercase digits without `#`) for the line's visual representation; e.g., `005EB8` for blue.
- **TextColour**: Hexadecimal color code for text displayed on the line; typically contrasts with Colour for readability; e.g., `FFFFFF` for white.

## 4. References
- [Operator](../Operator/Table_Operator.md) – Organization responsible for operating this Line
- [Route](../Route/Table_Route.md) – Geographic path definition for journeys on this Line
- [JourneyPattern](../JourneyPattern/Table_JourneyPattern.md) – Stop sequence patterns served by this Line

## 5. Usage Notes

### 5a. Consistency Rules
- A Line should have a unique Name within the scope of its Operator to avoid confusion in passenger communication and system references.
- The OperatorRef must be defined in ResourceFrame/organisations before the Line is referenced by Routes, JourneyPatterns, or ServiceJourneys.
- Presentation colors (Colour and TextColour) should be consistent across all visual touchpoints (websites, signage, information systems) to reinforce brand identity.

### 5b. Validation Requirements
- **Name is mandatory** – Every Line must have a Name element for public identification.
- **OperatorRef is mandatory** – Every Line must reference exactly one Operator with @ref attribute; cardinality is 1..1.
- **@id and @version are mandatory** – Must follow codespace conventions (e.g., `ERP:Line:1`); version typically "1" or incremental.
- **Colour format is strict** – If Presentation is used, Colour must be exactly 6 uppercase hexadecimal digits (0–9, A–F) without a leading # character.
- **TextColour format is strict** – Same format requirements as Colour; recommended to ensure text-to-background contrast for accessibility.

### 5c. Common Pitfalls
- **TransportMode confusion**: XML examples may show `<TransportMode>` directly under Line, but this is not permitted in the current XSD schema variant. Do NOT include TransportMode as a direct child; use alternative patterns if line classification is required.
- **TypeOfLineRef not supported**: The schema does not accept `TypeOfLineRef` directly under Line. If line type classification is needed, document it as a profile rule or use alternative constructs.
- **Presentation element mistakes**: Do NOT add `@id` or `@version` attributes to the Presentation element; it is a simple container with only child text elements.
- **Colour format errors**: Common mistakes include using lowercase hexadecimal (e.g., `005eb8` instead of `005EB8`), including a leading `#` (invalid), or using color names instead of hex codes (invalid).

## 6. Additional Information
See [Table_Line.md](Table_Line.md) for detailed attribute specifications, cardinality rules, and XSD constraints. See [Example_Line.xml](Example_Line.xml) for a complete, validated XML instance based on the ERP profile.
