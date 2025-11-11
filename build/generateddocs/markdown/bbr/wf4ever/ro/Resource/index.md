
# ro:Resource (Datatype)

`ogc.bbr.wf4ever.ro.Resource` *v1.0*

A resource that can be aggregated in a Research Object. Resources represent any artifact that contributes to the research outcome, such as data files, workflows, documentation, or external references.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# ro:Resource

## Description

A **Resource** represents a resource that can be aggregated in a Research Object. Resources represent any artifact that contributes to the research result, such as data files, workflows, documentation, or external references.

## Relations

- Can be aggregated in a `ro:ResearchObject` via `ore:aggregates`
- Can be referenced by a `ro:FolderEntry`
- Can be the target of a `ro:AggregatedAnnotation`

## Examples

### Simple resource
#### json
```json
{
  "@id": "data/workflow_definition.cwl",
  "@type": "Resource",
  "name": "NDVI Workflow Definition",
  "description": "CWL workflow for computing NDVI from satellite imagery"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Resource/context.jsonld",
  "@id": "data/workflow_definition.cwl",
  "@type": "Resource",
  "name": "NDVI Workflow Definition",
  "description": "CWL workflow for computing NDVI from satellite imagery"
}
```

#### ttl
```ttl
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ro: <http://purl.org/wf4ever/ro#> .

<file:///github/workspace/data/workflow_definition.cwl> a ro:Resource ;
    dcterms:description "CWL workflow for computing NDVI from satellite imagery" ;
    dcterms:title "NDVI Workflow Definition" .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A resource that can be aggregated in a Research Object
type: object
properties:
  '@id':
    type: string
    format: uri
    description: Unique identifier for the resource
  '@type':
    type: string
    description: Type of the resource
  name:
    type: string
    description: Name of the resource
    x-jsonld-id: http://purl.org/dc/terms/title
  description:
    type: string
    description: Description of the resource
    x-jsonld-id: http://purl.org/dc/terms/description
required:
- '@id'
x-jsonld-extra-terms:
  Resource: http://purl.org/wf4ever/ro#Resource
x-jsonld-vocab: http://purl.org/wf4ever/ro#
x-jsonld-prefixes:
  ro: http://purl.org/wf4ever/ro#
  dcterms: http://purl.org/dc/terms/
  rdfs: http://www.w3.org/2000/01/rdf-schema#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Resource/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Resource/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/ro#",
    "Resource": "ro:Resource",
    "name": "dcterms:title",
    "description": "dcterms:description",
    "ro": "http://purl.org/wf4ever/ro#",
    "dcterms": "http://purl.org/dc/terms/",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Resource/context.jsonld)

## Sources

* [Research Object Ontology - Resource](http://purl.org/wf4ever/ro#Resource)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/ro/Resource`

