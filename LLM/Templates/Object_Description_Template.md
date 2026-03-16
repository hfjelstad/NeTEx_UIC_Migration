# `<ObjectName>` — Description

## 1. Purpose
A short explanation of the object’s intent, scope, and the role it plays within the NeTEx model.  
This text must be derived from the XML examples, the Structure Overview, and the Table.

## 2. Structure Overview
The Structure Overview provides a readable, icon‑based representation of the object's structure.
It must follow the ordering and hierarchy shown in `Table_<ObjectName>.md`.

### Structure Overview — `<ObjectName>`
```text
📄 @id
📄 @version
📄 <ElementA>
📁 <ContainerA>
└── 📄 <ChildElement> (0..*)
🔗 <ReferenceElement/@ref>
```

## 3. Key Elements
Summarize the key elements and their functional meaning.
Do not duplicate the entire table.

## 4. References
List all external references shown in the table and provide brief explanations.

## 5. Usage Notes (optional)
Optional modeling details, recommended usage, or clarifications.

## 6. Additional Information (optional)
Any extra information relevant to understanding the object.

### Section Rules
Only the numbered top‑level sections defined in this template may be used.  
Sections marked as optional may be omitted entirely when not relevant, but the numbering of other sections must remain unchanged.
