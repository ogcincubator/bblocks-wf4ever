
# wfdesc:Process (Datatype)

`ogc.bbr.wf4ever.wfdesc.Process` *v1.0*

A computational process or task in a workflow. Processes have inputs, outputs, and perform computations. This is the base class for atomic processes and composite Workflows.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfdesc:Process

## Description

A **Process** represents a unit of computation in a workflow. It is the base class that can be:
- An **atomic process**: A single computational task (e.g., running a command-line tool)
- A **Workflow**: A composite process containing sub-processes

Processes are characterized by their inputs (what data they consume) and outputs (what data they produce).

## Class Hierarchy

```
wfdesc:Process (base class)
└── wfdesc:Workflow (composite process with sub-processes)
```

## Process Interface

The interface of a process is defined by its inputs and outputs.

## Atomic vs Composite

### Atomic Process
- Performs a single computational task
- Cannot be decomposed further in the workflow model
- Examples: Run GDAL command, Execute Python script, Call web service

### Composite Process (Workflow)
- Contains sub-processes via `hasSubProcess`
- Has internal data flow via `hasDataLink`
- Can be treated as a black box via its inputs/outputs

## Related Classes

- **Input**: Parameters that feed data into the process
- **Output**: Parameters that produce data from the process
- **Workflow**: Subclass that represents composite processes
- **DataLink**: Connects processes together in a workflow

## Examples

### Simple Process - NDVI Calculator
#### json
```json
{
  "@type": "Process",
  "@id": "http://example.org/processes/ndvi",
  "name": "NDVI Calculator",
  "description": "Calculates Normalized Difference Vegetation Index from NIR and Red bands",
  "hasInput": [
    {
      "@type": "Input",
      "@id": "#input-nir",
      "name": "nearInfrared",
      "description": "Near-infrared band"
    },
    {
      "@type": "Input",
      "@id": "#input-red",
      "name": "redBand",
      "description": "Red band"
    }
  ],
  "hasOutput": [
    {
      "@type": "Output",
      "@id": "#output-ndvi",
      "name": "ndviLayer",
      "description": "Calculated NDVI raster layer"
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/context.jsonld",
  "@type": "Process",
  "@id": "http://example.org/processes/ndvi",
  "name": "NDVI Calculator",
  "description": "Calculates Normalized Difference Vegetation Index from NIR and Red bands",
  "hasInput": [
    {
      "@type": "Input",
      "@id": "#input-nir",
      "name": "nearInfrared",
      "description": "Near-infrared band"
    },
    {
      "@type": "Input",
      "@id": "#input-red",
      "name": "redBand",
      "description": "Red band"
    }
  ],
  "hasOutput": [
    {
      "@type": "Output",
      "@id": "#output-ndvi",
      "name": "ndviLayer",
      "description": "Calculated NDVI raster layer"
    }
  ]
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<http://example.org/processes/ndvi> a wfdesc:Process ;
    rdfs:label "NDVI Calculator" ;
    wfdesc:hasInput <file:///github/workspace/#input-nir>,
        <file:///github/workspace/#input-red> ;
    wfdesc:hasOutput <file:///github/workspace/#output-ndvi> ;
    rdfs:comment "Calculates Normalized Difference Vegetation Index from NIR and Red bands" .

<file:///github/workspace/#input-nir> a wfdesc:Input ;
    rdfs:label "nearInfrared" ;
    rdfs:comment "Near-infrared band" .

<file:///github/workspace/#input-red> a wfdesc:Input ;
    rdfs:label "redBand" ;
    rdfs:comment "Red band" .

<file:///github/workspace/#output-ndvi> a wfdesc:Output ;
    rdfs:label "ndviLayer" ;
    rdfs:comment "Calculated NDVI raster layer" .


```


