
# wfdesc:Workflow (Datatype)

`ogc.bbr.wf4ever.wfdesc.Workflow` *v1.0*

A composite process that contains sub-processes connected by data links. Workflows are directed graphs where nodes are processes and edges are data flow connections.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfdesc:Workflow

## Description

A **Workflow** is a composite process that orchestrates multiple sub-processes connected by data flow. Workflows are directed acyclic graphs (DAGs) where:
- **Nodes** are processes (sub-processes)
- **Edges** are data links (data flow)

Workflows inherit from **Process**, so they also have inputs and outputs that define their external interface.

## Class Hierarchy

```
wfdesc:Process
└── wfdesc:Workflow
```

## Workflow Structure

A workflow has two main components:

### 1. Sub-Processes (Nodes)
The computational steps in the workflow.

### 2. Data Links (Edges)
The data flow between processes.

## Workflow Patterns

### Sequential Pipeline
```
Process1 --> Process2 --> Process3
```

### Parallel Branches (Fan-out)

![Fan-out pattern](../fan-out.png)


### Data Aggregation (Fan-in)

![Fan-in pattern](../fan-in.png)

## Nested Workflows

Workflows can contain other workflows as sub-processes using the `hasSubWorkflow` property, which is a specialization of `hasSubProcess`. This allows for hierarchical workflow composition and modular design.

## Workflow as a Black Box

From the outside, a workflow looks like a single process:
- Defined interface (hasInput, hasOutput)
- Internal structure hidden (hasSubProcess, hasDataLink)
- Can be reused as a component in larger workflows

## Related Classes

- **Process**: Parent class (Workflow is a specialized Process)
- **DataLink**: Defines data flow between sub-processes
- **Input/Output**: Define workflow interface

## Examples

### Simple Two-Step Workflow
#### json
```json
{
  "@type": "Workflow",
  "@id": "#simple-workflow",
  "name": "Simple Processing Pipeline",
  "description": "Loads and processes data",
  "hasSubProcess": [
    {
      "@type": "Process",
      "@id": "#load",
      "name": "Load Data",
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#load-output",
          "name": "data"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#process",
      "name": "Process Data",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#process-input",
          "name": "inputData"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#process-output",
          "name": "result"
        }
      ]
    }
  ],
  "hasDataLink": [
    {
      "@type": "DataLink",
      "@id": "#link1",
      "hasSource": {
        "@id": "#load-output"
      },
      "hasSink": {
        "@id": "#process-input"
      }
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/context.jsonld",
  "@type": "Workflow",
  "@id": "#simple-workflow",
  "name": "Simple Processing Pipeline",
  "description": "Loads and processes data",
  "hasSubProcess": [
    {
      "@type": "Process",
      "@id": "#load",
      "name": "Load Data",
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#load-output",
          "name": "data"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#process",
      "name": "Process Data",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#process-input",
          "name": "inputData"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#process-output",
          "name": "result"
        }
      ]
    }
  ],
  "hasDataLink": [
    {
      "@type": "DataLink",
      "@id": "#link1",
      "hasSource": {
        "@id": "#load-output"
      },
      "hasSink": {
        "@id": "#process-input"
      }
    }
  ]
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<file:///github/workspace/#simple-workflow> a wfdesc:Workflow ;
    rdfs:label "Simple Processing Pipeline" ;
    wfdesc:hasDataLink <file:///github/workspace/#link1> ;
    wfdesc:hasSubProcess <file:///github/workspace/#load>,
        <file:///github/workspace/#process> ;
    rdfs:comment "Loads and processes data" .

<file:///github/workspace/#link1> a wfdesc:DataLink ;
    wfdesc:hasSink <file:///github/workspace/#process-input> ;
    wfdesc:hasSource <file:///github/workspace/#load-output> .

<file:///github/workspace/#load> a wfdesc:Process ;
    rdfs:label "Load Data" ;
    wfdesc:hasOutput <file:///github/workspace/#load-output> .

<file:///github/workspace/#process> a wfdesc:Process ;
    rdfs:label "Process Data" ;
    wfdesc:hasInput <file:///github/workspace/#process-input> ;
    wfdesc:hasOutput <file:///github/workspace/#process-output> .

<file:///github/workspace/#process-output> a wfdesc:Output ;
    rdfs:label "result" .

<file:///github/workspace/#load-output> a wfdesc:Output ;
    rdfs:label "data" .

<file:///github/workspace/#process-input> a wfdesc:Input ;
    rdfs:label "inputData" .


```


