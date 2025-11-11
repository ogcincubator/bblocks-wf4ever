
# wfprov:WorkflowEngine (Datatype)

`ogc.bbr.wf4ever.wfprov.WorkflowEngine` *v1.0*

A software agent that executes workflows. The WorkflowEngine is responsible for enacting workflow and process executions, managing the execution environment and resources.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfprov:WorkflowEngine

## Description

A **WorkflowEngine** represents a software agent that executes workflows. The workflow engine is responsible for enacting workflow and process executions, managing the execution environment and resources.

## Relations

- Process runs and workflow runs reference the engine via `wfprov:wasEnactedBy`
- This is the inverse relationship: the engine enacts the executions

## Examples of engines

- ZOO-Project WPS
- Apache Airflow
- Nextflow
- Snakemake
- CWL Runner

## Examples

### ZOO-Project WPS Engine
#### json
```json
{
  "@id": "#zoo-wps-engine",
  "@type": "WorkflowEngine",
  "name": "ZOO-Project WPS",
  "version": "1.9.0",
  "description": "Open source WPS server with workflow execution capabilities"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/context.jsonld",
  "@id": "#zoo-wps-engine",
  "@type": "WorkflowEngine",
  "name": "ZOO-Project WPS",
  "version": "1.9.0",
  "description": "Open source WPS server with workflow execution capabilities"
}
```

#### ttl
```ttl
@prefix ns1: <http://schema.org/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .

<file:///github/workspace/#zoo-wps-engine> a wfprov:WorkflowEngine ;
    rdfs:label "ZOO-Project WPS" ;
    ns1:version "1.9.0" ;
    rdfs:comment "Open source WPS server with workflow execution capabilities" .


```


### Apache Airflow Engine
#### json
```json
{
  "@id": "#airflow-engine",
  "@type": "WorkflowEngine",
  "name": "Apache Airflow",
  "version": "2.7.0",
  "description": "Platform to programmatically author, schedule and monitor workflows"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/context.jsonld",
  "@id": "#airflow-engine",
  "@type": "WorkflowEngine",
  "name": "Apache Airflow",
  "version": "2.7.0",
  "description": "Platform to programmatically author, schedule and monitor workflows"
}
```

#### ttl
```ttl
@prefix ns1: <http://schema.org/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .

<file:///github/workspace/#airflow-engine> a wfprov:WorkflowEngine ;
    rdfs:label "Apache Airflow" ;
    ns1:version "2.7.0" ;
    rdfs:comment "Platform to programmatically author, schedule and monitor workflows" .


```


### CWL Runner
#### json
```json
{
  "@id": "#cwl-runner",
  "@type": "WorkflowEngine",
  "name": "cwltool",
  "version": "3.1.20231114134824",
  "description": "Reference implementation of the Common Workflow Language"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/context.jsonld",
  "@id": "#cwl-runner",
  "@type": "WorkflowEngine",
  "name": "cwltool",
  "version": "3.1.20231114134824",
  "description": "Reference implementation of the Common Workflow Language"
}
```

#### ttl
```ttl
@prefix ns1: <http://schema.org/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .

<file:///github/workspace/#cwl-runner> a wfprov:WorkflowEngine ;
    rdfs:label "cwltool" ;
    ns1:version "3.1.20231114134824" ;
    rdfs:comment "Reference implementation of the Common Workflow Language" .


```


### cwltool Engine (Real Execution)
#### json
```json
{
  "@id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
  "@type": "WorkflowEngine",
  "name": "cwltool",
  "version": "3.1.20251031082601",
  "description": "Common Workflow Language reference implementation with provenance tracking support"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/context.jsonld",
  "@id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
  "@type": "WorkflowEngine",
  "name": "cwltool",
  "version": "3.1.20251031082601",
  "description": "Common Workflow Language reference implementation with provenance tracking support"
}
```

#### ttl
```ttl
@prefix ns1: <http://schema.org/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .

<urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> a wfprov:WorkflowEngine ;
    rdfs:label "cwltool" ;
    ns1:version "3.1.20251031082601" ;
    rdfs:comment "Common Workflow Language reference implementation with provenance tracking support" .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A software agent that executes workflows
type: object
properties:
  '@id':
    type: string
    format: uri
    description: Unique identifier for the workflow engine
  '@type':
    const: WorkflowEngine
    description: Type must be WorkflowEngine
  name:
    type: string
    description: Name of the workflow engine
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  version:
    type: string
    description: Version of the workflow engine
    x-jsonld-id: http://schema.org/version
  description:
    type: string
    description: Description of the workflow engine
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#comment
required:
- '@id'
- '@type'
x-jsonld-extra-terms:
  WorkflowEngine: http://purl.org/wf4ever/wfprov#WorkflowEngine
x-jsonld-vocab: http://purl.org/wf4ever/wfprov#
x-jsonld-prefixes:
  wfprov: http://purl.org/wf4ever/wfprov#
  rdfs: http://www.w3.org/2000/01/rdf-schema#
  prov: http://www.w3.org/ns/prov#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/wfprov#",
    "WorkflowEngine": "wfprov:WorkflowEngine",
    "name": "rdfs:label",
    "version": "http://schema.org/version",
    "description": "rdfs:comment",
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "prov": "http://www.w3.org/ns/prov#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/context.jsonld)

## Sources

* [Workflow Provenance Ontology - WorkflowEngine](http://purl.org/wf4ever/wfprov#WorkflowEngine)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfprov/WorkflowEngine`

