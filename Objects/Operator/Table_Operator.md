## Structure Overview

```text
Operator
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ ShortName (0..1)
 ├─ ContactDetails (0..1)
 ├─ OrganisationType (0..1)
 ├─ AuthorityRef/@ref (0..1)
 └─ ResponsibilitySetRef/@ref (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the Operator | Operator/@id |
| @version | String | Version label | Operator/@version |
| Name | String | Name of the Operator organisation | Operator/Name |
| ShortName | String | Abbreviated name | Operator/ShortName |
| ContactDetails | Element | Contact information (phone, email, website) | Operator/ContactDetails |
| OrganisationType | String | Type of organisation (e.g., company, cooperative) | Operator/OrganisationType |
| [Authority](../Authority/Table_Authority.md)@ref | Reference | Reference to the contracting Authority | Operator/AuthorityRef/@ref |
| [ResponsibilitySet](../ResponsibilitySet/Table_ResponsibilitySet.md)@ref | Reference | Reference to a ResponsibilitySet defining roles | Operator/ResponsibilitySetRef/@ref |
