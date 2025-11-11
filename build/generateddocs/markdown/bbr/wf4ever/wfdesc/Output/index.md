
# wfdesc:Output (Datatype)

`ogc.bbr.wf4ever.wfdesc.Output` *v1.0*

An output parameter from a workflow process. Outputs produce data that can be consumed by inputs of other processes or as final workflow results.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfdesc:Output

## Description

An **Output** is a parameter that produces data from a workflow process. Outputs can:
- Produce final workflow results
- Feed data to inputs of other processes via DataLinks
- Be intermediate results in a workflow

## Class Hierarchy

```
wfdesc:Parameter
└── wfdesc:Output
```

## Usage in Workflows

Outputs are declared using the `hasOutput` property on a Process.

## Data Flow

Outputs can be connected to Inputs via DataLinks.

## Related Classes

- **Parameter**: Base class (parent)
- **Input**: Complementary class for process inputs
- **DataLink**: Connects Outputs to Inputs (Output is source)
- **Process**: Container that has outputs via `hasOutput` property

## Examples

### Workflow Output Parameter
#### json
```json
{
  "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/outputs",
  "@type": "Output",
  "name": "outputs",
  "description": "Processed mangrove mapping results"
}
```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Output/context.jsonld",
  "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/outputs",
  "@type": "Output",
  "name": "outputs",
  "description": "Processed mangrove mapping results"
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/outputs> a wfdesc:Output ;
    rdfs:label "outputs" ;
    rdfs:comment "Processed mangrove mapping results" .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An output parameter from a workflow process
type: object
allOf:
- $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Parameter/schema.yaml
properties:
  '@type':
    const: Output
    description: Type identifier for a wfdesc Output
x-jsonld-extra-terms:
  Output: http://purl.org/wf4ever/wfdesc#Output
  name: http://www.w3.org/2000/01/rdf-schema#label
  description: http://www.w3.org/2000/01/rdf-schema#comment
x-jsonld-prefixes:
  wfdesc: http://purl.org/wf4ever/wfdesc#
  rdfs: http://www.w3.org/2000/01/rdf-schema#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Output/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Output/schema.yaml)


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
    "Output": "wfdesc:Output",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Output/context.jsonld)

## Sources

* [Workflow Description Ontology - Output](http://purl.org/wf4ever/wfdesc#Output)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfdesc/Output`

