
# ro:AggregatedAnnotation (Datatype)

`ogc.bbr.wf4ever.ro.AggregatedAnnotation` *v1.0*

An annotation about resources within a Research Object. Annotations provide additional metadata, provenance information, or contextual details about aggregated resources, stored as part of the Research Object itself.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# ro:AggregatedAnnotation

## Description

An **AggregatedAnnotation** is an annotation about resources within a Research Object. It is a specialization of `ro:SemanticAnnotation` that is specifically aggregated within an `ro:ResearchObject`.

As a subclass of `ro:SemanticAnnotation`, the annotation body must point to an RDF Graph which contains the actual semantic annotation. Annotations provide additional metadata, provenance information, or contextual details about aggregated resources, stored as part of the Research Object itself.

## Relations

- Annotates one or more `ro:Resource` via `ro:annotatesAggregatedResource`
- Has an annotation body via `oa:hasBody`
- Aggregated in a `ro:ResearchObject`

## Use Cases

- Provenance metadata about a data file
- Quality description of a result
- License and attribution for a resource
- Research notes and observations

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An annotation about resources in a Research Object
type: object
properties:
  '@id':
    type: string
    format: uri
    description: Unique identifier for the annotation
  '@type':
    const: AggregatedAnnotation
    description: Type must be AggregatedAnnotation
  annotatesAggregatedResource:
    oneOf:
    - type: string
      format: uri
    - type: array
      items:
        type: string
        format: uri
    description: The resource(s) that this annotation describes
    x-jsonld-id: http://purl.org/wf4ever/ro#annotatesAggregatedResource
    x-jsonld-type: '@id'
  body:
    type: string
    format: uri
    description: The body of the annotation (typically a URI to an annotation document)
    x-jsonld-id: http://www.w3.org/ns/oa#hasBody
    x-jsonld-type: '@id'
  created:
    type: string
    format: date-time
    description: Creation date of the annotation
    x-jsonld-id: http://purl.org/dc/terms/created
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
required:
- '@id'
- '@type'
- annotatesAggregatedResource
x-jsonld-extra-terms:
  AggregatedAnnotation: http://purl.org/wf4ever/ro#AggregatedAnnotation
x-jsonld-vocab: http://purl.org/wf4ever/ro#
x-jsonld-prefixes:
  ro: http://purl.org/wf4ever/ro#
  oa: http://www.w3.org/ns/oa#
  dcterms: http://purl.org/dc/terms/

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/AggregatedAnnotation/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/AggregatedAnnotation/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/ro#",
    "AggregatedAnnotation": "ro:AggregatedAnnotation",
    "annotatesAggregatedResource": {
      "@id": "ro:annotatesAggregatedResource",
      "@type": "@id"
    },
    "body": {
      "@id": "oa:hasBody",
      "@type": "@id"
    },
    "created": {
      "@id": "dcterms:created",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "ro": "http://purl.org/wf4ever/ro#",
    "oa": "http://www.w3.org/ns/oa#",
    "dcterms": "http://purl.org/dc/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/AggregatedAnnotation/context.jsonld)

## Sources

* [Research Object Ontology - AggregatedAnnotation](http://purl.org/wf4ever/ro#AggregatedAnnotation)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/ro/AggregatedAnnotation`

