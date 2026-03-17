# FlexibleServiceProperties

## Structure Overview

```text
FlexibleServiceProperties
  ├─ @id (1..1)
  ├─ @version (1..1)
  └─ ValidBetween (0..1)
     ├─ FromDate (1..1)
     └─ ToDate (1..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the flexible service properties | FlexibleServiceProperties/@id |
| @version | String | Version number for change tracking | FlexibleServiceProperties/@version |
| ValidBetween | Period | Validity period for these properties | FlexibleServiceProperties/ValidBetween |
| FromDate | DateTime | Start date of the validity period | FlexibleServiceProperties/ValidBetween/FromDate |
| ToDate | DateTime | End date of the validity period | FlexibleServiceProperties/ValidBetween/ToDate |
