## Structure Overview

```text
Operator
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ Name (1..1)
 ├─ CompanyNumber (0..1)
 ├─ ShortName (0..1)
 ├─ LegalName (0..1)
 ├─ ContactDetails (0..1)
 │  ├─ Phone (0..1)
 │  └─ Url (0..1)
 ├─ CustomerServiceContactDetails (0..1)
 │  ├─ Email (0..1)
 │  ├─ Phone (0..1)
 │  └─ Url (0..1)
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
| CompanyNumber | String | Official company registration number | Operator/CompanyNumber |
| ShortName | String | Abbreviated name | Operator/ShortName |
| LegalName | String | Official legal name of the operator | Operator/LegalName |
| ContactDetails | Element | Contact information (phone, email, website) | Operator/ContactDetails |
| Phone | String | Contact telephone number | Operator/ContactDetails/Phone |
| Url | String | Website URL | Operator/ContactDetails/Url |
| CustomerServiceContactDetails | Element | Public-facing customer service contact details | Operator/CustomerServiceContactDetails |
| Email | String | Customer service email | Operator/CustomerServiceContactDetails/Email |
| Phone | String | Customer service phone | Operator/CustomerServiceContactDetails/Phone |
| Url | String | Customer service URL | Operator/CustomerServiceContactDetails/Url |
| OrganisationType | String | Type of organisation (e.g., company, cooperative) | Operator/OrganisationType |
| [Authority](../Authority/Table_Authority.md)@ref | Reference | Reference to the contracting Authority | Operator/AuthorityRef/@ref |
| [ResponsibilitySet](../ResponsibilitySet/Table_ResponsibilitySet.md)@ref | Reference | Reference to a ResponsibilitySet defining roles | Operator/ResponsibilitySetRef/@ref |
