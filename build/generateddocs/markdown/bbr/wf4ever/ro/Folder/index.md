
# ro:Folder (Datatype)

`ogc.bbr.wf4ever.ro.Folder` *v1.0*

A folder that organizes resources within a Research Object. Folders provide hierarchical structure, similar to filesystem directories, allowing logical grouping of related resources.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# ro:Folder

## Description

A **Folder** organizes resources within a Research Object. Folders provide a hierarchical structure, similar to file system directories, allowing logical grouping of related resources.

## Relations

- Contains `ro:FolderEntry` via `ore:aggregates`
- Can be aggregated in a `ro:ResearchObject`
- Can contain other Folders (recursive structure)

## Example

See the real-world example from a CWLProv execution showing a workflow output folder with multiple file entries (mangrove_mask.tif, biomass_summary.csv, carbon_summary.csv, analysis.json).

## Examples

### Mangrove Analysis Output Folder
#### json
```json
{
  "@id": "urn:uuid:f1477d81-2d56-4874-9d5b-eb5de2a571af",
  "@type": "Folder",
  "basename": "mangrove-analysis-20251103-151416",
  "isDescribedBy": "metadata/directory-f1477d81-2d56-4874-9d5b-eb5de2a571af.ttl",
  "aggregates": [
    {
      "@id": "urn:uuid:3aade478-9f4e-4feb-8cdb-26d31d3467e7",
      "@type": ["FolderEntry"],
      "entryName": "mangrove_mask.tif",
      "proxyFor": {
        "@id": "urn:uuid:04c0ef72-14c0-4248-b042-6dec318c56c5",
        "@type": "File",
        "basename": "mangrove_mask.tif"
      }
    },
    {
      "@id": "urn:uuid:8de4c1ce-3576-4f00-aa02-7c7fe7e92370",
      "@type": ["FolderEntry"],
      "entryName": "mangrove-analysis-20251103-151416.json",
      "proxyFor": {
        "@id": "urn:uuid:b5c14d0c-6065-4171-96c8-dadbcde3822a",
        "@type": "File",
        "basename": "mangrove-analysis-20251103-151416.json"
      }
    },
    {
      "@id": "urn:uuid:9b2f4291-1391-4dc1-b587-193d86d95afc",
      "@type": ["FolderEntry"],
      "entryName": "carbon_summary.csv",
      "proxyFor": {
        "@id": "urn:uuid:f59664cc-4bda-4c8f-a5b1-b02d8bfcf369",
        "@type": "File",
        "basename": "carbon_summary.csv"
      }
    },
    {
      "@id": "urn:uuid:a7bbd47e-94ae-4baa-b2ff-ddd2667ac7f0",
      "@type": ["FolderEntry"],
      "entryName": "biomass_summary.csv",
      "proxyFor": {
        "@id": "urn:uuid:6dd8ef39-c040-4038-b2ee-0696ee7c712f",
        "@type": "File",
        "basename": "biomass_summary.csv"
      }
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Folder/context.jsonld",
  "@id": "urn:uuid:f1477d81-2d56-4874-9d5b-eb5de2a571af",
  "@type": "Folder",
  "basename": "mangrove-analysis-20251103-151416",
  "isDescribedBy": "metadata/directory-f1477d81-2d56-4874-9d5b-eb5de2a571af.ttl",
  "aggregates": [
    {
      "@id": "urn:uuid:3aade478-9f4e-4feb-8cdb-26d31d3467e7",
      "@type": [
        "FolderEntry"
      ],
      "entryName": "mangrove_mask.tif",
      "proxyFor": {
        "@id": "urn:uuid:04c0ef72-14c0-4248-b042-6dec318c56c5",
        "@type": "File",
        "basename": "mangrove_mask.tif"
      }
    },
    {
      "@id": "urn:uuid:8de4c1ce-3576-4f00-aa02-7c7fe7e92370",
      "@type": [
        "FolderEntry"
      ],
      "entryName": "mangrove-analysis-20251103-151416.json",
      "proxyFor": {
        "@id": "urn:uuid:b5c14d0c-6065-4171-96c8-dadbcde3822a",
        "@type": "File",
        "basename": "mangrove-analysis-20251103-151416.json"
      }
    },
    {
      "@id": "urn:uuid:9b2f4291-1391-4dc1-b587-193d86d95afc",
      "@type": [
        "FolderEntry"
      ],
      "entryName": "carbon_summary.csv",
      "proxyFor": {
        "@id": "urn:uuid:f59664cc-4bda-4c8f-a5b1-b02d8bfcf369",
        "@type": "File",
        "basename": "carbon_summary.csv"
      }
    },
    {
      "@id": "urn:uuid:a7bbd47e-94ae-4baa-b2ff-ddd2667ac7f0",
      "@type": [
        "FolderEntry"
      ],
      "entryName": "biomass_summary.csv",
      "proxyFor": {
        "@id": "urn:uuid:6dd8ef39-c040-4038-b2ee-0696ee7c712f",
        "@type": "File",
        "basename": "biomass_summary.csv"
      }
    }
  ]
}
```

