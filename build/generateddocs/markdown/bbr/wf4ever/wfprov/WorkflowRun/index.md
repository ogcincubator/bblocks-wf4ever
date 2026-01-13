
# wfprov:WorkflowRun (Datatype)

`ogc.bbr.wf4ever.wfprov.WorkflowRun` *v1.0*

An execution instance of a workflow. A WorkflowRun is a special type of ProcessRun that represents the execution of a complete workflow (wfdesc:Workflow), containing multiple ProcessRuns for its sub-processes.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfprov:WorkflowRun

## Description

A **WorkflowRun** represents an execution instance of a complete workflow. It is a specialized type of ProcessRun that represents the execution of a `wfdesc:Workflow`, containing multiple ProcessRuns for its sub-processes.

## Class Hierarchy

Inherits all properties from `wfprov:ProcessRun`.

## Relations

- Extends `wfprov:ProcessRun`
- Must be linked to a `wfdesc:Workflow` via `describedByWorkflow`
- Contains `wfprov:ProcessRun` via `hadSubProcessRun`
- Can be executed by a `wfprov:WorkflowEngine` via `wasEnactedBy`

## Example

See the real-world example from a CWLProv execution showing complete workflow provenance with temporal information (startedAtTime, endedAtTime), associated agents (cwltool), and artifacts used/generated during execution.

## Examples

### Mangrove Workflow Run with Provenance
#### json
```json
{
  "id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "type": "WorkflowRun",
  "label": "Run of workflow/packed.cwl#main",
  "describedByWorkflow": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main",
  "startedAtTime": "2025-11-03T15:14:02.032122",
  "endedAtTime": "2025-11-03T15:14:17.060218",
  "wasAssociatedWith": [
    {
      "id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "type": "WorkflowEngine",
      "label": "cwltool 3.1.20251031082601"
    },
    {
      "id": "urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f",
      "type": "Agent",
      "label": "Container execution of image r2d-2ftmp-2frepo2cwl-5fzbz5cbsp-2frepo1762182696"
    }
  ],
  "used": [
    {
      "id": "urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d",
      "value": 20.0,
      "hadRole": "cloud_cover_max"
    },
    {
      "id": "urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258",
      "value": 90,
      "hadRole": "days_back"
    },
    {
      "id": "urn:uuid:ced76ef7-e660-4798-9442-06c17a45bbea",
      "value": 95.35,
      "hadRole": "east"
    },
    {
      "id": "urn:uuid:fd57ac88-8716-40ed-8945-f83914857523",
      "value": 16.1,
      "hadRole": "north"
    }
  ],
  "generated": [
    {
      "id": "urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539",
      "type": "Artifact",
      "basename": "outputs"
    }
  ]
}


```

#### jsonld
```jsonld
{
  "@context": "https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/context.jsonld",
  "id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "type": "WorkflowRun",
  "label": "Run of workflow/packed.cwl#main",
  "describedByWorkflow": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main",
  "startedAtTime": "2025-11-03T15:14:02.032122",
  "endedAtTime": "2025-11-03T15:14:17.060218",
  "wasAssociatedWith": [
    {
      "id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "type": "WorkflowEngine",
      "label": "cwltool 3.1.20251031082601"
    },
    {
      "id": "urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f",
      "type": "Agent",
      "label": "Container execution of image r2d-2ftmp-2frepo2cwl-5fzbz5cbsp-2frepo1762182696"
    }
  ],
  "used": [
    {
      "id": "urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d",
      "value": 20.0,
      "hadRole": "cloud_cover_max"
    },
    {
      "id": "urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258",
      "value": 90,
      "hadRole": "days_back"
    },
    {
      "id": "urn:uuid:ced76ef7-e660-4798-9442-06c17a45bbea",
      "value": 95.35,
      "hadRole": "east"
    },
    {
      "id": "urn:uuid:fd57ac88-8716-40ed-8945-f83914857523",
      "value": 16.1,
      "hadRole": "north"
    }
  ],
  "generated": [
    {
      "id": "urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539",
      "type": "Artifact",
      "basename": "outputs"
    }
  ]
}
```

