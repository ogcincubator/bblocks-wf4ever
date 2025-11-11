
# wfprov:ProcessRun (Datatype)

`ogc.bbr.wf4ever.wfprov.ProcessRun` *v1.0*

An execution instance of a process. A ProcessRun represents the actual execution of a process described by wfdesc:Process, tracking what happened during that execution including inputs used, outputs generated, and timing information.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfprov:ProcessRun

## Description

A **ProcessRun** represents an execution instance of a process. It captures what actually happened during the execution of a process described by `wfdesc:Process`, including the input artifacts used, output artifacts generated, and timing information.

## Relations

- Must be linked to a `wfdesc:Process` via `describedByProcess`
- Uses `wfprov:Artifact` via `usedInput`
- Output artifacts reference this ProcessRun via their `wasOutputFrom` property
- Can be part of a `wfprov:WorkflowRun` via `wasPartOfWorkflowRun`
- Can be enacted by a `wfprov:WorkflowEngine` via `wasEnactedBy`

## Examples

### Simple process run
#### json
```json
{
  "@id": "#reproject-run-1",
  "@type": "ProcessRun",
  "describedByProcess": "#reproject-process",
  "usedInput": [
    { "@id": "artifact/input_data.tif" }
  ],
  "startedAtTime": "2025-11-07T10:00:00Z",
  "endedAtTime": "2025-11-07T10:02:00Z",
  "wasPartOfWorkflowRun": "#workflow-run-1"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/ProcessRun/context.jsonld",
  "@id": "#reproject-run-1",
  "@type": "ProcessRun",
  "describedByProcess": "#reproject-process",
  "usedInput": [
    {
      "@id": "artifact/input_data.tif"
    }
  ],
  "startedAtTime": "2025-11-07T10:00:00Z",
  "endedAtTime": "2025-11-07T10:02:00Z",
  "wasPartOfWorkflowRun": "#workflow-run-1"
}
```

#### ttl
```ttl
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<file:///github/workspace/#reproject-run-1> a wfprov:ProcessRun ;
    wfprov:describedByProcess <file:///github/workspace/#reproject-process> ;
    wfprov:usedInput <file:///github/workspace/artifact/input_data.tif> ;
    wfprov:wasPartOfWorkflowRun <file:///github/workspace/#workflow-run-1> ;
    prov:endedAtTime "2025-11-07T10:02:00+00:00"^^xsd:dateTime ;
    prov:startedAtTime "2025-11-07T10:00:00+00:00"^^xsd:dateTime .


```


### Process run within workflow
#### json
```json
{
  "@id": "#ndvi-process-run-1",
  "@type": "ProcessRun",
  "describedByProcess": "#ndvi-process",
  "usedInput": [
    { "@id": "artifact/landsat_band4.tif" },
    { "@id": "artifact/landsat_band5.tif" }
  ],
  "startedAtTime": "2025-11-07T10:00:00Z",
  "endedAtTime": "2025-11-07T10:05:00Z",
  "wasPartOfWorkflowRun": "#ndvi-workflow-run-1",
  "wasEnactedBy": "#zoo-wps-engine"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/ProcessRun/context.jsonld",
  "@id": "#ndvi-process-run-1",
  "@type": "ProcessRun",
  "describedByProcess": "#ndvi-process",
  "usedInput": [
    {
      "@id": "artifact/landsat_band4.tif"
    },
    {
      "@id": "artifact/landsat_band5.tif"
    }
  ],
  "startedAtTime": "2025-11-07T10:00:00Z",
  "endedAtTime": "2025-11-07T10:05:00Z",
  "wasPartOfWorkflowRun": "#ndvi-workflow-run-1",
  "wasEnactedBy": "#zoo-wps-engine"
}
```

#### ttl
```ttl
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<file:///github/workspace/#ndvi-process-run-1> a wfprov:ProcessRun ;
    wfprov:describedByProcess <file:///github/workspace/#ndvi-process> ;
    wfprov:usedInput <file:///github/workspace/artifact/landsat_band4.tif>,
        <file:///github/workspace/artifact/landsat_band5.tif> ;
    wfprov:wasPartOfWorkflowRun <file:///github/workspace/#ndvi-workflow-run-1> ;
    prov:endedAtTime "2025-11-07T10:05:00+00:00"^^xsd:dateTime ;
    prov:startedAtTime "2025-11-07T10:00:00+00:00"^^xsd:dateTime ;
    prov:wasAssociatedWith <file:///github/workspace/#zoo-wps-engine> .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An execution instance of a process (based on prov:Activity)
type: object
properties:
  id:
    type: string
    format: uri
    description: Unique identifier for the process run
    x-jsonld-id: '@id'
  type:
    type: string
    description: Type indicator (Activity or sub-type)
    x-jsonld-id: '@type'
  describedByProcess:
    type: string
    format: uri
    description: Links to the process description (wfdesc:Process) that was executed
    x-jsonld-id: http://purl.org/wf4ever/wfprov#describedByProcess
    x-jsonld-type: '@id'
  usedInput:
    type: array
    items:
      type: object
      properties:
        id:
          type: string
          format: uri
      required:
      - id
    description: Input artifacts used by this process run
    x-jsonld-id: http://purl.org/wf4ever/wfprov#usedInput
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
  startedAtTime:
    type: string
    format: date-time
    description: Start time of the execution
    x-jsonld-id: http://www.w3.org/ns/prov#startedAtTime
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
  endedAtTime:
    type: string
    format: date-time
    description: End time of the execution
    x-jsonld-id: http://www.w3.org/ns/prov#endedAtTime
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
  wasPartOfWorkflowRun:
    type: string
    format: uri
    description: The workflow run that this process run was part of
    x-jsonld-id: http://purl.org/wf4ever/wfprov#wasPartOfWorkflowRun
    x-jsonld-type: '@id'
  wasEnactedBy:
    type: string
    format: uri
    description: The workflow engine that enacted this process run
    x-jsonld-id: http://www.w3.org/ns/prov#wasAssociatedWith
    x-jsonld-type: '@id'
required:
- id
x-jsonld-extra-terms:
  ProcessRun: http://purl.org/wf4ever/wfprov#ProcessRun
  WorkflowRun: http://purl.org/wf4ever/wfprov#WorkflowRun
  wasOutputFrom:
    x-jsonld-id: http://www.w3.org/ns/prov#generated
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
x-jsonld-vocab: http://purl.org/wf4ever/wfprov#
x-jsonld-prefixes:
  wfprov: http://purl.org/wf4ever/wfprov#
  prov: http://www.w3.org/ns/prov#
  wfdesc: http://purl.org/wf4ever/wfdesc#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/ProcessRun/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/ProcessRun/schema.yaml)


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
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "prov": "http://www.w3.org/ns/prov#",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/ProcessRun/context.jsonld)

## Sources

* [Workflow Provenance Ontology - ProcessRun](http://purl.org/wf4ever/wfprov#ProcessRun)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfprov/ProcessRun`

