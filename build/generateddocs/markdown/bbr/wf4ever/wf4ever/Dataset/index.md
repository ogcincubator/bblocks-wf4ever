
# wf4ever:Dataset (Datatype)

`ogc.bbr.wf4ever.wf4ever.Dataset` *v1.0*

A dataset artifact - a collection of data values or files representing a scientific dataset.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wf4ever:Dataset

## Description

A **Dataset** is a specialization of `wfdesc:Artifact` representing a collection of data values or files that constitute a scientific dataset. Datasets are high-level data entities commonly consumed or produced by scientific workflows.

## Properties

- `@type` : Must include "Dataset"
- `title` : Dataset title or name
- `description` : Description of dataset contents
- `creator` : Dataset creator or owner
- `temporalCoverage` : Temporal extent (date range)
- `spatialCoverage` : Spatial extent (bounding box, region)


## Examples

### Remote Sensing Dataset
#### json
```json
{
  "@id": "#sentinel2-dataset",
  "@type": "Dataset",
  "title": "Sentinel-2 Imagery - Myanmar Mangroves",
  "description": "Multispectral satellite imagery",
  "temporalCoverage": "2025-08-01/2025-11-01",
  "spatialCoverage": {
    "west": 95.15,
    "south": 15.9,
    "east": 95.35,
    "north": 16.1
  }
}

```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A dataset artifact
type: object
properties:
  '@type':
    oneOf:
    - const: Dataset
    - type: array
      contains:
        const: Dataset
    description: Type must include Dataset
  title:
    type: string
    description: Dataset title
  description:
    type: string
    description: Dataset description
  creator:
    type: string
    description: Dataset creator or owner
  temporalCoverage:
    type: string
    description: Temporal coverage (e.g., date range)
  spatialCoverage:
    type: object
    description: Spatial coverage (e.g., bounding box, region)
required:
- '@type'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/Dataset/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/Dataset/schema.yaml)

## Sources

* [Wf4Ever Ontology - Dataset](http://purl.org/wf4ever/wf4ever#Dataset)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wf4ever/Dataset`