#### ttl
```ttl
@prefix ro: <http://purl.org/wf4ever/ro#> .

<urn:uuid:f1477d81-2d56-4874-9d5b-eb5de2a571af> a ro:Folder ;
    ro:aggregates <urn:uuid:3aade478-9f4e-4feb-8cdb-26d31d3467e7>,
        <urn:uuid:8de4c1ce-3576-4f00-aa02-7c7fe7e92370>,
        <urn:uuid:9b2f4291-1391-4dc1-b587-193d86d95afc>,
        <urn:uuid:a7bbd47e-94ae-4baa-b2ff-ddd2667ac7f0> ;
    ro:basename "mangrove-analysis-20251103-151416" ;
    ro:isDescribedBy "metadata/directory-f1477d81-2d56-4874-9d5b-eb5de2a571af.ttl" .

<urn:uuid:04c0ef72-14c0-4248-b042-6dec318c56c5> a ro:File ;
    ro:basename "mangrove_mask.tif" .

<urn:uuid:3aade478-9f4e-4feb-8cdb-26d31d3467e7> a ro:FolderEntry ;
    ro:entryName "mangrove_mask.tif" ;
    ro:proxyFor <urn:uuid:04c0ef72-14c0-4248-b042-6dec318c56c5> .

<urn:uuid:6dd8ef39-c040-4038-b2ee-0696ee7c712f> a ro:File ;
    ro:basename "biomass_summary.csv" .

<urn:uuid:8de4c1ce-3576-4f00-aa02-7c7fe7e92370> a ro:FolderEntry ;
    ro:entryName "mangrove-analysis-20251103-151416.json" ;
    ro:proxyFor <urn:uuid:b5c14d0c-6065-4171-96c8-dadbcde3822a> .

<urn:uuid:9b2f4291-1391-4dc1-b587-193d86d95afc> a ro:FolderEntry ;
    ro:entryName "carbon_summary.csv" ;
    ro:proxyFor <urn:uuid:f59664cc-4bda-4c8f-a5b1-b02d8bfcf369> .

<urn:uuid:a7bbd47e-94ae-4baa-b2ff-ddd2667ac7f0> a ro:FolderEntry ;
    ro:entryName "biomass_summary.csv" ;
    ro:proxyFor <urn:uuid:6dd8ef39-c040-4038-b2ee-0696ee7c712f> .

<urn:uuid:b5c14d0c-6065-4171-96c8-dadbcde3822a> a ro:File ;
    ro:basename "mangrove-analysis-20251103-151416.json" .

<urn:uuid:f59664cc-4bda-4c8f-a5b1-b02d8bfcf369> a ro:File ;
    ro:basename "carbon_summary.csv" .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A folder organizing resources in a Research Object
type: object
properties:
  '@id':
    type: string
    format: uri
    description: Unique identifier for the folder
  '@type':
    const: Folder
    description: Type must be Folder
  name:
    type: string
    description: Name of the folder
    x-jsonld-id: http://purl.org/dc/terms/title
  description:
    type: string
    description: Description of the folder
    x-jsonld-id: http://purl.org/dc/terms/description
  hasEntry:
    type: array
    items:
      type: object
      properties:
        '@id':
          type: string
          format: uri
      required:
      - '@id'
    description: Entries contained in this folder
    x-jsonld-id: http://purl.org/wf4ever/ro#hasEntry
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
required:
- '@id'
- '@type'
x-jsonld-extra-terms:
  Folder: http://purl.org/wf4ever/ro#Folder
x-jsonld-vocab: http://purl.org/wf4ever/ro#
x-jsonld-prefixes:
  ro: http://purl.org/wf4ever/ro#
  dcterms: http://purl.org/dc/terms/

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Folder/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Folder/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/ro#",
    "Folder": "ro:Folder",
    "name": "dcterms:title",
    "description": "dcterms:description",
    "hasEntry": {
      "@id": "ro:hasEntry",
      "@type": "@id",
      "@container": "@set"
    },
    "ro": "http://purl.org/wf4ever/ro#",
    "dcterms": "http://purl.org/dc/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Folder/context.jsonld)

## Sources

* [Research Object Ontology - Folder](http://purl.org/wf4ever/ro#Folder)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/ro/Folder`

