
# wf4ever:Document (Datatype)

`ogc.bbr.wf4ever.wf4ever.Document` *v1.0*

A document artifact - textual or formatted content such as PDF, HTML, or text files.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wf4ever:Document

A document artifact representing textual or formatted content.

## Examples

### PDF Report Document
#### json
```json
{"@id": "#report", "@type": "Document", "title": "Workflow Report", "format": "application/pdf"}

```

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

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/Document/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/Document/schema.yaml)

## Sources

* [Wf4Ever Ontology - Document](http://purl.org/wf4ever/wf4ever#Document)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wf4ever/Document`