#### ttl
```ttl
@prefix dct: <http://purl.org/dc/terms/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c> a wfprov:WorkflowRun ;
    wfprov:describedByWorkflow <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main> ;
    wfprov:label "Run of workflow/packed.cwl#main" ;
    prov:endedAtTime "2025-11-03T15:14:17.060218"^^xsd:dateTime ;
    prov:generated <urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539> ;
    prov:startedAtTime "2025-11-03T15:14:02.032122"^^xsd:dateTime ;
    prov:used <urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d>,
        <urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258>,
        <urn:uuid:ced76ef7-e660-4798-9442-06c17a45bbea>,
        <urn:uuid:fd57ac88-8716-40ed-8945-f83914857523> ;
    prov:wasAssociatedWith <urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f>,
        <urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> .

<urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d> prov:hadRole <file:///github/workspace/cloud_cover_max> ;
    prov:value 2e+01 .

<urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f> dct:type "Agent" ;
    wfprov:label "Container execution of image r2d-2ftmp-2frepo2cwl-5fzbz5cbsp-2frepo1762182696" .

<urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> dct:type "WorkflowEngine" ;
    wfprov:label "cwltool 3.1.20251031082601" .

<urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539> a wfprov:Artifact ;
    wfprov:basename "outputs" .

<urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258> prov:hadRole <file:///github/workspace/days_back> ;
    prov:value 90 .

<urn:uuid:ced76ef7-e660-4798-9442-06c17a45bbea> prov:hadRole <file:///github/workspace/east> ;
    prov:value 9.535e+01 .

<urn:uuid:fd57ac88-8716-40ed-8945-f83914857523> prov:hadRole <file:///github/workspace/north> ;
    prov:value 1.61e+01 .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An execution instance of a workflow
allOf:
- $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/ProcessRun/schema.yaml
- type: object
  properties:
    describedByWorkflow:
      type: string
      format: uri
      description: Links to the workflow description (wfdesc:Workflow) that was executed
      x-jsonld-id: http://purl.org/wf4ever/wfprov#describedByWorkflow
      x-jsonld-type: '@id'
    hadSubProcessRun:
      type: array
      items:
        type: object
        properties:
          id:
            type: string
            format: uri
        required:
        - id
      description: The process runs that were part of this workflow execution
      x-jsonld-reverse: wfprov:wasPartOfWorkflowRun
      x-jsonld-type: '@id'
      x-jsonld-container: '@set'
    wasEnactedBy:
      type: string
      format: uri
      description: The workflow engine that executed this workflow
      x-jsonld-id: http://www.w3.org/ns/prov#wasAssociatedWith
      x-jsonld-type: '@id'
x-jsonld-extra-terms:
  WorkflowRun: http://purl.org/wf4ever/wfprov#WorkflowRun
x-jsonld-vocab: http://purl.org/wf4ever/wfprov#
x-jsonld-prefixes:
  wfprov: http://purl.org/wf4ever/wfprov#
  prov: http://www.w3.org/ns/prov#
  wfdesc: http://purl.org/wf4ever/wfdesc#

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/wfprov#",
    "wasInfluencedBy": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasInfluencedBy",
      "@type": "@id"
    },
    "qualifiedInfluence": {
      "@context": {
        "influencer": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:influencer",
          "@type": "@id"
        },
        "entity": {
          "@context": {
            "wasAttributedTo": {
              "@context": {
                "href": {
                  "@type": "@id",
                  "@id": "oa:hasTarget"
                },
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              },
              "@id": "prov:wasAttributedTo",
              "@type": "@id"
            },
            "links": {
              "@context": {
                "href": {
                  "@type": "@id",
                  "@id": "oa:hasTarget"
                },
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              },
              "@id": "rdfs:seeAlso"
            },
            "actedOnBehalfOf": {
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id",
              "@context": {
                "href": {
                  "@type": "@id",
                  "@id": "oa:hasTarget"
                },
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              }
            }
          },
          "@id": "prov:entity",
          "@type": "@id"
        },
        "agent": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:agent",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedInfluence",
      "@type": "@id"
    },
    "id": "@id",
    "provType": "@type",
    "activityType": "@type",
    "endedAtTime": {
      "@id": "prov:endedAtTime",
      "@type": "xsd:dateTime"
    },
    "wasAssociatedWith": {
      "@context": {
        "href": {
          "@type": "@id",
          "@id": "oa:hasTarget"
        },
        "rel": {
          "@context": {
            "@base": "http://www.iana.org/assignments/relation/"
          },
          "@id": "http://www.iana.org/assignments/relation",
          "@type": "@id"
        },
        "type": "dct:type",
        "hreflang": "dct:language",
        "title": "rdfs:label",
        "length": "dct:extent"
      },
      "@id": "prov:wasAssociatedWith",
      "@type": "@id"
    },
    "wasInformedBy": {
      "@id": "prov:wasInformedBy",
      "@type": "@id"
    },
    "used": {
      "@context": {
        "wasAttributedTo": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:wasAttributedTo",
          "@type": "@id"
        },
        "links": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "rdfs:seeAlso"
        },
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id",
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          }
        }
      },
      "@id": "prov:used",
      "@type": "@id"
    },
    "wasStartedBy": {
      "@context": {
        "wasAttributedTo": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:wasAttributedTo",
          "@type": "@id"
        },
        "links": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "rdfs:seeAlso"
        },
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id",
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          }
        }
      },
      "@id": "prov:wasStartedBy",
      "@type": "@id"
    },
    "wasEndedBy": {
      "@context": {
        "wasAttributedTo": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:wasAttributedTo",
          "@type": "@id"
        },
        "links": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "rdfs:seeAlso"
        },
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id",
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          }
        }
      },
      "@id": "prov:wasEndedBy",
      "@type": "@id"
    },
    "invalidated": {
      "@context": {
        "wasAttributedTo": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:wasAttributedTo",
          "@type": "@id"
        },
        "links": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "rdfs:seeAlso"
        },
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id",
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          }
        }
      },
      "@id": "prov:invalidated",
      "@type": "@id"
    },
    "generated": {
      "@context": {
        "wasAttributedTo": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "prov:wasAttributedTo",
          "@type": "@id"
        },
        "links": {
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          },
          "@id": "rdfs:seeAlso"
        },
        "actedOnBehalfOf": {
          "@id": "prov:actedOnBehalfOf",
          "@type": "@id",
          "@context": {
            "href": {
              "@type": "@id",
              "@id": "oa:hasTarget"
            },
            "rel": {
              "@context": {
                "@base": "http://www.iana.org/assignments/relation/"
              },
              "@id": "http://www.iana.org/assignments/relation",
              "@type": "@id"
            },
            "type": "dct:type",
            "hreflang": "dct:language",
            "title": "rdfs:label",
            "length": "dct:extent"
          }
        }
      },
      "@id": "prov:generated",
      "@type": "@id"
    },
    "atLocation": {
      "@id": "prov:atLocation",
      "@type": "@id"
    },
    "qualifiedUsage": {
      "@id": "prov:qualifiedUsage",
      "@type": "@id"
    },
    "qualifiedCommunication": {
      "@id": "prov:qualifiedCommunication",
      "@type": "@id"
    },
    "qualifiedStart": {
      "@context": {
        "entity": {
          "@context": {
            "has_provenance": {
              "@context": {
                "actedOnBehalfOf": {
                  "@context": {
                    "href": {
                      "@type": "@id",
                      "@id": "oa:hasTarget"
                    },
                    "rel": {
                      "@context": {
                        "@base": "http://www.iana.org/assignments/relation/"
                      },
                      "@id": "http://www.iana.org/assignments/relation",
                      "@type": "@id"
                    },
                    "type": "dct:type",
                    "hreflang": "dct:language",
                    "title": "rdfs:label",
                    "length": "dct:extent"
                  },
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              },
              "@id": "dct:provenance",
              "@type": "@id"
            },
            "wasAttributedTo": {
              "@context": {
                "href": {
                  "@type": "@id",
                  "@id": "oa:hasTarget"
                },
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              },
              "@id": "prov:wasAttributedTo",
              "@type": "@id"
            },
            "links": {
              "@context": {
                "href": {
                  "@type": "@id",
                  "@id": "oa:hasTarget"
                },
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              },
              "@id": "rdfs:seeAlso"
            },
            "qualifiedAttribution": {
              "@context": {
                "agent": {
                  "@context": {
                    "actedOnBehalfOf": {
                      "@context": {
                        "href": {
                          "@type": "@id",
                          "@id": "oa:hasTarget"
                        },
                        "rel": {
                          "@context": {
                            "@base": "http://www.iana.org/assignments/relation/"
                          },
                          "@id": "http://www.iana.org/assignments/relation",
                          "@type": "@id"
                        },
                        "type": "dct:type",
                        "hreflang": "dct:language",
                        "title": "rdfs:label",
                        "length": "dct:extent"
                      },
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  },
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              },
              "@id": "prov:qualifiedAttribution",
              "@type": "@id"
            }
          },
          "@id": "prov:entity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedStart",
      "@type": "@id"
    },
    "qualifiedEnd": {
      "@context": {
        "entity": {
          "@context": {
            "has_provenance": {
              "@context": {
                "actedOnBehalfOf": {
                  "@context": {
                    "href": {
                      "@type": "@id",
                      "@id": "oa:hasTarget"
                    },
                    "rel": {
                      "@context": {
                        "@base": "http://www.iana.org/assignments/relation/"
                      },
                      "@id": "http://www.iana.org/assignments/relation",
                      "@type": "@id"
                    },
                    "type": "dct:type",
                    "hreflang": "dct:language",
                    "title": "rdfs:label",
                    "length": "dct:extent"
                  },
                  "@id": "prov:actedOnBehalfOf",
                  "@type": "@id"
                }
              },
              "@id": "dct:provenance",
              "@type": "@id"
            },
            "wasAttributedTo": {
              "@context": {
                "href": {
                  "@type": "@id",
                  "@id": "oa:hasTarget"
                },
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              },
              "@id": "prov:wasAttributedTo",
              "@type": "@id"
            },
            "links": {
              "@context": {
                "href": {
                  "@type": "@id",
                  "@id": "oa:hasTarget"
                },
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              },
              "@id": "rdfs:seeAlso"
            },
            "qualifiedAttribution": {
              "@context": {
                "agent": {
                  "@context": {
                    "actedOnBehalfOf": {
                      "@context": {
                        "href": {
                          "@type": "@id",
                          "@id": "oa:hasTarget"
                        },
                        "rel": {
                          "@context": {
                            "@base": "http://www.iana.org/assignments/relation/"
                          },
                          "@id": "http://www.iana.org/assignments/relation",
                          "@type": "@id"
                        },
                        "type": "dct:type",
                        "hreflang": "dct:language",
                        "title": "rdfs:label",
                        "length": "dct:extent"
                      },
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  },
                  "@id": "prov:agent",
                  "@type": "@id"
                }
              },
              "@id": "prov:qualifiedAttribution",
              "@type": "@id"
            }
          },
          "@id": "prov:entity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedEnd",
      "@type": "@id"
    },
    "qualifiedAssociation": {
      "@context": {
        "agent": {
          "@context": {
            "actedOnBehalfOf": {
              "@context": {
                "href": {
                  "@type": "@id",
                  "@id": "oa:hasTarget"
                },
                "rel": {
                  "@context": {
                    "@base": "http://www.iana.org/assignments/relation/"
                  },
                  "@id": "http://www.iana.org/assignments/relation",
                  "@type": "@id"
                },
                "type": "dct:type",
                "hreflang": "dct:language",
                "title": "rdfs:label",
                "length": "dct:extent"
              },
              "@id": "prov:actedOnBehalfOf",
              "@type": "@id"
            }
          },
          "@id": "prov:agent",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedAssociation",
      "@type": "@id"
    },
    "agentType": "@type",
    "entityType": "@type",
    "featureType": "@type",
    "Activity": "prov:Activity",
    "ActivityInfluence": "prov:ActivityInfluence",
    "Agent": "prov:Agent",
    "AgentInfluence": "prov:AgentInfluence",
    "Association": "prov:Association",
    "Attribution": "prov:Attribution",
    "Bundle": "prov:Bundle",
    "Collection": "prov:Collection",
    "Communication": "prov:Communication",
    "Delegation": "prov:Delegation",
    "Derivation": "prov:Derivation",
    "EmptyCollection": "prov:EmptyCollection",
    "End": "prov:End",
    "Entity": "prov:Entity",
    "EntityInfluence": "prov:EntityInfluence",
    "Generation": "prov:Generation",
    "Influence": "prov:Influence",
    "InstantaneousEvent": "prov:InstantaneousEvent",
    "Invalidation": "prov:Invalidation",
    "Location": "prov:Location",
    "Organization": "prov:Organization",
    "Person": "prov:Person",
    "Plan": "prov:Plan",
    "PrimarySource": "prov:PrimarySource",
    "Quotation": "prov:Quotation",
    "Revision": "prov:Revision",
    "Role": "prov:Role",
    "SoftwareAgent": "prov:SoftwareAgent",
    "Start": "prov:Start",
    "Usage": "prov:Usage",
    "ServiceDescription": "prov:ServiceDescription",
    "DirectQueryService": "prov:DirectQueryService",
    "Accept": "prov:Accept",
    "Contribute": "prov:Contribute",
    "Contributor": "prov:Contributor",
    "Copyright": "prov:Copyright",
    "Create": "prov:Create",
    "Creator": "prov:Creator",
    "Modify": "prov:Modify",
    "Publish": "prov:Publish",
    "Publisher": "prov:Publisher",
    "Replace": "prov:Replace",
    "RightsAssignment": "prov:RightsAssignment",
    "RightsHolder": "prov:RightsHolder",
    "Submit": "prov:Submit",
    "Dictionary": "prov:Dictionary",
    "EmptyDictionary": "prov:EmptyDictionary",
    "KeyEntityPair": "prov:KeyEntityPair",
    "Insertion": "prov:Insertion",
    "Removal": "prov:Removal",
    "atTime": {
      "@id": "prov:atTime",
      "@type": "xsd:dateTime"
    },
    "generatedAtTime": {
      "@id": "prov:generatedAtTime",
      "@type": "xsd:dateTime"
    },
    "invalidatedAtTime": {
      "@id": "prov:invalidatedAtTime",
      "@type": "xsd:dateTime"
    },
    "startedAtTime": {
      "@id": "prov:startedAtTime",
      "@type": "xsd:dateTime"
    },
    "value": "prov:value",
    "provenanceUriTemplate": "prov:provenanceUriTemplate",
    "pairKey": {
      "@id": "prov:pairKey",
      "@type": "rdfs:Literal"
    },
    "removedKey": {
      "@id": "prov:removedKey",
      "@type": "rdfs:Literal"
    },
    "actedOnBehalfOf": {
      "@id": "prov:actedOnBehalfOf",
      "@type": "@id"
    },
    "agent": {
      "@id": "prov:agent",
      "@type": "@id"
    },
    "alternateOf": {
      "@id": "prov:alternateOf",
      "@type": "@id"
    },
    "entity": {
      "@id": "prov:entity",
      "@type": "@id"
    },
    "hadActivity": {
      "@id": "prov:hadActivity",
      "@type": "@id"
    },
    "activity": {
      "@id": "prov:activity",
      "@type": "@id"
    },
    "hadGeneration": {
      "@id": "prov:hadGeneration",
      "@type": "@id"
    },
    "hadMember": {
      "@id": "prov:hadMember",
      "@type": "@id"
    },
    "hadPlan": {
      "@id": "prov:hadPlan",
      "@type": "@id"
    },
    "hadPrimarySource": {
      "@id": "prov:hadPrimarySource",
      "@type": "@id"
    },
    "hadRole": {
      "@id": "prov:hadRole",
      "@type": "@id"
    },
    "hadUsage": {
      "@id": "prov:hadUsage",
      "@type": "@id"
    },
    "influenced": {
      "@id": "prov:influenced",
      "@type": "@id"
    },
    "influencer": {
      "@id": "prov:influencer",
      "@type": "@id"
    },
    "qualifiedAttribution": {
      "@id": "prov:qualifiedAttribution",
      "@type": "@id"
    },
    "qualifiedDelegation": {
      "@id": "prov:qualifiedDelegation",
      "@type": "@id"
    },
    "qualifiedDerivation": {
      "@id": "prov:qualifiedDerivation",
      "@type": "@id"
    },
    "qualifiedGeneration": {
      "@id": "prov:qualifiedGeneration",
      "@type": "@id"
    },
    "qualifiedInvalidation": {
      "@id": "prov:qualifiedInvalidation",
      "@type": "@id"
    },
    "qualifiedPrimarySource": {
      "@id": "prov:qualifiedPrimarySource",
      "@type": "@id"
    },
    "qualifiedQuotation": {
      "@id": "prov:qualifiedQuotation",
      "@type": "@id"
    },
    "qualifiedRevision": {
      "@id": "prov:qualifiedRevision",
      "@type": "@id"
    },
    "specializationOf": {
      "@id": "prov:specializationOf",
      "@type": "@id"
    },
    "wasAttributedTo": {
      "@id": "prov:wasAttributedTo",
      "@type": "@id"
    },
    "wasDerivedFrom": {
      "@id": "prov:wasDerivedFrom",
      "@type": "@id"
    },
    "wasGeneratedBy": {
      "@id": "prov:wasGeneratedBy",
      "@type": "@id"
    },
    "wasInvalidatedBy": {
      "@id": "prov:wasInvalidatedBy",
      "@type": "@id"
    },
    "wasQuotedFrom": {
      "@id": "prov:wasQuotedFrom",
      "@type": "@id"
    },
    "wasRevisionOf": {
      "@id": "prov:wasRevisionOf",
      "@type": "@id"
    },
    "has_anchor": {
      "@id": "prov:has_anchor",
      "@type": "@id"
    },
    "has_provenance": {
      "@id": "dct:provenance",
      "@type": "@id"
    },
    "has_query_service": {
      "@id": "prov:has_query_service",
      "@type": "@id"
    },
    "describesService": {
      "@id": "prov:describesService",
      "@type": "@id"
    },
    "pingback": {
      "@id": "prov:pingback",
      "@type": "@id"
    },
    "dictionary": {
      "@id": "prov:dictionary",
      "@type": "@id"
    },
    "derivedByInsertionFrom": {
      "@id": "prov:derivedByInsertionFrom",
      "@type": "@id"
    },
    "derivedByRemovalFrom": {
      "@id": "prov:derivedByRemovalFrom",
      "@type": "@id"
    },
    "insertedKeyEntityPair": {
      "@id": "prov:insertedKeyEntityPair",
      "@type": "@id"
    },
    "hadDictionaryMember": {
      "@id": "prov:hadDictionaryMember",
      "@type": "@id"
    },
    "pairEntity": {
      "@id": "prov:pairEntity",
      "@type": "@id"
    },
    "qualifiedInsertion": {
      "@id": "prov:qualifiedInsertion",
      "@type": "@id"
    },
    "qualifiedRemoval": {
      "@id": "prov:qualifiedRemoval",
      "@type": "@id"
    },
    "asInBundle": {
      "@id": "prov:asInBundle",
      "@type": "@id"
    },
    "mentionOf": {
      "@id": "prov:mentionOf",
      "@type": "@id"
    },
    "name": "rdfs:label",
    "links": "rdfs:seeAlso",
    "ProcessRun": "wfprov:ProcessRun",
    "WorkflowRun": "wfprov:WorkflowRun",
    "wasOutputFrom": {
      "@id": "prov:generated",
      "@type": "@id",
      "@container": "@set"
    },
    "type": "@type",
    "describedByProcess": {
      "@id": "wfprov:describedByProcess",
      "@type": "@id"
    },
    "usedInput": {
      "@id": "wfprov:usedInput",
      "@type": "@id",
      "@container": "@set"
    },
    "wasPartOfWorkflowRun": {
      "@id": "wfprov:wasPartOfWorkflowRun",
      "@type": "@id"
    },
    "wasEnactedBy": {
      "@id": "prov:wasAssociatedWith",
      "@type": "@id"
    },
    "describedByWorkflow": {
      "@id": "wfprov:describedByWorkflow",
      "@type": "@id"
    },
    "hadSubProcessRun": {
      "@reverse": "wfprov:wasPartOfWorkflowRun",
      "@type": "@id",
      "@container": "@set"
    },
    "prov": "http://www.w3.org/ns/prov#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "dct": "http://purl.org/dc/terms/",
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "oa": "http://www.w3.org/ns/oa#",
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/context.jsonld)

## Sources

* [Workflow Provenance Ontology - WorkflowRun](http://purl.org/wf4ever/wfprov#WorkflowRun)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/wfprov/WorkflowRun`

