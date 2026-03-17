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

---

## 3. Quick Navigation

**Essential Index Files:**

- [TableOfContent.md](../TableOfContent.md) – Complete index of all Objects, Frames, and Guides with descriptions
- [TableOfExamples.md](../TableOfExamples.md) – Searchable list of all XML examples with brief descriptions

**Reference Materials:**

- [Templates/](Templates/) – Templates for creating new documentation
- [../../Objects/](../../Objects/) – All Object documentation
- [../../Frames/](../../Frames/) – All Frame documentation
- [../../Guides/](../../Guides/) – Guidelines and best practices

Use these files to quickly locate documentation, explore examples, and understand the overall structure of the NeTEx profile.

---

## 4. Documentation Structure for Each Object

Every object under `Objects/<ObjectName>/` must contain the following files:

### 4.1. Example_<ObjectName>_<ProfileCode>.xml (at least one required)
- A XML example validated against the current XSD.
- All XML examples that use a ProfileCode and validate against the current XSD act as authoritative sources for determining the element order used in both the Structure Overview and the Table. Other XML files may appear for guidance or illustration but must not influence structural ordering.

### 4.2. `Table_<ObjectName>.md` (mandatory)

The structural specification file. See [Object Table Template](Templates/Object_Structure_and_Table_Template.md) for detailed guidance.

Must contain a Structure Overview and flat table with all elements, attributes, references, and cardinality across all profiles.

### 4.3. `Description_<ObjectName>.md` (mandatory)

The semantic explanation file. See [Object Description Template](Templates/Object_Description_Template.md) for detailed guidance.

Must explain the object's purpose, key relationships, and usage patterns with reference links to related objects.

---

## 5. Documentation Structure for Frames

Every frame under `Frames/<FrameName>/` must contain the following files:

### 5.1. `Description_<FrameName>.md` (mandatory)

A human‑readable explanation of the frame including:
- purpose and role in the NeTEx data model,
- contained elements and sub-frames,
- relationships to other frames,
- typical usage patterns.

### 5.2. `Example_<FrameName>.xml` (at least one required)

A validated XML example demonstrating the frame structure and element composition.

---

## 6. Naming Conventions & File Organization

### File Naming

- **Example files:** `Example_<ObjectName>.xml` or `Example_<ObjectName>_<ProfileCode>.xml`  
- **Description files:** `Description_<ObjectName>.md`
- **Table files:** `Table_<ObjectName>.md`

### Folder Organization

```
Objects/
├── <ObjectName>/
│   ├── Description_<ObjectName>.md
│   ├── Table_<ObjectName>.md
│   └── Example_<ObjectName>_<ProfileCode>.xml (one or more)
└── ...

Frames/
├── <FrameName>/
│   ├── Description_<FrameName>.md
│   └── Example_<FrameName>.xml
└── ...
```

### Cross-Referencing

- Use relative markdown links to reference object tables: `[ObjectName](../ObjectName/Table_ObjectName.md)`
- Use consistent capitalization matching the NeTEx element names
- Always link from descriptions to examples and table files

---

## 7. Validation & Quality Assurance

- All XML examples must validate against the current NeTEx XSD
- Tables must stay synchronized with their corresponding XML examples
- Descriptions must reference actual elements from the table
- Cross-reference links must be relative and point to existing files
- ProfileCode examples are authoritative for element ordering