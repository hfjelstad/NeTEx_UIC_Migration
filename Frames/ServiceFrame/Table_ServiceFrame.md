# ServiceFrame

## Structure Overview

```text
ServiceFrame
 ├─ @id (1..1)
 ├─ @version (1..1)
 └─ lines (0..1)
     └─ Line (0..n)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the ServiceFrame | ServiceFrame/@id |
| @version | String | Version number for change tracking | ServiceFrame/@version |
| lines | Container | Collection of Line definitions | ServiceFrame/lines |
| [Line](../../Objects/Line/Table_Line.md) | Element | Transport line with name, public code, and operator reference | ServiceFrame/lines/Line |
