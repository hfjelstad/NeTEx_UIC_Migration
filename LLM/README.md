# LLM Documentation Hub  
This folder defines the documentation conventions, rules, and templates used by both humans and AI agents when creating or updating documentation for the NeTEx profile in this repository.

The contents here describe 
**how documentation must be structured**,
**how objects link to each other**, 
**how tables are generated**, and **how XML examples are constructed**.

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

### 3.1. Example_<ObjectName>_<ProfileCode>.xml (at least one required)
- A XML example validated against the current XSD.
- All XML examples that use a ProfileCode and validate against the current XSD act as authoritative sources for determining the element order used in both the Structure Overview and the Table. Other XML files may appear for guidance or illustration but must not influence structural ordering.

### 3.2. `Table_<ObjectName>.md` (mandatory)

[Object Table Template](../LLM/Templates/Object_Struture_and_Table_Template.md) 

The table file defines the complete structural specification of the object.  
It includes:

- a Structure Overview showing the hierarchical element layout,
- a flat table listing all elements, attributes, references, and cardinalities,
- relative links to referenced object tables,
- canonical paths showing where each element appears.

This file is the authoritative structural representation of the object and must stay 
synchronized with its XML examples.

### 3.3. `Description_<ObjectName>.md` (mandatory)

[Object Description Template](../LLM/Templates/Object_Description_Template.md)

A human‑readable explanation of the object. Includes:
- purpose and role in the model,
- an icon‑based summary structure,
- key elements and relationships,
- references to related objects,
- links to example XML files.

This file explains the semantics and usage of the object as defined in the Table.
