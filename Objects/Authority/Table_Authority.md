## Structure Overview

```text
Authority
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ LegalName (0..1)
 ├─ ShortName (0..1)
 ├─ CompanyNumber (0..1)
 ├─ Description (0..1)
 ├─ ContactDetails (0..1)
 │  ├─ Phone (0..1)
 │  └─ Url (0..1)
 ├─ OrganisationType (0..1)
 └─ ResponsibilitySetRef/@ref (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the Authority | Authority/@id |
| @version | String | Version label | Authority/@version |
| Name | String | Name of the Authority | Authority/Name |
| LegalName | String | Official legal name of the authority | Authority/LegalName |
| ShortName | String | Short name or abbreviation | Authority/ShortName |
| CompanyNumber | String | Official company registration number | Authority/CompanyNumber |
| Description | String | Description of the Authority | Authority/Description |
| ContactDetails | Element | Contact information | Authority/ContactDetails |
| Phone | String | Contact telephone number | Authority/ContactDetails/Phone |
| Url | String | Website URL | Authority/ContactDetails/Url |
| OrganisationType | Enum | Type of organisation (always "authority" for Authority) | Authority/OrganisationType |
| [ResponsibilitySet](../ResponsibilitySet/Table_ResponsibilitySet.md)@ref | Reference | Reference to a ResponsibilitySet defining roles | Authority/ResponsibilitySetRef/@ref |
