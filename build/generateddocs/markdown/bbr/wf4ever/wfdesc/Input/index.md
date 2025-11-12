
# wfdesc:Input (Datatype)

`ogc.bbr.wf4ever.wfdesc.Input` *v1.0*

An input parameter to a workflow process. Inputs receive data from external sources or from outputs of other processes via DataLinks.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfdesc:Input

## Description

An **Input** is a parameter that receives data into a workflow process. Inputs can receive data from:
- External sources (workflow inputs)
- Outputs of other processes (via DataLinks)
- Default values or configurations

## Class Hierarchy

```
wfdesc:Parameter
└── wfdesc:Input
```

## Usage in Workflows

Inputs are declared using the `hasInput` property on a Process.

## Data Flow

Inputs can be connected to Outputs via DataLinks.

## Related Classes

- **Parameter**: Base class (parent)
- **Output**: Complementary class for process outputs
- **DataLink**: Connects Outputs to Inputs
- **Process**: Container that has inputs via `hasInput` property

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An input parameter to a workflow process
type: object
allOf:
- $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Parameter/schema.yaml
properties:
  '@type':
    const: Input
    description: Type identifier for a wfdesc Input
x-jsonld-extra-terms:
  Input: http://purl.org/wf4ever/wfdesc#Input
  name: http://www.w3.org/2000/01/rdf-schema#label
  description: http://www.w3.org/2000/01/rdf-schema#comment
x-jsonld-prefixes:
  wfdesc: http://purl.org/wf4ever/wfdesc#
  rdfs: http://www.w3.org/2000/01/rdf-schema#

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/schema.yaml)


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
    "Input": "wfdesc:Input",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/context.jsonld)

## Sources

* [Workflow Description Ontology - Input](http://purl.org/wf4ever/wfdesc#Input)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/wfdesc/Input`

