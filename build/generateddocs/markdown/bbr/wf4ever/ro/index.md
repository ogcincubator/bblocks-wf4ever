
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

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/schema.yaml)


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
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/context.jsonld)

## Sources

* [Research Object Ontology](http://purl.org/wf4ever/ro)
* [OAI-ORE](http://www.openarchives.org/ore/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/ro`

