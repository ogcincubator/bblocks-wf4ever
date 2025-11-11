
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

### Geospatial Input
#### json
```json
{
  "@type": "Input",
  "@id": "http://example.org/workflow/input/image",
  "name": "sourceImage",
  "description": "Source satellite image in GeoTIFF format"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/context.jsonld",
  "@type": "Input",
  "@id": "http://example.org/workflow/input/image",
  "name": "sourceImage",
  "description": "Source satellite image in GeoTIFF format"
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<http://example.org/workflow/input/image> a wfdesc:Input ;
    rdfs:label "sourceImage" ;
    rdfs:comment "Source satellite image in GeoTIFF format" .


```


### KindGrove Bounding Box Input
#### json
```json
{
  "@id": "#input-bbox-north",
  "@type": "Input",
  "name": "north",
  "description": "Northern latitude boundary for Sentinel-2 image query (Myanmar mangrove area)",
  "datatype": "float",
  "required": true,
  "exampleValue": 16.1
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/context.jsonld",
  "@id": "#input-bbox-north",
  "@type": "Input",
  "name": "north",
  "description": "Northern latitude boundary for Sentinel-2 image query (Myanmar mangrove area)",
  "datatype": "float",
  "required": true,
  "exampleValue": 16.1
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<file:///github/workspace/#input-bbox-north> a wfdesc:Input ;
    rdfs:label "north" ;
    rdfs:comment "Northern latitude boundary for Sentinel-2 image query (Myanmar mangrove area)" .


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

