# Guideline — Folder structure and filenames for NeTEx deliveries

This guideline defines a consistent folder layout, file naming, packaging, and validation conventions for NeTEx deliveries. It aligns object documentation resources with the existing conventions used in this repository (Table_*, Example_*, Description_*). All documentation and file names should be in English unless a specific external requirement dictates otherwise.

## 1. Recommended root structure of a delivery folder

Root folder example name: "TEST_LLM/" (use a meaningful package name for production deliveries).

Top-level files in root:
- manifest.json
- checksums.sha256

Subfolders:
- 00_Metadata
- 01_XSD
- 02_Profile
- 03_Objects
  - Line
  - Route
  - JourneyPattern
  - ServiceJourney
  - Timetable
- 04_PublicationDelivery
- 05_Validation
- 06_Attachments

Compact directory tree example:

```
TEST_LLM/
├── manifest.json
├── checksums.sha256
├── 00_Metadata/
├── 01_XSD/
├── 02_Profile/
├── 03_Objects/
│   ├── Line/
│   ├── Route/
│   ├── JourneyPattern/
│   ├── ServiceJourney/
│   └── Timetable/
├── 04_PublicationDelivery/
├── 05_Validation/
└── 06_Attachments/
```

## 2. Naming standard

2.1 PublicationDelivery files (in 04_PublicationDelivery):
- Pattern: `PD_{Codespace}_{Scope}_{YYYYMMDDThhmmssZ}.xml`
  - Codespace: organizational codespace, e.g., `ERP`.
  - Scope: business or environment scope, e.g., line set, region, or environment tag.
  - Timestamp: UTC in ISO 8601 basic time, e.g., `20250131T123456Z`.
- Examples:
  - `PD_ERP_DEV_20250131T123456Z.xml`
  - `PD_ERP_PROD_20250131T123456Z.xml`

2.2 Object resources (in 03_Objects/{Object}):
- Use the established repository naming scheme and keep casing consistent with object names.
- Files per object:
  - `Description_{Object}.md`
  - `Table_{Object}.md`
  - `Example_{Object}.xml`
- Examples:
  - `03_Objects/JourneyPattern/Description_JourneyPattern.md`
  - `03_Objects/JourneyPattern/Table_JourneyPattern.md`
  - `03_Objects/JourneyPattern/Example_JourneyPattern.xml`
- Notes:
  - Align content with the master template in `Objects/README.md` for descriptions, tables, and XML examples.
  - Use codespace `ERP` in examples unless otherwise required.

2.3 Codespace and environment tags:
- Codespace (e.g., `ERP`) must appear in PublicationDelivery filenames and be used in the XML (ParticipantRef).
- Recommended environment tags: `DEV`, `TEST`, `PROD`.

## 3. Packaging convention

- Package the complete delivery folder as a ZIP file: `{PackageName}_{YYYYMMDD}.zip`.
  - Example: `TEST_LLM_20250131.zip`.
- PublicationDelivery requirements:
  - Use the NeTEx default namespace on the root element.
  - Wrap content in a `PublicationDelivery`.
  - Set `ParticipantRef` to the chosen codespace (e.g., `ERP`).
  - Note: `JourneyPattern` elements are typically contained in a `ServiceFrame`.

## 4. Validation artifacts (05_Validation)

Include validation evidence to ensure reproducibility and auditability:
- Validation report(s) (human-readable summary in PDF/HTML and/or text).
- Schematron results (e.g., SVRL/XML) with timestamps.
- Clearly reference which profile(s) and schematron(s) were used. The profile definitions and schematron files or references should be placed in `02_Profile/` and named to indicate version and source.
  - Example profile references: `02_Profile/NetexProfile_ERP_v1.2/`, `02_Profile/Schematron/Netex_ERP_rules_v1.2.sch`.

## 5. Compact examples

5.1 Folder tree for "TEST_LLM": see section 1 for the compact tree.

5.2 Example PublicationDelivery header (using codespace `ERP`):

```xml
<PublicationDelivery
    xmlns="http://www.netex.org.uk/netex"
    version="1.09">
  <PublicationTimestamp>2025-01-31T12:34:56Z</PublicationTimestamp>
  <ParticipantRef>ERP</ParticipantRef>
  <Description>NeTEx delivery for TEST_LLM (DEV)</Description>
  <!-- Frames and data go here; JourneyPattern normally within ServiceFrame -->
</PublicationDelivery>
```

## 6. Alignment with existing object conventions

- Ensure naming strictly follows the `Table_*`, `Example_*`, and `Description_*` patterns for each object.
- When documenting objects (e.g., `JourneyPattern`), follow the master template in `Objects/README.md` for:
  - Folder structure
  - File naming
  - Required content (Description, Table, at least one XML example using codespace `ERP`)
  - Description and table formatting
  - XML example formatting

## 7. Checksums and manifest

7.1 Checksums:
- Use SHA-256 for all files included in the delivery (excluding the ZIP package itself). Store in `checksums.sha256`.
- Recommended line format: `{sha256}  {relative/path/to/file}`

7.2 Manifest (manifest.json):
- Provide a machine-readable list of delivered files with key metadata, e.g.:

```json
{
  "packageName": "TEST_LLM",
  "generatedAt": "2025-01-31T12:34:56Z",
  "codespace": "ERP",
  "environment": "DEV",
  "files": [
    {
      "path": "04_PublicationDelivery/PD_ERP_DEV_20250131T123456Z.xml",
      "size": 123456,
      "sha256": "0123456789abcdef..."
    },
    {
      "path": "03_Objects/JourneyPattern/Example_JourneyPattern.xml",
      "size": 2345,
      "sha256": "abcdef0123456789..."
    }
  ]
}
```

Adhering to these conventions will keep NeTEx deliveries predictable, verifiable, and easy to automate and validate across environments.
