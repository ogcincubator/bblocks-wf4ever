
# wfdesc:Process (Datatype)

`ogc.bbr.wf4ever.wfdesc.Process` *v1.0*

A computational process or task in a workflow. Processes have inputs, outputs, and perform computations. This is the base class for atomic processes and composite Workflows.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfdesc:Process

## Description

A **Process** represents a unit of computation in a workflow. It is the base class that can be:
- An **atomic process**: A single computational task (e.g., running a command-line tool)
- A **Workflow**: A composite process containing sub-processes

Processes are characterized by their inputs (what data they consume) and outputs (what data they produce).

## Class Hierarchy

```
wfdesc:Process (base class)
└── wfdesc:Workflow (composite process with sub-processes)
```

## Process Interface

The interface of a process is defined by its inputs and outputs.

## Atomic vs Composite

### Atomic Process
- Performs a single computational task
- Cannot be decomposed further in the workflow model
- Examples: Run GDAL command, Execute Python script, Call web service

### Composite Process (Workflow)
- Contains sub-processes via `hasSubProcess`
- Has internal data flow via `hasDataLink`
- Can be treated as a black box via its inputs/outputs

## Related Classes

- **Input**: Parameters that feed data into the process
- **Output**: Parameters that produce data from the process
- **Workflow**: Subclass that represents composite processes
- **DataLink**: Connects processes together in a workflow

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A computational process in a workflow
type: object
properties:
  '@type':
    oneOf:
    - const: Process
    - const: Workflow
    description: Type identifier for a wfdesc Process or Workflow
  '@id':
    type: string
    format: uri
    description: Unique identifier for this process
  name:
    type: string
    description: Name of the process
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  description:
    type: string
    description: Description of what this process does
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#comment
  hasInput:
    type: array
    items:
      $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/schema.yaml
    description: Input parameters for this process
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasInput
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
  hasOutput:
    type: array
    items:
      $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Output/schema.yaml
    description: Output parameters produced by this process
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasOutput
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
required:
- '@type'
x-jsonld-extra-terms:
  Process: http://purl.org/wf4ever/wfdesc#Process
  Input: http://purl.org/wf4ever/wfdesc#Input
  Output: http://purl.org/wf4ever/wfdesc#Output
x-jsonld-prefixes:
  wfdesc: http://purl.org/wf4ever/wfdesc#
  rdfs: http://www.w3.org/2000/01/rdf-schema#

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "Process": "wfdesc:Process",
    "Input": "wfdesc:Input",
    "Output": "wfdesc:Output",
    "name": "rdfs:label",
    "description": "rdfs:comment",
    "hasInput": {
      "@context": {
        "hasArtifact": {
          "@id": "wfdesc:hasArtifact",
          "@type": "@id"
        }
      },
      "@id": "wfdesc:hasInput",
      "@type": "@id",
      "@container": "@set"
    },
    "hasOutput": {
      "@context": {
        "hasArtifact": {
          "@id": "wfdesc:hasArtifact",
          "@type": "@id"
        }
      },
      "@id": "wfdesc:hasOutput",
      "@type": "@id",
      "@container": "@set"
    },
    "Parameter": "wfdesc:Parameter",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/context.jsonld)

## Sources

* [Workflow Description Ontology - Process](http://purl.org/wf4ever/wfdesc#Process)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/wfdesc/Process`