### NDVI Calculation Workflow
#### json
```json
{
  "@type": "Workflow",
  "@id": "http://example.org/workflows/ndvi",
  "name": "NDVI Calculation Pipeline",
  "description": "Complete workflow for NDVI calculation from satellite imagery",
  "hasInput": [
    {
      "@type": "Input",
      "@id": "#wf-input",
      "name": "satelliteImage",
      "description": "Input satellite image (multispectral)"
    }
  ],
  "hasOutput": [
    {
      "@type": "Output",
      "@id": "#wf-output",
      "name": "ndviResult",
      "description": "Calculated NDVI raster"
    }
  ],
  "hasSubProcess": [
    {
      "@type": "Process",
      "@id": "#extract-bands",
      "name": "Extract Bands",
      "description": "Extract NIR and Red bands",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#extract-input"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#nir-band",
          "name": "nirBand"
        },
        {
          "@type": "Output",
          "@id": "#red-band",
          "name": "redBand"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#calculate-ndvi",
      "name": "Calculate NDVI",
      "description": "Compute NDVI from bands",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#ndvi-nir-input",
          "name": "nir"
        },
        {
          "@type": "Input",
          "@id": "#ndvi-red-input",
          "name": "red"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#ndvi-result",
          "name": "ndvi"
        }
      ]
    }
  ],
  "hasDataLink": [
    {
      "@type": "DataLink",
      "@id": "#link-nir",
      "hasSource": {
        "@id": "#nir-band"
      },
      "hasSink": {
        "@id": "#ndvi-nir-input"
      }
    },
    {
      "@type": "DataLink",
      "@id": "#link-red",
      "hasSource": {
        "@id": "#red-band"
      },
      "hasSink": {
        "@id": "#ndvi-red-input"
      }
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/context.jsonld",
  "@type": "Workflow",
  "@id": "http://example.org/workflows/ndvi",
  "name": "NDVI Calculation Pipeline",
  "description": "Complete workflow for NDVI calculation from satellite imagery",
  "hasInput": [
    {
      "@type": "Input",
      "@id": "#wf-input",
      "name": "satelliteImage",
      "description": "Input satellite image (multispectral)"
    }
  ],
  "hasOutput": [
    {
      "@type": "Output",
      "@id": "#wf-output",
      "name": "ndviResult",
      "description": "Calculated NDVI raster"
    }
  ],
  "hasSubProcess": [
    {
      "@type": "Process",
      "@id": "#extract-bands",
      "name": "Extract Bands",
      "description": "Extract NIR and Red bands",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#extract-input"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#nir-band",
          "name": "nirBand"
        },
        {
          "@type": "Output",
          "@id": "#red-band",
          "name": "redBand"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#calculate-ndvi",
      "name": "Calculate NDVI",
      "description": "Compute NDVI from bands",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#ndvi-nir-input",
          "name": "nir"
        },
        {
          "@type": "Input",
          "@id": "#ndvi-red-input",
          "name": "red"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#ndvi-result",
          "name": "ndvi"
        }
      ]
    }
  ],
  "hasDataLink": [
    {
      "@type": "DataLink",
      "@id": "#link-nir",
      "hasSource": {
        "@id": "#nir-band"
      },
      "hasSink": {
        "@id": "#ndvi-nir-input"
      }
    },
    {
      "@type": "DataLink",
      "@id": "#link-red",
      "hasSource": {
        "@id": "#red-band"
      },
      "hasSink": {
        "@id": "#ndvi-red-input"
      }
    }
  ]
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<http://example.org/workflows/ndvi> a wfdesc:Workflow ;
    rdfs:label "NDVI Calculation Pipeline" ;
    wfdesc:hasDataLink <file:///github/workspace/#link-nir>,
        <file:///github/workspace/#link-red> ;
    wfdesc:hasInput <file:///github/workspace/#wf-input> ;
    wfdesc:hasOutput <file:///github/workspace/#wf-output> ;
    wfdesc:hasSubProcess <file:///github/workspace/#calculate-ndvi>,
        <file:///github/workspace/#extract-bands> ;
    rdfs:comment "Complete workflow for NDVI calculation from satellite imagery" .

<file:///github/workspace/#calculate-ndvi> a wfdesc:Process ;
    rdfs:label "Calculate NDVI" ;
    wfdesc:hasInput <file:///github/workspace/#ndvi-nir-input>,
        <file:///github/workspace/#ndvi-red-input> ;
    wfdesc:hasOutput <file:///github/workspace/#ndvi-result> ;
    rdfs:comment "Compute NDVI from bands" .

<file:///github/workspace/#extract-bands> a wfdesc:Process ;
    rdfs:label "Extract Bands" ;
    wfdesc:hasInput <file:///github/workspace/#extract-input> ;
    wfdesc:hasOutput <file:///github/workspace/#nir-band>,
        <file:///github/workspace/#red-band> ;
    rdfs:comment "Extract NIR and Red bands" .

<file:///github/workspace/#extract-input> a wfdesc:Input .

<file:///github/workspace/#link-nir> a wfdesc:DataLink ;
    wfdesc:hasSink <file:///github/workspace/#ndvi-nir-input> ;
    wfdesc:hasSource <file:///github/workspace/#nir-band> .

<file:///github/workspace/#link-red> a wfdesc:DataLink ;
    wfdesc:hasSink <file:///github/workspace/#ndvi-red-input> ;
    wfdesc:hasSource <file:///github/workspace/#red-band> .

<file:///github/workspace/#ndvi-result> a wfdesc:Output ;
    rdfs:label "ndvi" .

<file:///github/workspace/#wf-input> a wfdesc:Input ;
    rdfs:label "satelliteImage" ;
    rdfs:comment "Input satellite image (multispectral)" .

<file:///github/workspace/#wf-output> a wfdesc:Output ;
    rdfs:label "ndviResult" ;
    rdfs:comment "Calculated NDVI raster" .

<file:///github/workspace/#ndvi-nir-input> a wfdesc:Input ;
    rdfs:label "nir" .

<file:///github/workspace/#ndvi-red-input> a wfdesc:Input ;
    rdfs:label "red" .

<file:///github/workspace/#nir-band> a wfdesc:Output ;
    rdfs:label "nirBand" .

<file:///github/workspace/#red-band> a wfdesc:Output ;
    rdfs:label "redBand" .


```


