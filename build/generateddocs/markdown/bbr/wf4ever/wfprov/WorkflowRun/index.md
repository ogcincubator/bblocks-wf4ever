
# wfprov:WorkflowRun (Datatype)

`ogc.bbr.wf4ever.wfprov.WorkflowRun` *v1.0*

An execution instance of a workflow. A WorkflowRun is a special type of ProcessRun that represents the execution of a complete workflow (wfdesc:Workflow), containing multiple ProcessRuns for its sub-processes.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfprov:WorkflowRun

## Description

A **WorkflowRun** represents an execution instance of a complete workflow. It is a specialized type of ProcessRun that represents the execution of a `wfdesc:Workflow`, containing multiple ProcessRuns for its sub-processes.

## Class Hierarchy

Inherits all properties from `wfprov:ProcessRun`.

## Relations

- Extends `wfprov:ProcessRun`
- Must be linked to a `wfdesc:Workflow` via `describedByWorkflow`
- Contains `wfprov:ProcessRun` via `hadSubProcessRun`
- Can be executed by a `wfprov:WorkflowEngine` via `wasEnactedBy`

## Example

See the real-world example from a CWLProv execution showing complete workflow provenance with temporal information (startedAtTime, endedAtTime), associated agents (cwltool), and artifacts used/generated during execution.

## Examples

### Mangrove Workflow Run with Provenance
#### json
```json
{
  "id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "type": "WorkflowRun",
  "label": "Run of workflow/packed.cwl#main",
  "describedByWorkflow": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main",
  "startedAtTime": "2025-11-03T15:14:02.032122",
  "endedAtTime": "2025-11-03T15:14:17.060218",
  "wasAssociatedWith": [
    {
      "id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "type": "WorkflowEngine",
      "label": "cwltool 3.1.20251031082601"
    },
    {
      "id": "urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f",
      "type": "Agent",
      "label": "Container execution of image r2d-2ftmp-2frepo2cwl-5fzbz5cbsp-2frepo1762182696"
    }
  ],
  "used": [
    {
      "id": "urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d",
      "value": 20.0,
      "hadRole": "cloud_cover_max"
    },
    {
      "id": "urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258",
      "value": 90,
      "hadRole": "days_back"
    },
    {
      "id": "urn:uuid:ced76ef7-e660-4798-9442-06c17a45bbea",
      "value": 95.35,
      "hadRole": "east"
    },
    {
      "id": "urn:uuid:fd57ac88-8716-40ed-8945-f83914857523",
      "value": 16.1,
      "hadRole": "north"
    }
  ],
  "generated": [
    {
      "id": "urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539",
      "type": "Artifact",
      "basename": "outputs"
    }
  ]
}


```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/context.jsonld",
  "id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "type": "WorkflowRun",
  "label": "Run of workflow/packed.cwl#main",
  "describedByWorkflow": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main",
  "startedAtTime": "2025-11-03T15:14:02.032122",
  "endedAtTime": "2025-11-03T15:14:17.060218",
  "wasAssociatedWith": [
    {
      "id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "type": "WorkflowEngine",
      "label": "cwltool 3.1.20251031082601"
    },
    {
      "id": "urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f",
      "type": "Agent",
      "label": "Container execution of image r2d-2ftmp-2frepo2cwl-5fzbz5cbsp-2frepo1762182696"
    }
  ],
  "used": [
    {
      "id": "urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d",
      "value": 20.0,
      "hadRole": "cloud_cover_max"
    },
    {
      "id": "urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258",
      "value": 90,
      "hadRole": "days_back"
    },
    {
      "id": "urn:uuid:ced76ef7-e660-4798-9442-06c17a45bbea",
      "value": 95.35,
      "hadRole": "east"
    },
    {
      "id": "urn:uuid:fd57ac88-8716-40ed-8945-f83914857523",
      "value": 16.1,
      "hadRole": "north"
    }
  ],
  "generated": [
    {
      "id": "urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539",
      "type": "Artifact",
      "basename": "outputs"
    }
  ]
}
```

#### ttl
```ttl
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c> a wfprov:WorkflowRun ;
    wfprov:describedByWorkflow <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main> ;
    wfprov:generated <urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539> ;
    wfprov:label "Run of workflow/packed.cwl#main" ;
    wfprov:used <urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d>,
        <urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258>,
        <urn:uuid:ced76ef7-e660-4798-9442-06c17a45bbea>,
        <urn:uuid:fd57ac88-8716-40ed-8945-f83914857523> ;
    wfprov:wasAssociatedWith <urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f>,
        <urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> ;
    prov:endedAtTime "2025-11-03T15:14:17.060218"^^xsd:dateTime ;
    prov:startedAtTime "2025-11-03T15:14:02.032122"^^xsd:dateTime .

<urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d> wfprov:hadRole "cloud_cover_max" ;
    wfprov:value 2e+01 .

<urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f> a wfprov:Agent ;
    wfprov:label "Container execution of image r2d-2ftmp-2frepo2cwl-5fzbz5cbsp-2frepo1762182696" .

<urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> a wfprov:WorkflowEngine ;
    wfprov:label "cwltool 3.1.20251031082601" .

<urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539> a wfprov:Artifact ;
    wfprov:basename "outputs" .

<urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258> wfprov:hadRole "days_back" ;
    wfprov:value 90 .

<urn:uuid:ced76ef7-e660-4798-9442-06c17a45bbea> wfprov:hadRole "east" ;
    wfprov:value 9.535e+01 .

<urn:uuid:fd57ac88-8716-40ed-8945-f83914857523> wfprov:hadRole "north" ;
    wfprov:value 1.61e+01 .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An execution instance of a workflow
allOf:
- $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/ProcessRun/schema.yaml
- type: object
  properties:
    describedByWorkflow:
      type: string
      format: uri
      description: Links to the workflow description (wfdesc:Workflow) that was executed
      x-jsonld-id: http://purl.org/wf4ever/wfprov#describedByWorkflow
      x-jsonld-type: '@id'
    hadSubProcessRun:
      type: array
      items:
        type: object
        properties:
          id:
            type: string
            format: uri
        required:
        - id
      description: The process runs that were part of this workflow execution
      x-jsonld-reverse: wfprov:wasPartOfWorkflowRun
      x-jsonld-type: '@id'
      x-jsonld-container: '@set'
    wasEnactedBy:
      type: string
      format: uri
      description: The workflow engine that executed this workflow
      x-jsonld-id: http://www.w3.org/ns/prov#wasAssociatedWith
      x-jsonld-type: '@id'
  required:
  - describedByWorkflow
x-jsonld-extra-terms:
  WorkflowRun: http://purl.org/wf4ever/wfprov#WorkflowRun
x-jsonld-vocab: http://purl.org/wf4ever/wfprov#
x-jsonld-prefixes:
  wfprov: http://purl.org/wf4ever/wfprov#
  prov: http://www.w3.org/ns/prov#
  wfdesc: http://purl.org/wf4ever/wfdesc#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/wfprov#",
    "ProcessRun": "wfprov:ProcessRun",
    "WorkflowRun": "wfprov:WorkflowRun",
    "wasOutputFrom": {
      "@id": "prov:generated",
      "@type": "@id",
      "@container": "@set"
    },
    "id": "@id",
    "type": "@type",
    "describedByProcess": {
      "@id": "wfprov:describedByProcess",
      "@type": "@id"
    },
    "usedInput": {
      "@id": "wfprov:usedInput",
      "@type": "@id",
      "@container": "@set"
    },
    "startedAtTime": {
      "@id": "prov:startedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "endedAtTime": {
      "@id": "prov:endedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "wasPartOfWorkflowRun": {
      "@id": "wfprov:wasPartOfWorkflowRun",
      "@type": "@id"
    },
    "wasEnactedBy": {
      "@id": "prov:wasAssociatedWith",
      "@type": "@id"
    },
    "describedByWorkflow": {
      "@id": "wfprov:describedByWorkflow",
      "@type": "@id"
    },
    "hadSubProcessRun": {
      "@reverse": "wfprov:wasPartOfWorkflowRun",
      "@type": "@id",
      "@container": "@set"
    },
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "prov": "http://www.w3.org/ns/prov#",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/context.jsonld)

## Sources

* [Workflow Provenance Ontology - WorkflowRun](http://purl.org/wf4ever/wfprov#WorkflowRun)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfprov/WorkflowRun`

