
# Workflow Provenance Ontology (wfprov) (Schema)

`ogc.bbr.wf4ever.wfprov` *v1.0*

The Workflow Provenance ontology (wfprov) extends PROV-O to describe workflow execution traces, linking workflow runs to their descriptions.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# Workflow Provenance Ontology (wfprov)

## Overview

The Workflow Provenance ontology (wfprov) extends PROV-O to describe workflow execution traces. It links workflow runs to their descriptions and tracks the provenance of workflow executions.

## Namespace

`http://purl.org/wf4ever/wfprov#`

## Key Classes

- **WorkflowRun** - An execution of a workflow
- **ProcessRun** - An execution of a process
- **WorkflowEngine** - Software that executes workflows
- **Artifact** - Data entity used or generated

## Key Properties

- `wasPartOfWorkflowRun` - Links process run to workflow run
- `usedInput` - Input artifacts used
- `wasOutputFrom` - Output artifacts generated
- `describedByWorkflow` - Links run to workflow description
- `describedByProcess` - Links process run to process description
- `wasEnactedBy` - Links run to workflow engine

## Usage

This ontology is used to describe the retrospective provenance of workflows - what actually happened during execution, linking it to the workflow description (wfdesc).

## Examples

### Workflow Run from CWL Execution
#### json
```json
{
  "@id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "@type": "WorkflowRun",
  "name": "Run of workflow/packed.cwl#main",
  "describedByWorkflow": {
    "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main",
    "@type": ["wfdesc:Workflow", "wfdesc:Process"]
  },
  "wasAssociatedWith": [
    {
      "@id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "@type": "WorkflowEngine",
      "name": "cwltool 3.1.20251031082601"
    }
  ],
  "usedInput": [
    {
      "@type": "Artifact",
      "@id": "urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d",
      "value": 20.0
    },
    {
      "@type": "Artifact",
      "@id": "urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258",
      "value": 90
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/context.jsonld",
  "@id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "@type": "WorkflowRun",
  "name": "Run of workflow/packed.cwl#main",
  "describedByWorkflow": {
    "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main",
    "@type": [
      "wfdesc:Workflow",
      "wfdesc:Process"
    ]
  },
  "wasAssociatedWith": [
    {
      "@id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "@type": "WorkflowEngine",
      "name": "cwltool 3.1.20251031082601"
    }
  ],
  "usedInput": [
    {
      "@type": "Artifact",
      "@id": "urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d",
      "value": 20.0
    },
    {
      "@type": "Artifact",
      "@id": "urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258",
      "value": 90
    }
  ]
}
```

#### ttl
```ttl
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c> a wfprov:WorkflowRun ;
    rdfs:label "Run of workflow/packed.cwl#main" ;
    wfprov:describedByWorkflow <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main> ;
    wfprov:usedInput <urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d>,
        <urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258> ;
    prov:wasAssociatedWith <urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main> a wfdesc:Process,
        wfdesc:Workflow .

<urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d> a wfprov:Artifact ;
    prov:value 2e+01 .

<urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> a wfprov:WorkflowEngine ;
    rdfs:label "cwltool 3.1.20251031082601" .

<urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258> a wfprov:Artifact ;
    prov:value 90 .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: Workflow Provenance schema based on wfprov ontology
type: object
properties:
  '@type':
    oneOf:
    - type: string
      enum:
      - WorkflowRun
      - ProcessRun
      - WorkflowEngine
      - Artifact
    - type: array
      items:
        type: string
  name:
    type: string
    description: Name of the run or artifact
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  describedByWorkflow:
    type: object
    description: Links workflow run to its description
    x-jsonld-id: http://purl.org/wf4ever/wfprov#describedByWorkflow
    x-jsonld-type: '@id'
  describedByProcess:
    type: object
    description: Links process run to its description
    x-jsonld-id: http://purl.org/wf4ever/wfprov#describedByProcess
    x-jsonld-type: '@id'
  wasPartOfWorkflowRun:
    type: object
    description: Links process run to workflow run
    x-jsonld-id: http://purl.org/wf4ever/wfprov#wasPartOfWorkflowRun
    x-jsonld-type: '@id'
  usedInput:
    type: array
    items:
      type: object
    description: Input artifacts used
    x-jsonld-id: http://purl.org/wf4ever/wfprov#usedInput
    x-jsonld-type: '@id'
  wasOutputFrom:
    type: array
    items:
      type: object
    description: Output artifacts generated
    x-jsonld-id: http://purl.org/wf4ever/wfprov#wasOutputFrom
    x-jsonld-type: '@id'
  wasAssociatedWith:
    type: array
    items:
      type: object
    description: Agents associated with execution
    x-jsonld-id: http://www.w3.org/ns/prov#wasAssociatedWith
    x-jsonld-type: '@id'
  wasEnactedBy:
    type: object
    description: Workflow engine that executed the run
    x-jsonld-id: http://purl.org/wf4ever/wfprov#wasEnactedBy
    x-jsonld-type: '@id'
  value:
    description: Value of an artifact or parameter
    x-jsonld-id: http://www.w3.org/ns/prov#value
x-jsonld-extra-terms:
  WorkflowRun: http://purl.org/wf4ever/wfprov#WorkflowRun
  ProcessRun: http://purl.org/wf4ever/wfprov#ProcessRun
  WorkflowEngine: http://purl.org/wf4ever/wfprov#WorkflowEngine
  Artifact: http://purl.org/wf4ever/wfprov#Artifact
x-jsonld-prefixes:
  wfprov: http://purl.org/wf4ever/wfprov#
  rdfs: http://www.w3.org/2000/01/rdf-schema#
  prov: http://www.w3.org/ns/prov#
  wfdesc: http://purl.org/wf4ever/wfdesc#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "WorkflowRun": "wfprov:WorkflowRun",
    "ProcessRun": "wfprov:ProcessRun",
    "WorkflowEngine": "wfprov:WorkflowEngine",
    "Artifact": "wfprov:Artifact",
    "name": "rdfs:label",
    "describedByWorkflow": {
      "@id": "wfprov:describedByWorkflow",
      "@type": "@id"
    },
    "describedByProcess": {
      "@id": "wfprov:describedByProcess",
      "@type": "@id"
    },
    "wasPartOfWorkflowRun": {
      "@id": "wfprov:wasPartOfWorkflowRun",
      "@type": "@id"
    },
    "usedInput": {
      "@id": "wfprov:usedInput",
      "@type": "@id"
    },
    "wasOutputFrom": {
      "@id": "wfprov:wasOutputFrom",
      "@type": "@id"
    },
    "wasAssociatedWith": {
      "@id": "prov:wasAssociatedWith",
      "@type": "@id"
    },
    "wasEnactedBy": {
      "@id": "wfprov:wasEnactedBy",
      "@type": "@id"
    },
    "value": "prov:value",
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "prov": "http://www.w3.org/ns/prov#",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/context.jsonld)

## Sources

* [Workflow Provenance Ontology](http://purl.org/wf4ever/wfprov)
* [PROV-O](https://www.w3.org/TR/prov-o/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfprov`

