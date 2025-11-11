
# wfdesc:Parameter (Datatype)

`ogc.bbr.wf4ever.wfdesc.Parameter` *v1.0*

A parameter (input or output) of a workflow process. This is the base class for Input, Output, and Configuration.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfdesc:Parameter

## Description

A **Parameter** is the base class for describing parameters of workflow processes. In wfdesc, parameters represent any kind of data port that can be connected in a workflow.

## Class Hierarchy

```
wfdesc:Parameter (base class)
├── wfdesc:Input (input parameter)
└── wfdesc:Output (output parameter)
```

## Usage

Parameters are typically not used directly but through their subclasses (Input, Output). They represent the interface points of a Process and can be associated with Artifacts that describe the data types.

## Related Classes

- **Input**: A parameter that receives data into a process
- **Output**: A parameter that produces data from a process
- **Artifact**: Describes the type of data associated with a parameter
- **Process**: The class that has parameters

## Examples

### Simple Parameter
#### json
```json
{
  "@type": "Parameter",
  "@id": "http://example.org/workflow/param1",
  "name": "dataParameter",
  "description": "A generic parameter for data flow"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Parameter/context.jsonld",
  "@type": "Parameter",
  "@id": "http://example.org/workflow/param1",
  "name": "dataParameter",
  "description": "A generic parameter for data flow"
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<http://example.org/workflow/param1> a wfdesc:Parameter ;
    rdfs:label "dataParameter" ;
    rdfs:comment "A generic parameter for data flow" .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A parameter of a workflow process
type: object
properties:
  '@type':
    type: string
    description: Type identifier for a wfdesc Parameter or its subclasses
  '@id':
    type: string
    format: uri
    description: Unique identifier for this parameter
  name:
    type: string
    description: Name of the parameter
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  description:
    type: string
    description: Description of the parameter
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#comment
  hasArtifact:
    type: object
    description: Links this parameter to an artifact containing concrete data or values
    properties:
      '@type':
        const: Artifact
      '@id':
        type: string
        format: uri
      value:
        description: The concrete value or data reference
      description:
        type: string
        x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#comment
    required:
    - '@type'
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasArtifact
    x-jsonld-type: '@id'
x-jsonld-extra-terms:
  Parameter: http://purl.org/wf4ever/wfdesc#Parameter
x-jsonld-prefixes:
  wfdesc: http://purl.org/wf4ever/wfdesc#
  rdfs: http://www.w3.org/2000/01/rdf-schema#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Parameter/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Parameter/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "Parameter": "wfdesc:Parameter",
    "name": "rdfs:label",
    "description": "rdfs:comment",
    "hasArtifact": {
      "@id": "wfdesc:hasArtifact",
      "@type": "@id"
    },
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Parameter/context.jsonld)

## Sources

* [Workflow Description Ontology - Parameter](http://purl.org/wf4ever/wfdesc#Parameter)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfdesc/Parameter`

