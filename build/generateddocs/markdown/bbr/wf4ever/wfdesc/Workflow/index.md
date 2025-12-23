
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

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A workflow composed of sub-processes and data links
type: object
allOf:
- $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/schema.yaml
properties:
  '@type':
    const: Workflow
    description: Type identifier for a wfdesc Workflow
  hasSubProcess:
    type: array
    items:
      $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Process/schema.yaml
    description: Sub-processes within this workflow
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#hasSubProcess
    x-jsonld-type: '@id'
    x-jsonld-container: '@set'
  hasDataLink:
    type: array
    items:
      $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/DataLink/schema.yaml
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

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "Process": "wfdesc:Process",
    "Input": "wfdesc:Input",
    "Output": "wfdesc:Output",
    "@type": {
      "@context": {}
    },
    "@id": {
      "@context": {}
    },
    "name": "rdfs:label",
    "description": "rdfs:comment",
    "hasInput": {
      "@context": {
        "@type": {
          "@context": {}
        },
        "@id": {
          "@context": {}
        },
        "hasArtifact": {
          "@context": {
            "@type": {
              "@context": {}
            },
            "@id": {
              "@context": {}
            }
          },
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
        "@type": {
          "@context": {}
        },
        "@id": {
          "@context": {}
        },
        "hasArtifact": {
          "@context": {
            "@type": {
              "@context": {}
            },
            "@id": {
              "@context": {}
            }
          },
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
      "@context": {
        "@type": {
          "@context": {}
        },
        "@id": {
          "@context": {}
        }
      },
      "@id": "wfdesc:hasSubProcess",
      "@type": "@id",
      "@container": "@set"
    },
    "hasDataLink": {
      "@context": {
        "@type": {
          "@context": {}
        },
        "@id": {
          "@context": {}
        },
        "hasSource": {
          "@context": {
            "@type": {
              "@context": {}
            },
            "@id": {
              "@context": {}
            },
            "hasArtifact": {
              "@context": {
                "@type": {
                  "@context": {}
                },
                "@id": {
                  "@context": {}
                }
              },
              "@id": "wfdesc:hasArtifact",
              "@type": "@id"
            }
          },
          "@id": "wfdesc:hasSource",
          "@type": "@id"
        },
        "hasSink": {
          "@context": {
            "@type": {
              "@context": {}
            },
            "@id": {
              "@context": {}
            },
            "hasArtifact": {
              "@context": {
                "@type": {
                  "@context": {}
                },
                "@id": {
                  "@context": {}
                }
              },
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
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/context.jsonld)

## Sources

* [Workflow Description Ontology - Workflow](http://purl.org/wf4ever/wfdesc#Workflow)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/wfdesc/Workflow`

