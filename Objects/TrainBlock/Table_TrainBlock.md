## Structure Overview

```text
Block (TrainBlock)
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (0..1)
 ├─ PublicCode (0..1)
 └─ OperatorRef/@ref (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the TrainBlock | Block/@id |
| @version | String | Version label | Block/@version |
| Name | String | Human-readable label | Block/Name |
| PublicCode | String | Short operational communication code | Block/PublicCode |
| [Operator](../Operator/Table_Operator.md)@ref | Reference | Reference to the operating organisation | Block/OperatorRef/@ref |
