# AlternativeName

## Structure Overview

```text
AlternativeName
  ├─ NameType (0..1)
  ├─ Name (1..1)
  └─ QualifierName (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| NameType | Enum | Classification of the alternative name (e.g., alias, translation, copy) | AlternativeName/NameType |
| Name | String | The alternative name text | AlternativeName/Name |
| QualifierName | String | Type or purpose of the alternative name (e.g., official, translation) | AlternativeName/QualifierName |
