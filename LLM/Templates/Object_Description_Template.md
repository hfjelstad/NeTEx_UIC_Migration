# `<ObjectName>` — Description

## 1. Purpose
A short explanation of the object’s intent, scope, and the role it plays within the NeTEx model.  
This text must be derived from the XML examples, the Structure Overview, and the Table.


## 2. Structure Overview
A human‑friendly outline of the object’s structure as defined in the `Table_<ObjectName>.md` file.  
This overview must visually reflect the same ordering and element hierarchy as the table.

Use the following style with icons to indicate semantic roles:

- 📄 = simple element or attribute  
- 🔗 = reference to another object (Ref element)  
- 📁 = container element  

### Structure Overview — <ObjectName>

```text
📄 @id  
📄 @version  
📄 <ElementA>  
📄 <ElementB>  
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