### Geospatial Reprojection Process
#### json
```json
{
  "@type": "Process",
  "@id": "#reproject-process",
  "name": "Reproject Raster",
  "description": "Reprojects a raster dataset to a target coordinate reference system",
  "hasInput": [
    {
      "@type": "Input",
      "@id": "#input-source-raster",
      "name": "sourceRaster",
      "description": "Source raster in original CRS"
    },
    {
      "@type": "Input",
      "@id": "#input-target-crs",
      "name": "targetCRS",
      "description": "Target coordinate reference system (EPSG code)"
    }
  ],
  "hasOutput": [
    {
      "@type": "Output",
      "@id": "#output-reprojected",
      "name": "reprojectedRaster",
      "description": "Raster reprojected to target CRS"
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/context.jsonld",
  "@type": "Process",
  "@id": "#reproject-process",
  "name": "Reproject Raster",
  "description": "Reprojects a raster dataset to a target coordinate reference system",
  "hasInput": [
    {
      "@type": "Input",
      "@id": "#input-source-raster",
      "name": "sourceRaster",
      "description": "Source raster in original CRS"
    },
    {
      "@type": "Input",
      "@id": "#input-target-crs",
      "name": "targetCRS",
      "description": "Target coordinate reference system (EPSG code)"
    }
  ],
  "hasOutput": [
    {
      "@type": "Output",
      "@id": "#output-reprojected",
      "name": "reprojectedRaster",
      "description": "Raster reprojected to target CRS"
    }
  ]
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<file:///github/workspace/#reproject-process> a wfdesc:Process ;
    rdfs:label "Reproject Raster" ;
    wfdesc:hasInput <file:///github/workspace/#input-source-raster>,
        <file:///github/workspace/#input-target-crs> ;
    wfdesc:hasOutput <file:///github/workspace/#output-reprojected> ;
    rdfs:comment "Reprojects a raster dataset to a target coordinate reference system" .

<file:///github/workspace/#input-source-raster> a wfdesc:Input ;
    rdfs:label "sourceRaster" ;
    rdfs:comment "Source raster in original CRS" .

<file:///github/workspace/#input-target-crs> a wfdesc:Input ;
    rdfs:label "targetCRS" ;
    rdfs:comment "Target coordinate reference system (EPSG code)" .

<file:///github/workspace/#output-reprojected> a wfdesc:Output ;
    rdfs:label "reprojectedRaster" ;
    rdfs:comment "Raster reprojected to target CRS" .


```


### Multi-Output Statistics Process
#### json
```json
{
  "@type": "Process",
  "@id": "#stats-calculator",
  "name": "Statistics Calculator",
  "description": "Computes statistical metrics from raster data",
  "hasInput": [
    {
      "@type": "Input",
      "@id": "#input-raster",
      "name": "inputRaster",
      "description": "Input raster for statistical analysis"
    }
  ],
  "hasOutput": [
    {
      "@type": "Output",
      "@id": "#output-mean",
      "name": "meanValue",
      "description": "Mean pixel value"
    },
    {
      "@type": "Output",
      "@id": "#output-stdev",
      "name": "standardDeviation",
      "description": "Standard deviation of pixel values"
    },
    {
      "@type": "Output",
      "@id": "#output-histogram",
      "name": "histogram",
      "description": "Histogram of value distribution"
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/context.jsonld",
  "@type": "Process",
  "@id": "#stats-calculator",
  "name": "Statistics Calculator",
  "description": "Computes statistical metrics from raster data",
  "hasInput": [
    {
      "@type": "Input",
      "@id": "#input-raster",
      "name": "inputRaster",
      "description": "Input raster for statistical analysis"
    }
  ],
  "hasOutput": [
    {
      "@type": "Output",
      "@id": "#output-mean",
      "name": "meanValue",
      "description": "Mean pixel value"
    },
    {
      "@type": "Output",
      "@id": "#output-stdev",
      "name": "standardDeviation",
      "description": "Standard deviation of pixel values"
    },
    {
      "@type": "Output",
      "@id": "#output-histogram",
      "name": "histogram",
      "description": "Histogram of value distribution"
    }
  ]
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<file:///github/workspace/#stats-calculator> a wfdesc:Process ;
    rdfs:label "Statistics Calculator" ;
    wfdesc:hasInput <file:///github/workspace/#input-raster> ;
    wfdesc:hasOutput <file:///github/workspace/#output-histogram>,
        <file:///github/workspace/#output-mean>,
        <file:///github/workspace/#output-stdev> ;
    rdfs:comment "Computes statistical metrics from raster data" .

<file:///github/workspace/#input-raster> a wfdesc:Input ;
    rdfs:label "inputRaster" ;
    rdfs:comment "Input raster for statistical analysis" .

<file:///github/workspace/#output-histogram> a wfdesc:Output ;
    rdfs:label "histogram" ;
    rdfs:comment "Histogram of value distribution" .

<file:///github/workspace/#output-mean> a wfdesc:Output ;
    rdfs:label "meanValue" ;
    rdfs:comment "Mean pixel value" .

<file:///github/workspace/#output-stdev> a wfdesc:Output ;
    rdfs:label "standardDeviation" ;
    rdfs:comment "Standard deviation of pixel values" .


```


