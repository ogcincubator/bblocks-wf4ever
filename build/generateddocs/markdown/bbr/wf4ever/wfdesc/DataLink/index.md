
# wfdesc:DataLink (Datatype)

`ogc.bbr.wf4ever.wfdesc.DataLink` *v1.0*

A connection between processes in a workflow, linking an output of one process to an input of another process. DataLinks define the data flow in a workflow.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfdesc:DataLink

## Description

A **DataLink** represents a data flow connection between processes in a workflow. It describes how the output of one process is connected to the input of another process, defining the data dependencies between workflow steps.

## Relations

- Links a `wfdesc:Output` (source) to a `wfdesc:Input` (sink)
- Used by `wfdesc:Workflow` via `hasDataLink`
- Defines the data flow between processes

## Examples

### Simple DataLink
#### json
```json
{
  "@type": "DataLink",
  "@id": "#link-reproject-to-ndvi",
  "hasSource": {
    "@type": "Output",
    "@id": "#reproject-output",
    "name": "reprojectedImage"
  },
  "hasSink": {
    "@type": "Input",
    "@id": "#ndvi-input",
    "name": "sourceImage"
  }
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/DataLink/context.jsonld",
  "@type": "DataLink",
  "@id": "#link-reproject-to-ndvi",
  "hasSource": {
    "@type": "Output",
    "@id": "#reproject-output",
    "name": "reprojectedImage"
  },
  "hasSink": {
    "@type": "Input",
    "@id": "#ndvi-input",
    "name": "sourceImage"
  }
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<file:///github/workspace/#link-reproject-to-ndvi> a wfdesc:DataLink ;
    wfdesc:hasSink <file:///github/workspace/#ndvi-input> ;
    wfdesc:hasSource <file:///github/workspace/#reproject-output> .

<file:///github/workspace/#ndvi-input> a wfdesc:Input ;
    rdfs:label "sourceImage" .

<file:///github/workspace/#reproject-output> a wfdesc:Output ;
    rdfs:label "reprojectedImage" .


```


### DataLink with References
#### json
```json
{
  "@type": "DataLink",
  "@id": "#link1",
  "hasSource": {
    "@id": "#process1-output"
  },
  "hasSink": {
    "@id": "#process2-input"
  }
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/DataLink/context.jsonld",
  "@type": "DataLink",
  "@id": "#link1",
  "hasSource": {
    "@id": "#process1-output"
  },
  "hasSink": {
    "@id": "#process2-input"
  }
}
```

#### ttl
```ttl
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<file:///github/workspace/#link1> a wfdesc:DataLink ;
    wfdesc:hasSink <file:///github/workspace/#process2-input> ;
    wfdesc:hasSource <file:///github/workspace/#process1-output> .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A data flow connection between an output and an input in a workflow
type: object
properties:
  '@type':
    const: DataLink
    description: Type identifier for a wfdesc DataLink
  '@id':
    type: string
    format: uri
    description: Unique identifier for this data link
  hasSource:
    $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Output/schema.yaml
    description: The source output that produces data
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasSource
    x-jsonld-type: '@id'
  hasSink:
    $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/schema.yaml
    description: The sink input that consumes data
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasSink
    x-jsonld-type: '@id'
required:
- '@type'
- hasSource
- hasSink
x-jsonld-extra-terms:
  DataLink: http://purl.org/wf4ever/wfdesc#DataLink
x-jsonld-prefixes:
  wfdesc: http://purl.org/wf4ever/wfdesc#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/DataLink/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/DataLink/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "DataLink": "wfdesc:DataLink",
    "hasSource": {
      "@context": {
        "hasArtifact": {
          "@id": "wfdesc:hasArtifact",
          "@type": "@id"
        }
      },
      "@id": "wfdesc:hasSource",
      "@type": "@id"
    },
    "hasSink": {
      "@context": {
        "hasArtifact": {
          "@id": "wfdesc:hasArtifact",
          "@type": "@id"
        }
      },
      "@id": "wfdesc:hasSink",
      "@type": "@id"
    },
    "Parameter": "wfdesc:Parameter",
    "Output": "wfdesc:Output",
    "name": "rdfs:label",
    "description": "rdfs:comment",
    "Input": "wfdesc:Input",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/DataLink/context.jsonld)

## Sources

* [Workflow Description Ontology - DataLink](http://purl.org/wf4ever/wfdesc#DataLink)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfdesc/DataLink`

