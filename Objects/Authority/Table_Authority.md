## Structure Overview

```text
Authority
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ ShortName (0..1)
 ├─ Description (0..1)
 ├─ ContactDetails (0..1)
 └─ ResponsibilitySetRef/@ref (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the Authority | Authority/@id |
| @version | String | Version label | Authority/@version |
| Name | String | Name of the Authority | Authority/Name |
| ShortName | String | Short name or abbreviation | Authority/ShortName |
| Description | String | Description of the Authority | Authority/Description |
| ContactDetails | Element | Contact information | Authority/ContactDetails |
| [ResponsibilitySet](../ResponsibilitySet/Table_ResponsibilitySet.md)@ref | Reference | Reference to a ResponsibilitySet defining roles | Authority/ResponsibilitySetRef/@ref |
