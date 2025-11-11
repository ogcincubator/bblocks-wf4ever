
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

## Examples

### Workflow Input Parameter (cloud_cover_max)
#### json
```json
{
  "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/cloud_cover_max",
  "@type": "Input",
  "name": "cloud_cover_max",
  "description": "Maximum cloud coverage percentage",
  "value": 20.0
}
```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/context.jsonld",
  "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/cloud_cover_max",
  "@type": "Input",
  "name": "cloud_cover_max",
  "description": "Maximum cloud coverage percentage",
  "value": 20.0
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/cloud_cover_max> a wfdesc:Input ;
    rdfs:label "cloud_cover_max" ;
    rdfs:comment "Maximum cloud coverage percentage" .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An input parameter to a workflow process
type: object
allOf:
- $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Parameter/schema.yaml
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

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/schema.yaml)


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
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/context.jsonld)

## Sources

* [Workflow Description Ontology - Input](http://purl.org/wf4ever/wfdesc#Input)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfdesc/Input`

