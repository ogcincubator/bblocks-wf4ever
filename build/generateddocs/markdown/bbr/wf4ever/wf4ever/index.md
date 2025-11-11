
# Wf4Ever Extension Ontology (Schema)

`ogc.bbr.wf4ever.wf4ever` *v1.0*

The wf4ever ontology extends ro, wfdesc and wfprov with specialized artifact and process types commonly used in workflow research objects.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# Wf4Ever Extension Ontology

## Overview

The **wf4ever ontology** extends the base Wf4Ever ontologies (ro, wfdesc, wfprov) with specialized classes for common artifact and process types used in workflow research objects.

## Purpose

While the base ontologies provide generic concepts (wfdesc:Artifact, wfdesc:Process), the wf4ever ontology adds **semantic precision** by defining specialized types that are commonly encountered in scientific workflows:

- **Artifact specializations**: File, Dataset, Document, Image
- **Process specializations**: WebServiceProcess
- **Research Object specializations**: WorkflowResearchObject

## Imported Ontologies

The wf4ever ontology imports and extends:
- **ro** (Research Object): Research object structure and annotations
- **wfdesc** (Workflow Description): Workflow structure and composition
- **wfprov** (Workflow Provenance): Workflow execution provenance

## Classes Defined

### Artifact Types (subClassOf wfdesc:Artifact)

1. **wf4ever:File** - A file artifact (e.g., .json, .csv, .tif)
2. **wf4ever:Dataset** - A data collection or dataset
3. **wf4ever:Document** - A document artifact (e.g., PDF, HTML)
4. **wf4ever:Image** - An image file (e.g., PNG, JPEG, GeoTIFF)

### Process Types (subClassOf wfdesc:Process)

5. **wf4ever:WebServiceProcess** - A process executed as a web service call

### Research Object Types

6. **wf4ever:WorkflowResearchObject** - A research object containing at least one workflow

## Usage in CWL Provenance

In CWLProv (Common Workflow Language Provenance), wf4ever types are used to provide semantic precision through dual typing.

This dual typing allows:
- **Generic queries**: Find all `wfprov:Artifact` entities
- **Specific queries**: Find only `wf4ever:File` entities
- **Type-specific processing**: Handle files differently from generic artifacts

## Version

- **Version**: 0.1.1
- **Based on**: Wf4Ever Research Object ontologies v0.1.1

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: Wf4Ever ontology - extension vocabulary for workflow research objects
type: object
properties:
  '@context':
    type: object
required: []

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/schema.yaml)

## Sources

* [Wf4Ever Ontology](http://purl.org/wf4ever/wf4ever)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wf4ever`

