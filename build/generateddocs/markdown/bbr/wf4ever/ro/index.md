
# Research Object Ontology (ro) (Schema)

`ogc.bbr.wf4ever.ro` *v1.0*

The Research Object ontology (ro) provides concepts for bundling and aggregating research artifacts, describing folder structures and annotations.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# Research Object Ontology (ro)

## Overview

The Research Object ontology (ro) provides concepts for bundling and aggregating research artifacts. It enables the packaging of workflows, data, and metadata into a single research object.

## Namespace

`http://purl.org/wf4ever/ro#`

## Key Classes

- **ResearchObject** - A bundled collection of resources
- **Resource** - Any research artifact
- **Folder** - Directory structure
- **FolderEntry** - Entry in a folder
- **AggregatedAnnotation** - Annotation about resources
- **Manifest** - Manifest describing the research object

## Key Properties

- `aggregates` - Resources in the research object
- `rootFolder` - Main folder
- `entryName` - Name of a folder entry
- `annotatesAggregatedResource` - Annotation target
- `manifest` - Manifest of the research object

## Usage

This ontology is used to package workflow descriptions, execution provenance, and data into cohesive research objects that can be shared and preserved.

## Examples

### Research Object Folder from CWL Execution
#### json
```json
{
  "@id": "urn:uuid:f1477d81-2d56-4874-9d5b-eb5de2a571af",
  "@type": ["Folder", "wfprov:Artifact"],
  "name": "mangrove-analysis-20251103-151416",
  "aggregates": [
    {
      "@type": "FolderEntry",
      "entryName": "mangrove_mask.tif",
      "@id": "urn:uuid:3aade478-9f4e-4feb-8cdb-26d31d3467e7"
    },
    {
      "@type": "FolderEntry",
      "entryName": "biomass_summary.csv",
      "@id": "urn:uuid:a7bbd47e-94ae-4baa-b2ff-ddd2667ac7f0"
    },
    {
      "@type": "FolderEntry",
      "entryName": "carbon_summary.csv",
      "@id": "urn:uuid:9b2f4291-1391-4dc1-b587-193d86d95afc"
    },
    {
      "@type": "FolderEntry",
      "entryName": "mangrove-analysis-20251103-151416.json",
      "@id": "urn:uuid:8de4c1ce-3576-4f00-aa02-7c7fe7e92370"
    }
  ],
  "isDescribedBy": {
    "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/directory-f1477d81-2d56-4874-9d5b-eb5de2a571af.ttl"
  }
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/context.jsonld",
  "@id": "urn:uuid:f1477d81-2d56-4874-9d5b-eb5de2a571af",
  "@type": [
    "Folder",
    "wfprov:Artifact"
  ],
  "name": "mangrove-analysis-20251103-151416",
  "aggregates": [
    {
      "@type": "FolderEntry",
      "entryName": "mangrove_mask.tif",
      "@id": "urn:uuid:3aade478-9f4e-4feb-8cdb-26d31d3467e7"
    },
    {
      "@type": "FolderEntry",
      "entryName": "biomass_summary.csv",
      "@id": "urn:uuid:a7bbd47e-94ae-4baa-b2ff-ddd2667ac7f0"
    },
    {
      "@type": "FolderEntry",
      "entryName": "carbon_summary.csv",
      "@id": "urn:uuid:9b2f4291-1391-4dc1-b587-193d86d95afc"
    },
    {
      "@type": "FolderEntry",
      "entryName": "mangrove-analysis-20251103-151416.json",
      "@id": "urn:uuid:8de4c1ce-3576-4f00-aa02-7c7fe7e92370"
    }
  ],
  "isDescribedBy": {
    "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/directory-f1477d81-2d56-4874-9d5b-eb5de2a571af.ttl"
  }
}
```

#### ttl
```ttl
@prefix ore: <http://www.openarchives.org/ore/terms/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix ro: <http://purl.org/wf4ever/ro#> .

<urn:uuid:f1477d81-2d56-4874-9d5b-eb5de2a571af> a ro:Folder,
        <wfprov:Artifact> ;
    rdfs:label "mangrove-analysis-20251103-151416" ;
    ore:aggregates <urn:uuid:3aade478-9f4e-4feb-8cdb-26d31d3467e7>,
        <urn:uuid:8de4c1ce-3576-4f00-aa02-7c7fe7e92370>,
        <urn:uuid:9b2f4291-1391-4dc1-b587-193d86d95afc>,
        <urn:uuid:a7bbd47e-94ae-4baa-b2ff-ddd2667ac7f0> ;
    ore:isDescribedBy <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/directory-f1477d81-2d56-4874-9d5b-eb5de2a571af.ttl> .

<urn:uuid:3aade478-9f4e-4feb-8cdb-26d31d3467e7> a ro:FolderEntry ;
    ro:entryName "mangrove_mask.tif" .

<urn:uuid:8de4c1ce-3576-4f00-aa02-7c7fe7e92370> a ro:FolderEntry ;
    ro:entryName "mangrove-analysis-20251103-151416.json" .

<urn:uuid:9b2f4291-1391-4dc1-b587-193d86d95afc> a ro:FolderEntry ;
    ro:entryName "carbon_summary.csv" .

<urn:uuid:a7bbd47e-94ae-4baa-b2ff-ddd2667ac7f0> a ro:FolderEntry ;
    ro:entryName "biomass_summary.csv" .


```