### Parallel Processing Workflow (Fan-out/Fan-in)
#### json
```json
{
  "@type": "Workflow",
  "@id": "#parallel-workflow",
  "name": "Parallel Analysis Workflow",
  "hasSubProcess": [
    {
      "@type": "Process",
      "@id": "#source",
      "name": "Load Source",
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#source-out"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#analyze-vegetation",
      "name": "Vegetation Analysis",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#veg-in"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#veg-out"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#analyze-water",
      "name": "Water Analysis",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#water-in"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#water-out"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#merge-results",
      "name": "Merge Results",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#merge-in1"
        },
        {
          "@type": "Input",
          "@id": "#merge-in2"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#final-out"
        }
      ]
    }
  ],
  "hasDataLink": [
    {
      "@type": "DataLink",
      "@id": "#link-to-veg",
      "hasSource": {
        "@id": "#source-out"
      },
      "hasSink": {
        "@id": "#veg-in"
      }
    },
    {
      "@type": "DataLink",
      "@id": "#link-to-water",
      "hasSource": {
        "@id": "#source-out"
      },
      "hasSink": {
        "@id": "#water-in"
      }
    },
    {
      "@type": "DataLink",
      "@id": "#link-veg-to-merge",
      "hasSource": {
        "@id": "#veg-out"
      },
      "hasSink": {
        "@id": "#merge-in1"
      }
    },
    {
      "@type": "DataLink",
      "@id": "#link-water-to-merge",
      "hasSource": {
        "@id": "#water-out"
      },
      "hasSink": {
        "@id": "#merge-in2"
      }
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/context.jsonld",
  "@type": "Workflow",
  "@id": "#parallel-workflow",
  "name": "Parallel Analysis Workflow",
  "hasSubProcess": [
    {
      "@type": "Process",
      "@id": "#source",
      "name": "Load Source",
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#source-out"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#analyze-vegetation",
      "name": "Vegetation Analysis",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#veg-in"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#veg-out"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#analyze-water",
      "name": "Water Analysis",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#water-in"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#water-out"
        }
      ]
    },
    {
      "@type": "Process",
      "@id": "#merge-results",
      "name": "Merge Results",
      "hasInput": [
        {
          "@type": "Input",
          "@id": "#merge-in1"
        },
        {
          "@type": "Input",
          "@id": "#merge-in2"
        }
      ],
      "hasOutput": [
        {
          "@type": "Output",
          "@id": "#final-out"
        }
      ]
    }
  ],
  "hasDataLink": [
    {
      "@type": "DataLink",
      "@id": "#link-to-veg",
      "hasSource": {
        "@id": "#source-out"
      },
      "hasSink": {
        "@id": "#veg-in"
      }
    },
    {
      "@type": "DataLink",
      "@id": "#link-to-water",
      "hasSource": {
        "@id": "#source-out"
      },
      "hasSink": {
        "@id": "#water-in"
      }
    },
    {
      "@type": "DataLink",
      "@id": "#link-veg-to-merge",
      "hasSource": {
        "@id": "#veg-out"
      },
      "hasSink": {
        "@id": "#merge-in1"
      }
    },
    {
      "@type": "DataLink",
      "@id": "#link-water-to-merge",
      "hasSource": {
        "@id": "#water-out"
      },
      "hasSink": {
        "@id": "#merge-in2"
      }
    }
  ]
}
```

