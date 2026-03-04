| Field | Description | Cardinality | Data type | Notes |
|-------|-------------|-------------|-----------|-------|
| id | Globally unique identifier for the GroupOfLines in the ERP codespace. | 1..1 | xs:string | Format: ERP:GroupOfLines:<local_id> |
| version | Version of the GroupOfLines. | 1..1 | xs:string | Increment when updating the object. |
| Name | Public name of the group. | 0..1 | xs:string | Human readable. |
| ShortName | Short public name or label. | 0..1 | xs:string | Optional. |
| Description | Description of purpose and content. | 0..1 | xs:string | Back-office information. |
| PrivateCode | Private back-office code. | 0..1 | xs:string | Optional. |
| members | Container of line members. | 1..1 | members | Contains one or more LineRef elements. |
| LineRef/@ref | Reference to a Line that is a member. | 1..n | xs:anyURI | Must reference an existing Line id. |
| LineRef/@version | Version of referenced Line. | 0..1 | xs:string | Should equal the version of the referenced Line. |