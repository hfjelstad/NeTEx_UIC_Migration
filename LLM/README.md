# LLM Documentation Hub  
This folder defines the documentation conventions, rules, and templates used by both humans and AI agents when creating or updating documentation for the NeTEx profile in this repository.

The contents here describe **how documentation must be structured**, **how objects link to each other**, **how tables are generated**, and **how XML examples are constructed**.  
All agents and contributors must treat these rules as authoritative.

---

## 1. Purpose of this folder
The purpose of the `LLM/` folder is to provide a single, authoritative source for:

- documentation rules  
- generation rules  
- templates for new objects  
- standards for tables, structure overviews, and XML examples  
- naming conventions  
- cross-reference patterns  
- file and folder layout  

The agent must always consult this folder when reading, validating, or generating documentation.

---

## 2. Profiles

| ProfileCode | Profile Description |
| -- | -- |
| MIN | Minimum profile | 
| ERP | European Recomended Profile |
| NP | Nordic Profile |

## 3. Documentation Structure for Each Object

Every object under `Objects/<ObjectName>/` must contain the following files:

### 1. Example_<ObjectName>_<ProfileCode>.xml (at least one required)
- A XML example validated against the current XSD.
- All XML examples that use a ProfileCode and validate against the current XSD act as authoritative sources for determining the element order used in both the Structure Overview and the Table. Other XML files may appear for guidance or illustration but must not influence structural ordering.

### 2. Table_<ObjectName>.md (mandatory)

[Table template](../LLM/Templates/Object_Struture_and_Table_Template.md)

### 3. Description_<ObjectName>.md (mandatory)

[Description template](../LLM/Templates/Object_Description_Template.md)