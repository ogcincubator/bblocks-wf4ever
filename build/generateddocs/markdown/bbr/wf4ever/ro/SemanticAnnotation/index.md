
# ro:SemanticAnnotation (Datatype)

`ogc.bbr.wf4ever.ro.SemanticAnnotation` *v1.0*

A semantic annotation is a specialization of ao:Annotation which requires that the annotation body points to an RDF Graph containing semantic information about the annotated resource.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# ro:SemanticAnnotation

## Description

A **SemanticAnnotation** is a specialization of `ao:Annotation` which requires that the annotation body (`ao:body`) points to an **RDF Graph**. This graph contains semantic information about the annotated resource, expressed using RDF triples.

This might be a Named Graph or a resource which can be resolved separately from the URI given by `ao:body`.

The RDF graph SHOULD mention the resources identified by `ao:annotatesResource`, preferably by using their URIs as subject or object of RDF statements.

## Relations

- Annotates resources via `ao:annotatesResource`
- Has a semantic body (RDF Graph) via `ao:body`
- Subclass of `ao:Annotation` from the Annotation Ontology

## Difference from ao:hasTopic

Note that the use of `ao:body` in SemanticAnnotation is distinct from `ao:hasTopic`:
- **`ao:body`**: The RDF graph is the annotation content (it describes/mentions the annotated resource)
- **`ao:hasTopic`**: The RDF graph is the "topic" or "bookmark" of the annotated resource

For `ro:SemanticAnnotation`, the graph body merely needs to **mention** the annotated resource (e.g., to give it a `dc:title` or to relate it to other resources), without necessarily being its "topic".

## Use Cases

- Semantic metadata expressed in RDF (e.g., Dublin Core, FOAF, PROV-O)
- Linking resources using semantic relationships
- Provenance graphs describing resource creation
- Quality assessments with structured vocabularies

## Examples

### Basic Semantic Annotation
#### json
```json
{
  "@id": "#semantic-annotation-1",
  "@type": "SemanticAnnotation",
  "annotatesResource": "data/results.csv",
  "body": ".ro/annotations/metadata-1.ttl",
  "created": "2025-11-07T10:00:00Z",
  "creator": "https://orcid.org/0000-0002-1825-0097"
}

```


### Multi-resource Annotation
#### json
```json
{
  "@id": ".ro/annotations/provenance-annotation",
  "@type": "SemanticAnnotation",
  "annotatesResource": [
    "workflow/ndvi-calculation.cwl",
    "data/ndvi-result.tif"
  ],
  "body": ".ro/annotations/provenance-graph.ttl",
  "created": "2025-11-07T14:30:00Z",
  "creator": "https://orcid.org/0000-0002-1825-0097"
}

```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A semantic annotation with an RDF Graph body
type: object
properties:
  '@id':
    type: string
    format: uri
    description: Unique identifier for the annotation
  '@type':
    const: SemanticAnnotation
    description: Type must be SemanticAnnotation
  body:
    type: string
    format: uri
    description: URI pointing to an RDF Graph containing the semantic annotation content
  annotatesResource:
    oneOf:
    - type: string
      format: uri
    - type: array
      items:
        type: string
        format: uri
    description: The resource(s) that this annotation describes
  created:
    type: string
    format: date-time
    description: Creation date of the annotation
  creator:
    type: string
    format: uri
    description: The agent (person or organization) who created this annotation
required:
- '@id'
- '@type'
- body
- annotatesResource

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/SemanticAnnotation/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/SemanticAnnotation/schema.yaml)

## Sources

* [Research Object Ontology - SemanticAnnotation](http://purl.org/wf4ever/ro#SemanticAnnotation)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/ro/SemanticAnnotation`