### Complete Research Object Output
#### json
```json
{
  "@id": "urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539",
  "@type": ["Folder", "wfprov:Artifact"],
  "name": "outputs",
  "aggregates": [
    {
      "@type": "FolderEntry",
      "entryName": "catalog.json",
      "@id": "urn:uuid:cef10a06-9879-4354-8543-833951388c61"
    },
    {
      "@type": "FolderEntry",
      "entryName": "mangrove-analysis-20251103-151416",
      "@id": "urn:uuid:f03ce803-f175-437f-bc7a-3888a62c1d4e"
    }
  ],
  "isDescribedBy": {
    "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/directory-83c8708e-ccbd-494e-b939-1298b65b1539.ttl"
  }
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/context.jsonld",
  "@id": "urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539",
  "@type": [
    "Folder",
    "wfprov:Artifact"
  ],
  "name": "outputs",
  "aggregates": [
    {
      "@type": "FolderEntry",
      "entryName": "catalog.json",
      "@id": "urn:uuid:cef10a06-9879-4354-8543-833951388c61"
    },
    {
      "@type": "FolderEntry",
      "entryName": "mangrove-analysis-20251103-151416",
      "@id": "urn:uuid:f03ce803-f175-437f-bc7a-3888a62c1d4e"
    }
  ],
  "isDescribedBy": {
    "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/directory-83c8708e-ccbd-494e-b939-1298b65b1539.ttl"
  }
}
```

#### ttl
```ttl
@prefix ore: <http://www.openarchives.org/ore/terms/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix ro: <http://purl.org/wf4ever/ro#> .

<urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539> a ro:Folder,
        <wfprov:Artifact> ;
    rdfs:label "outputs" ;
    ore:aggregates <urn:uuid:cef10a06-9879-4354-8543-833951388c61>,
        <urn:uuid:f03ce803-f175-437f-bc7a-3888a62c1d4e> ;
    ore:isDescribedBy <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/directory-83c8708e-ccbd-494e-b939-1298b65b1539.ttl> .

<urn:uuid:cef10a06-9879-4354-8543-833951388c61> a ro:FolderEntry ;
    ro:entryName "catalog.json" .

<urn:uuid:f03ce803-f175-437f-bc7a-3888a62c1d4e> a ro:FolderEntry ;
    ro:entryName "mangrove-analysis-20251103-151416" .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: Research Object schema based on ro ontology
type: object
properties:
  '@type':
    oneOf:
    - type: string
      enum:
      - ResearchObject
      - Resource
      - Folder
      - FolderEntry
      - AggregatedAnnotation
      - Manifest
    - type: array
      items:
        type: string
  name:
    type: string
    description: Name of the resource
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  aggregates:
    type: array
    items:
      type: object
    description: Resources aggregated
    x-jsonld-id: http://www.openarchives.org/ore/terms/aggregates
    x-jsonld-type: '@id'
  rootFolder:
    type: object
    description: Root folder
    x-jsonld-id: http://purl.org/wf4ever/ro#rootFolder
    x-jsonld-type: '@id'
  entryName:
    type: string
    description: Name of folder entry
    x-jsonld-id: http://purl.org/wf4ever/ro#entryName
  annotatesAggregatedResource:
    type: object
    description: Resource being annotated
    x-jsonld-id: http://purl.org/wf4ever/ro#annotatesAggregatedResource
    x-jsonld-type: '@id'
  manifest:
    type: object
    description: Manifest
    x-jsonld-id: http://purl.org/wf4ever/ro#manifest
    x-jsonld-type: '@id'
  isDescribedBy:
    type: object
    description: Description of resource
    x-jsonld-id: http://www.openarchives.org/ore/terms/isDescribedBy
    x-jsonld-type: '@id'
x-jsonld-extra-terms:
  ResearchObject: http://purl.org/wf4ever/ro#ResearchObject
  Resource: http://purl.org/wf4ever/ro#Resource
  Folder: http://purl.org/wf4ever/ro#Folder
  FolderEntry: http://purl.org/wf4ever/ro#FolderEntry
  AggregatedAnnotation: http://purl.org/wf4ever/ro#AggregatedAnnotation
  Manifest: http://purl.org/wf4ever/ro#Manifest
x-jsonld-prefixes:
  ro: http://purl.org/wf4ever/ro#
  rdfs: http://www.w3.org/2000/01/rdf-schema#
  ore: http://www.openarchives.org/ore/terms/

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "ResearchObject": "ro:ResearchObject",
    "Resource": "ro:Resource",
    "Folder": "ro:Folder",
    "FolderEntry": "ro:FolderEntry",
    "AggregatedAnnotation": "ro:AggregatedAnnotation",
    "Manifest": "ro:Manifest",
    "name": "rdfs:label",
    "aggregates": {
      "@id": "ore:aggregates",
      "@type": "@id"
    },
    "rootFolder": {
      "@id": "ro:rootFolder",
      "@type": "@id"
    },
    "entryName": "ro:entryName",
    "annotatesAggregatedResource": {
      "@id": "ro:annotatesAggregatedResource",
      "@type": "@id"
    },
    "manifest": {
      "@id": "ro:manifest",
      "@type": "@id"
    },
    "isDescribedBy": {
      "@id": "ore:isDescribedBy",
      "@type": "@id"
    },
    "ro": "http://purl.org/wf4ever/ro#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "ore": "http://www.openarchives.org/ore/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/context.jsonld)

## Sources

* [Research Object Ontology](http://purl.org/wf4ever/ro)
* [OAI-ORE](http://www.openarchives.org/ore/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/ro`

