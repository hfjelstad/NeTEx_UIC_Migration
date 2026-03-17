## Structure Overview

```text
Line
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ OperatorRef/@ref (1..1)
 └─ Presentation (0..1)
    ├─ Colour (0..1)
    └─ TextColour (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the Line (e.g., ERP:Line:5) | Line/@id |
| @version | String | Version label | Line/@version |
| Name | String | Human-readable line name | Line/Name |
| [Operator](../Operator/Table_Operator.md)@ref | Reference | Reference to the Operator running this Line | Line/OperatorRef/@ref |
| Colour | String | Line colour as 6-digit uppercase hex (e.g., 005EB8) | Line/Presentation/Colour |
| TextColour | String | Text colour as 6-digit uppercase hex (e.g., FFFFFF) | Line/Presentation/TextColour |