### KindGrove Mangrove Analysis Process
#### json
```json
{
  "@id": "https://github.com/starling-foundries/KindGrove#mangrove-analysis",
  "@type": "Process",
  "name": "Mangrove Biomass Analysis",
  "description": "Analyzes mangrove biomass using Sentinel-2 satellite imagery within a specified bounding box",
  "hasInput": [
    {
      "@id": "#input-north",
      "@type": "Input",
      "name": "north",
      "description": "Northern latitude of bounding box",
      "datatype": "float"
    },
    {
      "@id": "#input-south",
      "@type": "Input",
      "name": "south",
      "description": "Southern latitude of bounding box",
      "datatype": "float"
    },
    {
      "@id": "#input-east",
      "@type": "Input",
      "name": "east",
      "description": "Eastern longitude of bounding box",
      "datatype": "float"
    },
    {
      "@id": "#input-west",
      "@type": "Input",
      "name": "west",
      "description": "Western longitude of bounding box",
      "datatype": "float"
    },
    {
      "@id": "#input-cloud-cover",
      "@type": "Input",
      "name": "cloud_cover_max",
      "description": "Maximum acceptable cloud cover percentage",
      "datatype": "float"
    },
    {
      "@id": "#input-days-back",
      "@type": "Input",
      "name": "days_back",
      "description": "Number of days to look back for imagery",
      "datatype": "integer"
    },
    {
      "@id": "#input-output-dir",
      "@type": "Input",
      "name": "output_dir",
      "description": "Output directory name",
      "datatype": "string"
    }
  ],
  "hasOutput": [
    {
      "@id": "#output-result",
      "@type": "Output",
      "name": "result",
      "description": "Directory containing analysis results including biomass maps and statistics",
      "datatype": "Directory"
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/context.jsonld",
  "@id": "https://github.com/starling-foundries/KindGrove#mangrove-analysis",
  "@type": "Process",
  "name": "Mangrove Biomass Analysis",
  "description": "Analyzes mangrove biomass using Sentinel-2 satellite imagery within a specified bounding box",
  "hasInput": [
    {
      "@id": "#input-north",
      "@type": "Input",
      "name": "north",
      "description": "Northern latitude of bounding box",
      "datatype": "float"
    },
    {
      "@id": "#input-south",
      "@type": "Input",
      "name": "south",
      "description": "Southern latitude of bounding box",
      "datatype": "float"
    },
    {
      "@id": "#input-east",
      "@type": "Input",
      "name": "east",
      "description": "Eastern longitude of bounding box",
      "datatype": "float"
    },
    {
      "@id": "#input-west",
      "@type": "Input",
      "name": "west",
      "description": "Western longitude of bounding box",
      "datatype": "float"
    },
    {
      "@id": "#input-cloud-cover",
      "@type": "Input",
      "name": "cloud_cover_max",
      "description": "Maximum acceptable cloud cover percentage",
      "datatype": "float"
    },
    {
      "@id": "#input-days-back",
      "@type": "Input",
      "name": "days_back",
      "description": "Number of days to look back for imagery",
      "datatype": "integer"
    },
    {
      "@id": "#input-output-dir",
      "@type": "Input",
      "name": "output_dir",
      "description": "Output directory name",
      "datatype": "string"
    }
  ],
  "hasOutput": [
    {
      "@id": "#output-result",
      "@type": "Output",
      "name": "result",
      "description": "Directory containing analysis results including biomass maps and statistics",
      "datatype": "Directory"
    }
  ]
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<https://github.com/starling-foundries/KindGrove#mangrove-analysis> a wfdesc:Process ;
    rdfs:label "Mangrove Biomass Analysis" ;
    wfdesc:hasInput <file:///github/workspace/#input-cloud-cover>,
        <file:///github/workspace/#input-days-back>,
        <file:///github/workspace/#input-east>,
        <file:///github/workspace/#input-north>,
        <file:///github/workspace/#input-output-dir>,
        <file:///github/workspace/#input-south>,
        <file:///github/workspace/#input-west> ;
    wfdesc:hasOutput <file:///github/workspace/#output-result> ;
    rdfs:comment "Analyzes mangrove biomass using Sentinel-2 satellite imagery within a specified bounding box" .

<file:///github/workspace/#input-cloud-cover> a wfdesc:Input ;
    rdfs:label "cloud_cover_max" ;
    rdfs:comment "Maximum acceptable cloud cover percentage" .

<file:///github/workspace/#input-days-back> a wfdesc:Input ;
    rdfs:label "days_back" ;
    rdfs:comment "Number of days to look back for imagery" .

<file:///github/workspace/#input-east> a wfdesc:Input ;
    rdfs:label "east" ;
    rdfs:comment "Eastern longitude of bounding box" .

<file:///github/workspace/#input-north> a wfdesc:Input ;
    rdfs:label "north" ;
    rdfs:comment "Northern latitude of bounding box" .

<file:///github/workspace/#input-output-dir> a wfdesc:Input ;
    rdfs:label "output_dir" ;
    rdfs:comment "Output directory name" .

<file:///github/workspace/#input-south> a wfdesc:Input ;
    rdfs:label "south" ;
    rdfs:comment "Southern latitude of bounding box" .

<file:///github/workspace/#input-west> a wfdesc:Input ;
    rdfs:label "west" ;
    rdfs:comment "Western longitude of bounding box" .

<file:///github/workspace/#output-result> a wfdesc:Output ;
    rdfs:label "result" ;
    rdfs:comment "Directory containing analysis results including biomass maps and statistics" .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A computational process in a workflow
type: object
properties:
  '@type':
    oneOf:
    - const: Process
    - const: Workflow
    description: Type identifier for a wfdesc Process or Workflow
  '@id':
    type: string
    format: uri
    description: Unique identifier for this process
  name:
    type: string
    description: Name of the process
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  description:
    type: string
    description: Description of what this process does
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#comment
  hasInput:
    type: array
    items:
      $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Input/schema.yaml
    description: Input parameters for this process
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasInput
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
  hasOutput:
    type: array
    items:
      $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Output/schema.yaml
    description: Output parameters produced by this process
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasOutput
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
required:
- '@type'
x-jsonld-extra-terms:
  Process: http://purl.org/wf4ever/wfdesc#Process
  Input: http://purl.org/wf4ever/wfdesc#Input
  Output: http://purl.org/wf4ever/wfdesc#Output
x-jsonld-prefixes:
  wfdesc: http://purl.org/wf4ever/wfdesc#
  rdfs: http://www.w3.org/2000/01/rdf-schema#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "Process": "wfdesc:Process",
    "Input": "wfdesc:Input",
    "Output": "wfdesc:Output",
    "name": "rdfs:label",
    "description": "rdfs:comment",
    "hasInput": {
      "@context": {
        "hasArtifact": {
          "@id": "wfdesc:hasArtifact",
          "@type": "@id"
        }
      },
      "@id": "wfdesc:hasInput",
      "@type": "@id",
      "@container": "@set"
    },
    "hasOutput": {
      "@context": {
        "hasArtifact": {
          "@id": "wfdesc:hasArtifact",
          "@type": "@id"
        }
      },
      "@id": "wfdesc:hasOutput",
      "@type": "@id",
      "@container": "@set"
    },
    "Parameter": "wfdesc:Parameter",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/context.jsonld)

## Sources

* [Workflow Description Ontology - Process](http://purl.org/wf4ever/wfdesc#Process)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfdesc/Process`

