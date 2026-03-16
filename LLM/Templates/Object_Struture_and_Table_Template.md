## 1. Structure Overview (placed at the top of Table_<ObjectName>.md)
The Structure Overview must:
- follow the exact element order from the XML examples,
- show nesting using a monospace tree diagram,
- use box‑drawing symbols for clarity and consistency,
- list attributes inline using `ElementName/@attribute`,
- show multiplicities only when meaningful (e.g., (0..*), (1..*)),
- contain no descriptions or comments—structure only.

### Structure Overview Template
```text
<ObjectName>
 ├─ @id
 ├─ @version
 ├─ <ElementA>
 ├─ <ElementB>
 ├─ <ContainerA>
 │   └─ <ChildElement> (0..*)
 └─ <ReferenceElement/@ref>
 ```

## 2. `Table_<ObjectName>.md` (mandatory)

The flat table provides a normalized, machine‑readable representation of the object's structure.  
It must always be placed below the Structure Overview.

### Required Columns
The table must always contain the following base columns, in this order:

Element | Type | Description | Path

In addition, the table must include one column for each ProfileCode for which an
`Example_<ObjectName>_<ProfileCode>.xml` file exists in the object folder.

These profile columns must use the ProfileCode as the column header.

Each ProfileCode column must describe the cardinality for that profile as defined by the
corresponding XML example. If a profile example exists but a particular XML element is not
present in that example, the column must still be included and the value for that row left empty


### Rules
- **Element** must contain only the element name or attribute (e.g. `ArrivalTime`, `StopPointInJourneyPatternRef/@ref`).  
  No nesting or path notation is allowed here.
  
- **Cross‑references** must be written using relative links.  
  The link wraps the referenced object name, and `@ref` must appear *after* the link.  
  Example:  
  `[JourneyPattern](../JourneyPattern/Table_JourneyPattern.md/)@ref`

- **Type** must reflect the datatype or reference type used in the XML examples and NeTEx model.

- **Description** must briefly describe the purpose or meaning of the element, based on the XML and its role in the model.

- **Path** must contain the full hierarchical structure using slash notation  
  (e.g. `passingTimes/TimetabledPassingTime/ArrivalTime`).

### Additional Requirements
- All columns must be present for every row.  
- Attributes must appear with an `@` prefix.  
- The structure, order, and presence of elements must match the XML examples.  
- The table and Structure Overview must always remain synchronized.