#### ttl
```ttl
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .

<file:///github/workspace/#parallel-workflow> a wfdesc:Workflow ;
    rdfs:label "Parallel Analysis Workflow" ;
    wfdesc:hasDataLink <file:///github/workspace/#link-to-veg>,
        <file:///github/workspace/#link-to-water>,
        <file:///github/workspace/#link-veg-to-merge>,
        <file:///github/workspace/#link-water-to-merge> ;
    wfdesc:hasSubProcess <file:///github/workspace/#analyze-vegetation>,
        <file:///github/workspace/#analyze-water>,
        <file:///github/workspace/#merge-results>,
        <file:///github/workspace/#source> .

<file:///github/workspace/#analyze-vegetation> a wfdesc:Process ;
    rdfs:label "Vegetation Analysis" ;
    wfdesc:hasInput <file:///github/workspace/#veg-in> ;
    wfdesc:hasOutput <file:///github/workspace/#veg-out> .

<file:///github/workspace/#analyze-water> a wfdesc:Process ;
    rdfs:label "Water Analysis" ;
    wfdesc:hasInput <file:///github/workspace/#water-in> ;
    wfdesc:hasOutput <file:///github/workspace/#water-out> .

<file:///github/workspace/#final-out> a wfdesc:Output .

<file:///github/workspace/#link-to-veg> a wfdesc:DataLink ;
    wfdesc:hasSink <file:///github/workspace/#veg-in> ;
    wfdesc:hasSource <file:///github/workspace/#source-out> .

<file:///github/workspace/#link-to-water> a wfdesc:DataLink ;
    wfdesc:hasSink <file:///github/workspace/#water-in> ;
    wfdesc:hasSource <file:///github/workspace/#source-out> .

<file:///github/workspace/#link-veg-to-merge> a wfdesc:DataLink ;
    wfdesc:hasSink <file:///github/workspace/#merge-in1> ;
    wfdesc:hasSource <file:///github/workspace/#veg-out> .

<file:///github/workspace/#link-water-to-merge> a wfdesc:DataLink ;
    wfdesc:hasSink <file:///github/workspace/#merge-in2> ;
    wfdesc:hasSource <file:///github/workspace/#water-out> .

<file:///github/workspace/#merge-results> a wfdesc:Process ;
    rdfs:label "Merge Results" ;
    wfdesc:hasInput <file:///github/workspace/#merge-in1>,
        <file:///github/workspace/#merge-in2> ;
    wfdesc:hasOutput <file:///github/workspace/#final-out> .

<file:///github/workspace/#source> a wfdesc:Process ;
    rdfs:label "Load Source" ;
    wfdesc:hasOutput <file:///github/workspace/#source-out> .

<file:///github/workspace/#merge-in1> a wfdesc:Input .

<file:///github/workspace/#merge-in2> a wfdesc:Input .

<file:///github/workspace/#veg-in> a wfdesc:Input .

<file:///github/workspace/#veg-out> a wfdesc:Output .

<file:///github/workspace/#water-in> a wfdesc:Input .

<file:///github/workspace/#water-out> a wfdesc:Output .

<file:///github/workspace/#source-out> a wfdesc:Output .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A workflow composed of sub-processes and data links
type: object
allOf:
- $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/schema.yaml
properties:
  '@type':
    const: Workflow
    description: Type identifier for a wfdesc Workflow
  hasSubProcess:
    type: array
    items:
      $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/schema.yaml
    description: Sub-processes within this workflow
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasSubProcess
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
  hasDataLink:
    type: array
    items:
      $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/DataLink/schema.yaml
    description: Data flow connections between sub-processes
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasDataLink
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
x-jsonld-extra-terms:
  Workflow: http://purl.org/wf4ever/wfdesc#Workflow
  Process: http://purl.org/wf4ever/wfdesc#Process
  DataLink: http://purl.org/wf4ever/wfdesc#DataLink
  Input: http://purl.org/wf4ever/wfdesc#Input
  Output: http://purl.org/wf4ever/wfdesc#Output
  name: http://www.w3.org/2000/01/rdf-schema#label
  description: http://www.w3.org/2000/01/rdf-schema#comment
  hasInput:
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasInput
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
  hasOutput:
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasOutput
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
  hasSource:
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasSource
    x-jsonld-type: '@id'
  hasSink:
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasSink
    x-jsonld-type: '@id'
x-jsonld-prefixes:
  wfdesc: http://purl.org/wf4ever/wfdesc#
  rdfs: http://www.w3.org/2000/01/rdf-schema#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/schema.yaml)


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
    "Workflow": "wfdesc:Workflow",
    "DataLink": "wfdesc:DataLink",
    "hasSource": {
      "@id": "wfdesc:hasSource",
      "@type": "@id"
    },
    "hasSink": {
      "@id": "wfdesc:hasSink",
      "@type": "@id"
    },
    "hasSubProcess": {
      "@id": "wfdesc:hasSubProcess",
      "@type": "@id",
      "@container": "@set"
    },
    "hasDataLink": {
      "@context": {
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
        }
      },
      "@id": "wfdesc:hasDataLink",
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
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/context.jsonld)

## Sources

* [Workflow Description Ontology - Workflow](http://purl.org/wf4ever/wfdesc#Workflow)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfdesc/Workflow`

