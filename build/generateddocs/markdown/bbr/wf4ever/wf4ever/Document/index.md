
# wf4ever:Document (Datatype)

`ogc.bbr.wf4ever.wf4ever.Document` *v1.0*

A document artifact - textual or formatted content such as PDF, HTML, or text files.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wf4ever:Document

A document artifact representing textual or formatted content.

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A document artifact
type: object
properties:
  '@type':
    oneOf:
    - const: Document
    - type: array
      contains:
        const: Document
  title:
    type: string
  format:
    type: string
    description: Document format (e.g., "application/pdf", "text/html")
required:
- '@type'

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/Document/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/Document/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@type": {
      "@context": {}
    },
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/Document/context.jsonld)

## Sources

* [Wf4Ever Ontology - Document](http://purl.org/wf4ever/wf4ever#Document)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/wf4ever/Document`

