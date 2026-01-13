
# wf4ever:Image (Datatype)

`ogc.bbr.wf4ever.wf4ever.Image` *v1.0*

An image artifact - visual representation such as PNG, JPEG, or raster geospatial imagery.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wf4ever:Image

An image artifact - visual representation (PNG, JPEG, GeoTIFF).

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An image artifact
type: object
properties:
  '@type':
    oneOf:
    - const: Image
    - type: array
      contains:
        const: Image
  format:
    type: string
    description: Image format (e.g., "image/png", "image/tiff")
  width:
    type: integer
  height:
    type: integer
required:
- '@type'

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/Image/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/Image/schema.yaml)

## Sources

* [Wf4Ever Ontology - Image](http://purl.org/wf4ever/wf4ever#Image)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/wf4ever/Image`

