
# wf4ever:File (Datatype)

`ogc.bbr.wf4ever.wf4ever.File` *v1.0*

A file artifact - a specialization of wfdesc:Artifact representing a file-based data entity used or produced by workflow execution.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wf4ever:File

## Description

A **File** is a specialization of `wfdesc:Artifact` representing a file-based data entity. Files are commonly used as inputs and outputs in scientific workflows, and this class provides semantic precision for file-typed artifacts.

## Relationship to Base Classes

```
wfdesc:Artifact
  └─ wf4ever:File
```

A File is a specific type of Artifact that represents file-system based data, as opposed to in-memory values or streamed data.

## Properties

Inherits all properties from `wfdesc:Artifact`, plus:

- `@type` : Must include "File" (can be multi-typed with wfprov:Artifact, etc.)
- `basename` : The base filename (without directory path)
- `checksum` : File integrity checksum (e.g., SHA256, MD5)
- `size` : File size in bytes
- `format` : Media type or file format (e.g., "text/csv", "image/tiff")

## Usage in CWL Provenance

In CWLProv (Common Workflow Language Provenance), files are dual-typed to combine provenance semantics with artifact type precision:

```json
{
  "@id": "id:4d15cb37-a4a3-4170-a7aa-529399cb4753",
  "prov:type": [
    {
      "$": "wfprov:Artifact",
      "type": "prov:QUALIFIED_NAME"
    },
    {
      "$": "wf4ever:File",
      "type": "prov:QUALIFIED_NAME"
    }
  ],
  "cwlprov:basename": "catalog.json"
}
```

## Common File Types in Workflows

- **Data files**: CSV, JSON, GeoTIFF, NetCDF, HDF5
- **Configuration files**: YAML, XML, INI
- **Scripts**: Python, R, Shell scripts
- **Documents**: PDF, HTML, Markdown
- **Images**: PNG, JPEG, TIFF (for raster data)

## Relations

- Subclass of `wfdesc:Artifact`
- Can be used in `wfprov:Artifact` contexts for provenance tracking
- Can be aggregated in `ro:Folder` via `ro:FolderEntry`


## Examples

### Simple JSON File
#### json
```json
{
  "@id": "id:4d15cb37-a4a3-4170-a7aa-529399cb4753",
  "@type": ["wfprov:Artifact", "File"],
  "basename": "catalog.json",
  "format": "application/json"
}

```


### GeoTIFF File with Checksum
#### json
```json
{
  "@id": "id:04c0ef72-14c0-4248-b042-6dec318c56c5",
  "@type": ["wfprov:Artifact", "File"],
  "basename": "mangrove_mask.tif",
  "format": "image/tiff",
  "checksum": "sha1:0999fb93da76020eefac9eb02b1921cf7096b5fc"
}

```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A file artifact
type: object
properties:
  '@type':
    oneOf:
    - const: File
    - type: array
      contains:
        const: File
    description: Type must include File
  basename:
    type: string
    description: The base filename
  checksum:
    type: string
    description: File integrity checksum (e.g., SHA256)
  size:
    type: integer
    description: File size in bytes
  format:
    type: string
    description: Media type or file format
required:
- '@type'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/File/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/File/schema.yaml)

## Sources

* [Wf4Ever Ontology - File](http://purl.org/wf4ever/wf4ever#File)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wf4ever/File`

