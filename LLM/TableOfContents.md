# Profile Documentation v2 — Table of Contents

This document is the mandatory starting point for navigating and maintaining the documentation set. Use the links below to reach the master template, examples, and the Part 1 (NetworkDescription) object documentation.

Getting started
- Master template for object documentation: LLM/README.md
- Examples overview: LLM/TableOfExamples.md
- Validated examples list: TableOfValidatedExamples.md

Part 1 — NetworkDescription

Overview
- Scope: Topology and product structure of the network, including Network, Line and GroupOfLines objects.
- Outcome: Consistent descriptions, attribute tables and at least one ERP-coded XML example for each object.

Network
- Folder: Objects/Network/ (planned; to be added)
- Purpose: Top-level container describing a transport network and its context. If this folder is missing, add it following LLM/README.md.

Lines
- Object: Line
- Documentation
  - Description: Objects/Line/Description_Line.md
  - Attribute table: Objects/Line/Table_Line.md
  - XML example (ERP): Objects/Line/Example_Line.xml

Groups of Lines
- Object: GroupOfLines
- Documentation
  - Description: Objects/GroupOfLines/Description_GroupOfLines.md
  - Attribute table: Objects/GroupOfLines/Table_GroupOfLines.md
  - XML example (ERP): Objects/GroupOfLines/Example_GroupOfLines.xml
- Key elements (for quick orientation)
  - Definition: A GroupOfLines is a logical grouping of Line objects used to present or manage sets of services as a single unit (for example, branded service families, corridors or marketing bundles).
  - Element structure (typical):
    - GroupOfLines (id, version)
      - Name
      - PrivateCode (optional)
      - Members
        - LineRef (one or more)
      - KeyList (optional)
  - Core attributes: id (must use ERP codespace, e.g. erp:GroupOfLines:<LOCAL_ID>), version.
  - Typical usage: branding or marketing groupings, journey planning filters, operational/reporting bundles across multiple Line instances.
  - Examples: see Objects/GroupOfLines/Example_GroupOfLines.xml (ERP codespace).

Related material
- Coding conventions and formatting rules are defined by the master template: LLM/README.md (apply exactly as written).
- Example catalog: LLM/TableOfExamples.md
- List of validated examples: TableOfValidatedExamples.md

Maintenance notes
- When an object folder does not exist, create it and start with a .gitkeep file containing the text "tom". Replace or remove .gitkeep when actual documentation files are added.
- Ensure every object has: Description, Attribute Table, and at least one XML example using the ERP codespace.
