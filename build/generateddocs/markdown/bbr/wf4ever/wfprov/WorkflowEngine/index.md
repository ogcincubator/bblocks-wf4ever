
# wfprov:WorkflowEngine (Datatype)

`ogc.bbr.wf4ever.wfprov.WorkflowEngine` *v1.0*

A software agent that executes workflows. The WorkflowEngine is responsible for enacting workflow and process executions, managing the execution environment and resources.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wfprov:WorkflowEngine

## Description

A **WorkflowEngine** represents a software agent that executes workflows. The workflow engine is responsible for enacting workflow and process executions, managing the execution environment and resources.

## Relations

- Process runs and workflow runs reference the engine via `wfprov:wasEnactedBy`
- This is the inverse relationship: the engine enacts the executions

## Examples of engines

- ZOO-Project WPS
- Apache Airflow
- Nextflow
- Snakemake
- CWL Runner

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A software agent that executes workflows
allOf:
- $ref: https://ogcincubator.github.io/bblock-prov-schema/build/annotated/ogc-utils/prov/schema.yaml#/$defs/Agent
type: object
properties:
  '@id':
    type: string
    format: uri
    description: Unique identifier for the workflow engine
  '@type':
    const: WorkflowEngine
    description: Type must be WorkflowEngine
  name:
    type: string
    description: Name of the workflow engine
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  version:
    type: string
    description: Version of the workflow engine
    x-jsonld-id: http://schema.org/version
  description:
    type: string
    description: Description of the workflow engine
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#comment
required:
- '@id'
- '@type'
x-jsonld-extra-terms:
  WorkflowEngine: http://purl.org/wf4ever/wfprov#WorkflowEngine
x-jsonld-vocab: http://purl.org/wf4ever/wfprov#
x-jsonld-prefixes:
  wfprov: http://purl.org/wf4ever/wfprov#
  rdfs: http://www.w3.org/2000/01/rdf-schema#
  prov: http://www.w3.org/ns/prov#

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/schema.yaml)


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
            }
          },
          "@id": "prov:entity",
          "@type": "@id"
        },
        "activity": {
          "@context": {
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
                }
              },
              "@id": "prov:generated",
              "@type": "@id"
            }
          },
          "@id": "prov:activity",
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
    "agentType": "@type",
    "provType": "@type",
    "name": "rdfs:label",
    "id": "@id",
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
    },
    "atLocation": {
      "@id": "prov:atLocation",
      "@type": "@id"
    },
    "qualifiedDelegation": {
      "@context": {
        "hadActivity": {
          "@context": {
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
                }
              },
              "@id": "prov:generated",
              "@type": "@id"
            },
            "qualifiedStart": {
              "@context": {
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
                    }
                  },
                  "@id": "prov:entity",
                  "@type": "@id"
                }
              },
              "@id": "prov:qualifiedEnd",
              "@type": "@id"
            }
          },
          "@id": "prov:hadActivity",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedDelegation",
      "@type": "@id"
    },
    "activityType": "@type",
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
    "endedAtTime": {
      "@id": "prov:endedAtTime",
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
    "generated": {
      "@id": "prov:generated",
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
    "invalidated": {
      "@id": "prov:invalidated",
      "@type": "@id"
    },
    "qualifiedAssociation": {
      "@id": "prov:qualifiedAssociation",
      "@type": "@id"
    },
    "qualifiedAttribution": {
      "@id": "prov:qualifiedAttribution",
      "@type": "@id"
    },
    "qualifiedCommunication": {
      "@id": "prov:qualifiedCommunication",
      "@type": "@id"
    },
    "qualifiedDerivation": {
      "@id": "prov:qualifiedDerivation",
      "@type": "@id"
    },
    "qualifiedEnd": {
      "@id": "prov:qualifiedEnd",
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
    "qualifiedStart": {
      "@id": "prov:qualifiedStart",
      "@type": "@id"
    },
    "qualifiedUsage": {
      "@id": "prov:qualifiedUsage",
      "@type": "@id"
    },
    "specializationOf": {
      "@id": "prov:specializationOf",
      "@type": "@id"
    },
    "used": {
      "@id": "prov:used",
      "@type": "@id"
    },
    "wasAssociatedWith": {
      "@id": "prov:wasAssociatedWith",
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
    "wasEndedBy": {
      "@id": "prov:wasEndedBy",
      "@type": "@id"
    },
    "wasGeneratedBy": {
      "@id": "prov:wasGeneratedBy",
      "@type": "@id"
    },
    "wasInformedBy": {
      "@id": "prov:wasInformedBy",
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
    "wasStartedBy": {
      "@id": "prov:wasStartedBy",
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
    "links": "rdfs:seeAlso",
    "WorkflowEngine": "wfprov:WorkflowEngine",
    "version": "http://schema.org/version",
    "description": "rdfs:comment",
    "prov": "http://www.w3.org/ns/prov#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "dct": "http://purl.org/dc/terms/",
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "oa": "http://www.w3.org/ns/oa#",
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowEngine/context.jsonld)

## Sources

* [Workflow Provenance Ontology - WorkflowEngine](http://purl.org/wf4ever/wfprov#WorkflowEngine)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/wfprov/WorkflowEngine`

