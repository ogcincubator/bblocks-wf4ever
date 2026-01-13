
# Complete Workflow Provenance Trace (Schema)

`ogc.bbr.wf4ever.wf4ever-profiles.complete-provenance-trace` *v0.1*

Master profile combining Research Object, Workflow Description, and Workflow Execution Provenance

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# Complete Workflow Provenance Trace

## Overview

This master profile demonstrates the full integration of the Wf4Ever ontology suite, combining:

1. **Research Object (RO)**: Container and packaging
2. **Workflow Description (WFDESC)**: Prospective provenance
3. **Workflow Execution (WFPROV)**: Retrospective provenance

## Purpose

This building block serves as:

- **Integration test**: Validates that all Wf4Ever components work together
- **Documentation**: Shows how to combine all pieces
- **Example**: Real CWLProv data from scientific workflow
- **Validation**: End-to-end test of RDF graph generation

## Structure

A complete provenance trace contains four main components:

### 1. Research Object

The container that aggregates all resources:

```json
{
  "researchObject": {
    "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/",
    "type": "ResearchObject",
    "aggregates": [...],
    "annotations": [...]
  }
}
```

**Key properties:**
- `aggregates`: All files, data, workflows included
- `annotations`: Metadata about aggregated resources
- `manifest`: Points to the RO manifest
- `conformsTo`: CWLProv version

### 2. Workflow Description

The workflow structure (prospective provenance):

```json
{
  "workflow": {
    "id": "arcp://uuid,.../workflow/packed.cwl#main",
    "type": "Workflow",
    "hasInput": [...],
    "hasOutput": [...]
  }
}
```

**Key properties:**
- `hasInput`: Input parameters of the workflow
- `hasOutput`: Output parameters of the workflow
- `hasSubWorkflow`: Nested workflows (if any)

### 3. Workflow Execution

The execution trace (retrospective provenance):

```json
{
  "workflowRun": {
    "id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
    "type": "WorkflowRun",
    "describedByWorkflow": "arcp://uuid,.../workflow/packed.cwl#main",
    "used": [...],
    "generated": [...],
    "wasAssociatedWith": [...]
  }
}
```

**Key properties:**
- `describedByWorkflow`: Links to workflow definition
- `used`: Input artifacts consumed
- `generated`: Output artifacts produced
- `wasAssociatedWith`: Agents/engines that executed
- `startedAtTime` / `endedAtTime`: Execution timeline

### 4. Manifest

The RO manifest describing the bundle:

```json
{
  "manifest": {
    "id": "arcp://uuid,.../metadata/manifest.json",
    "type": "Manifest",
    "authoredBy": {...},
    "describes": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/"
  }
}
```

## Relationships

The complete trace shows these key relationships:

```
Research Object
    ├─ ore:aggregates → Workflow (WFDESC)
    ├─ ore:aggregates → WorkflowRun Provenance (WFPROV)
    ├─ ore:aggregates → Input Data
    ├─ ore:aggregates → Output Data
    └─ ore:isDescribedBy → Manifest

Workflow (WFDESC)
    ├─ wfdesc:hasInput → Input Parameters
    └─ wfdesc:hasOutput → Output Parameters

WorkflowRun (WFPROV)
    ├─ wfprov:describedByWorkflow → Workflow
    ├─ prov:used → Input Artifacts
    ├─ prov:generated → Output Artifacts
    ├─ prov:wasAssociatedWith → Agents
    ├─ prov:startedAtTime → Start Time
    └─ prov:endedAtTime → End Time
```

## PROV-O Mapping

This complete trace maps to PROV-O as follows:

- **Research Object** → `prov:Collection` (specialized as `prov:Bundle`)
- **Workflow** → Description (no direct PROV equivalent, stays in WFDESC)
- **WorkflowRun** → `prov:Activity`
- **Input/Output Artifacts** → `prov:Entity`
- **Workflow Engine** → `prov:Agent` (specialized as `prov:SoftwareAgent`)

## Use Cases

### 1. Scientific Workflow Archival

Package a complete workflow execution for long-term preservation:

- Workflow definition (how to reproduce)
- Execution trace (what actually happened)
- Input data (what was used)
- Output data (what was generated)
- Software environment (how it was run)

### 2. Reproducibility

Enable others to:

1. Understand the workflow structure
2. See the actual execution parameters
3. Trace data lineage
4. Reproduce the results

### 3. FAIR Data Compliance

Meet FAIR principles:

- **Findable**: Unique identifiers for all components
- **Accessible**: Standard formats (JSON-LD, RDF)
- **Interoperable**: Standard ontologies (PROV-O, DCAT)
- **Reusable**: Complete provenance metadata

### 4. Workflow Comparison

Compare different executions:

- Same workflow, different parameters
- Same workflow, different data
- Different versions of workflow
- Performance analysis

## Example: Mangrove Mapping Workflow

The included example shows a real scientific workflow for mangrove mapping using Sentinel-2 satellite imagery.

**Workflow inputs:**
- `cloud_cover_max`: 20% (maximum acceptable cloud coverage)
- `days_back`: 90 (days of historical data)
- `east`: 95.35° (longitude)
- `north`: 16.1° (latitude)

**Execution:**
- Started: 2025-11-03T15:14:02
- Ended: 2025-11-03T15:14:17
- Duration: ~15 seconds
- Engine: cwltool 3.1.20251031082601

**Outputs:**
- Mangrove classification results
- Aggregated in Research Object

## Validation

This building block enables validation at multiple levels:

1. **JSON Schema**: Structure validation
2. **JSON-LD**: RDF graph generation
3. **SHACL**: Semantic constraints (future)
4. **PROV Constraints**: PROV-O model compliance (future)

## Next Steps

To complete the master profile validation:

1. ✅ Create complete trace schema
2. ✅ Create real example
3. ⏳ Add SHACL shapes for validation
4. ⏳ Create SPARQL queries for analysis
5. ⏳ Generate transformations to other formats

## See Also

- [Research Object](../ro/ResearchObject/description.md)
- [Workflow](../wfdesc/Workflow/description.md)
- [WorkflowRun](../wfprov/WorkflowRun/description.md)
- [CWLProv Specification](https://w3id.org/cwl/prov)

## Examples

### Complete Mangrove Workflow Provenance Trace
#### json
```json
{
  "researchObject": {
    "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/",
    "type": "ResearchObject",
    "conformsTo": "https://w3id.org/cwl/prov/0.6.0",
    "manifest": "metadata/manifest.json",
    "createdOn": "2025-11-03T15:14:17.166945",
    "createdBy": {
      "uri": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "name": "cwltool 3.1.20251031082601"
    },
    "aggregates": [
      {
        "id": "urn:hash::sha1:e71003c6b7dd4093ce139ac0c51a6ba38d54a439",
        "bundledAs": {
          "uri": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/data/e7/e71003c6b7dd4093ce139ac0c51a6ba38d54a439",
          "folder": "/data/e7/",
          "filename": "e71003c6b7dd4093ce139ac0c51a6ba38d54a439"
        },
        "mediatype": "text/plain; charset='UTF-8'"
      },
      {
        "id": "metadata/provenance/primary.cwlprov.jsonld",
        "mediatype": "application/ld+json",
        "conformsTo": [
          "http://www.w3.org/TR/2013/REC-prov-o-20130430/",
          "https://w3id.org/cwl/prov/0.6.0"
        ],
        "createdOn": "2025-11-03T15:14:17.167324",
        "createdBy": {
          "uri": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
          "name": "cwltool 3.1.20251031082601"
        }
      },
      {
        "id": "workflow/packed.cwl",
        "mediatype": "text/x+yaml; charset=\"UTF-8\"",
        "conformsTo": "https://w3id.org/cwl/",
        "createdOn": "2025-11-03T15:14:17.167396",
        "createdBy": {
          "uri": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
          "name": "cwltool 3.1.20251031082601"
        }
      }
    ],
    "annotations": [
      {
        "id": "urn:uuid:55443a59-6a39-4b4c-89de-871dbceb5b84",
        "about": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
        "content": [
          "provenance/primary.cwlprov.nt",
          "provenance/primary.cwlprov.json",
          "provenance/primary.cwlprov.jsonld"
        ]
      },
      {
        "id": "urn:uuid:5ac7d6f3-79c4-4b27-988f-56232cbb9999",
        "about": "workflow/packed.cwl",
        "content": null
      }
    ]
  },
  "workflow": {
    "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main",
    "type": "Workflow",
    "label": "Mangrove Mapping Workflow",
    "hasInput": [
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/cloud_cover_max",
        "type": "Input",
        "label": "cloud_cover_max",
        "description": "Maximum cloud coverage percentage"
      },
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/days_back",
        "type": "Input",
        "label": "days_back",
        "description": "Number of days to look back for imagery"
      },
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/east",
        "type": "Input",
        "label": "east",
        "description": "Eastern boundary longitude"
      },
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/north",
        "type": "Input",
        "label": "north",
        "description": "Northern boundary latitude"
      }
    ],
    "hasOutput": [
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/outputs",
        "type": "Output",
        "label": "outputs",
        "description": "Processed mangrove mapping results"
      }
    ]
  },
  "workflowRun": {
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
  },
  "manifest": {
    "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/manifest.json",
    "type": "Manifest",
    "conformsTo": "https://w3id.org/bundle/2014-11-05/",
    "authoredBy": {
      "id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "name": "cwltool 3.1.20251031082601"
    },
    "authoredOn": "2025-11-03T15:14:17.166945",
    "retrievedFrom": "https://w3id.org/cwl/prov/0.6.0",
    "describes": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/"
  },
  "metadata": {
    "created": "2025-11-03T15:14:17Z",
    "creator": "cwltool 3.1.20251031082601",
    "description": "Complete provenance trace for mangrove mapping workflow execution using CWL and Sentinel-2 imagery",
    "keywords": [
      "mangrove",
      "remote-sensing",
      "sentinel-2",
      "cwl",
      "provenance",
      "workflow"
    ]
  }
}

```

#### jsonld
```jsonld
{
  "@context": "https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever-profiles/complete-provenance-trace/context.jsonld",
  "researchObject": {
    "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/",
    "type": "ResearchObject",
    "conformsTo": "https://w3id.org/cwl/prov/0.6.0",
    "manifest": "metadata/manifest.json",
    "createdOn": "2025-11-03T15:14:17.166945",
    "createdBy": {
      "uri": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "name": "cwltool 3.1.20251031082601"
    },
    "aggregates": [
      {
        "id": "urn:hash::sha1:e71003c6b7dd4093ce139ac0c51a6ba38d54a439",
        "bundledAs": {
          "uri": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/data/e7/e71003c6b7dd4093ce139ac0c51a6ba38d54a439",
          "folder": "/data/e7/",
          "filename": "e71003c6b7dd4093ce139ac0c51a6ba38d54a439"
        },
        "mediatype": "text/plain; charset='UTF-8'"
      },
      {
        "id": "metadata/provenance/primary.cwlprov.jsonld",
        "mediatype": "application/ld+json",
        "conformsTo": [
          "http://www.w3.org/TR/2013/REC-prov-o-20130430/",
          "https://w3id.org/cwl/prov/0.6.0"
        ],
        "createdOn": "2025-11-03T15:14:17.167324",
        "createdBy": {
          "uri": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
          "name": "cwltool 3.1.20251031082601"
        }
      },
      {
        "id": "workflow/packed.cwl",
        "mediatype": "text/x+yaml; charset=\"UTF-8\"",
        "conformsTo": "https://w3id.org/cwl/",
        "createdOn": "2025-11-03T15:14:17.167396",
        "createdBy": {
          "uri": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
          "name": "cwltool 3.1.20251031082601"
        }
      }
    ],
    "annotations": [
      {
        "id": "urn:uuid:55443a59-6a39-4b4c-89de-871dbceb5b84",
        "about": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
        "content": [
          "provenance/primary.cwlprov.nt",
          "provenance/primary.cwlprov.json",
          "provenance/primary.cwlprov.jsonld"
        ]
      },
      {
        "id": "urn:uuid:5ac7d6f3-79c4-4b27-988f-56232cbb9999",
        "about": "workflow/packed.cwl",
        "content": null
      }
    ]
  },
  "workflow": {
    "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main",
    "type": "Workflow",
    "label": "Mangrove Mapping Workflow",
    "hasInput": [
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/cloud_cover_max",
        "type": "Input",
        "label": "cloud_cover_max",
        "description": "Maximum cloud coverage percentage"
      },
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/days_back",
        "type": "Input",
        "label": "days_back",
        "description": "Number of days to look back for imagery"
      },
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/east",
        "type": "Input",
        "label": "east",
        "description": "Eastern boundary longitude"
      },
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/north",
        "type": "Input",
        "label": "north",
        "description": "Northern boundary latitude"
      }
    ],
    "hasOutput": [
      {
        "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/outputs",
        "type": "Output",
        "label": "outputs",
        "description": "Processed mangrove mapping results"
      }
    ]
  },
  "workflowRun": {
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
  },
  "manifest": {
    "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/manifest.json",
    "type": "Manifest",
    "conformsTo": "https://w3id.org/bundle/2014-11-05/",
    "authoredBy": {
      "id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60",
      "name": "cwltool 3.1.20251031082601"
    },
    "authoredOn": "2025-11-03T15:14:17.166945",
    "retrievedFrom": "https://w3id.org/cwl/prov/0.6.0",
    "describes": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/"
  },
  "metadata": {
    "created": "2025-11-03T15:14:17Z",
    "creator": "cwltool 3.1.20251031082601",
    "description": "Complete provenance trace for mangrove mapping workflow execution using CWL and Sentinel-2 imagery",
    "keywords": [
      "mangrove",
      "remote-sensing",
      "sentinel-2",
      "cwl",
      "provenance",
      "workflow"
    ]
  }
}
```

#### ttl
```ttl
@prefix : <http://purl.org/wf4ever/> .
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix ns1: <http://purl.org/wf4ever/profiles#> .
@prefix ore: <http://www.openarchives.org/ore/terms/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix ro: <http://purl.org/wf4ever/ro#> .
@prefix wfdesc: <http://purl.org/wf4ever/wfdesc#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/manifest.json> ro:authoredBy <urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> ;
    ro:authoredOn "2025-11-03T15:14:17.166945" ;
    ro:conformsTo "https://w3id.org/bundle/2014-11-05/" ;
    ro:retrievedFrom "https://w3id.org/cwl/prov/0.6.0" ;
    ro:type "Manifest" ;
    ore:describes <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/> .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/cloud_cover_max> :label "cloud_cover_max" ;
    :type "Input" ;
    rdfs:comment "Maximum cloud coverage percentage" .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/days_back> :label "days_back" ;
    :type "Input" ;
    rdfs:comment "Number of days to look back for imagery" .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/east> :label "east" ;
    :type "Input" ;
    rdfs:comment "Eastern boundary longitude" .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/north> :label "north" ;
    :type "Input" ;
    rdfs:comment "Northern boundary latitude" .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/outputs> :label "outputs" ;
    :type "Output" ;
    rdfs:comment "Processed mangrove mapping results" .

<file:///github/workspace/metadata/provenance/primary.cwlprov.jsonld> ro:conformsTo "http://www.w3.org/TR/2013/REC-prov-o-20130430/",
        "https://w3id.org/cwl/prov/0.6.0" ;
    ro:createdBy [ rdfs:label "cwltool 3.1.20251031082601" ;
            ro:uri "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60" ] ;
    ro:createdOn "2025-11-03T15:14:17.167324" ;
    ro:mediatype "application/ld+json" .

<file:///github/workspace/workflow/packed.cwl> ro:conformsTo "https://w3id.org/cwl/" ;
    ro:createdBy [ rdfs:label "cwltool 3.1.20251031082601" ;
            ro:uri "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60" ] ;
    ro:createdOn "2025-11-03T15:14:17.167396" ;
    ro:mediatype "text/x+yaml; charset=\"UTF-8\"" .

<urn:hash::sha1:e71003c6b7dd4093ce139ac0c51a6ba38d54a439> ro:bundledAs [ ro:filename "e71003c6b7dd4093ce139ac0c51a6ba38d54a439" ;
            ro:folder "/data/e7/" ;
            ro:uri "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/data/e7/e71003c6b7dd4093ce139ac0c51a6ba38d54a439" ] ;
    ro:mediatype "text/plain; charset='UTF-8'" .

<urn:uuid:192e18cb-9182-4147-ad13-03076e7a3b3d> prov:hadRole <file:///github/workspace/cloud_cover_max> ;
    prov:value 2e+01 .

<urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f> dct:type "Agent" ;
    wfprov:label "Container execution of image r2d-2ftmp-2frepo2cwl-5fzbz5cbsp-2frepo1762182696" .

<urn:uuid:55443a59-6a39-4b4c-89de-871dbceb5b84> ro:about "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c" ;
    ro:content "provenance/primary.cwlprov.json",
        "provenance/primary.cwlprov.jsonld",
        "provenance/primary.cwlprov.nt" .

<urn:uuid:5ac7d6f3-79c4-4b27-988f-56232cbb9999> ro:about "workflow/packed.cwl" .

<urn:uuid:83c8708e-ccbd-494e-b939-1298b65b1539> a wfprov:Artifact ;
    wfprov:basename "outputs" .

<urn:uuid:91b4ec49-d11a-4407-9685-032bf7e95258> prov:hadRole <file:///github/workspace/days_back> ;
    prov:value 90 .

<urn:uuid:ced76ef7-e660-4798-9442-06c17a45bbea> prov:hadRole <file:///github/workspace/east> ;
    prov:value 9.535e+01 .

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

<urn:uuid:fd57ac88-8716-40ed-8945-f83914857523> prov:hadRole <file:///github/workspace/north> ;
    prov:value 1.61e+01 .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/> ro:annotations <urn:uuid:55443a59-6a39-4b4c-89de-871dbceb5b84>,
        <urn:uuid:5ac7d6f3-79c4-4b27-988f-56232cbb9999> ;
    ro:conformsTo "https://w3id.org/cwl/prov/0.6.0" ;
    ro:createdBy [ rdfs:label "cwltool 3.1.20251031082601" ;
            ro:uri "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60" ] ;
    ro:createdOn "2025-11-03T15:14:17.166945" ;
    ro:manifest <file:///github/workspace/metadata/manifest.json> ;
    ro:type "ResearchObject" ;
    ore:aggregates <file:///github/workspace/metadata/provenance/primary.cwlprov.jsonld>,
        <file:///github/workspace/workflow/packed.cwl>,
        <urn:hash::sha1:e71003c6b7dd4093ce139ac0c51a6ba38d54a439> .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main> :label "Mangrove Mapping Workflow" ;
    :type "Workflow" ;
    wfdesc:hasInput <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/cloud_cover_max>,
        <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/days_back>,
        <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/east>,
        <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/north> ;
    wfdesc:hasOutput <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main/outputs> .

<urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> rdfs:label "cwltool 3.1.20251031082601" ;
    dct:type "WorkflowEngine" ;
    wfprov:label "cwltool 3.1.20251031082601" .

[] ns1:metadata [ dct:created "2025-11-03T15:14:17+00:00"^^xsd:dateTime ;
            dct:creator <file:///github/workspace/> ;
            dct:description "Complete provenance trace for mangrove mapping workflow execution using CWL and Sentinel-2 imagery" ;
            dcat:keyword "cwl",
                "mangrove",
                "provenance",
                "remote-sensing",
                "sentinel-2",
                "workflow" ] ;
    ro:Manifest <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/manifest.json> ;
    ro:ResearchObject <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/> ;
    wfdesc:Workflow <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main> ;
    wfprov:WorkflowRun <urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c> .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: Complete workflow provenance trace combining Research Object, Workflow
  Description, and Execution Provenance
type: object
properties:
  researchObject:
    description: The Research Object container aggregating all workflow resources
    allOf:
    - $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/ResearchObject/schema.yaml
    x-jsonld-id: http://purl.org/wf4ever/ro#ResearchObject
    x-jsonld-type: '@id'
  workflow:
    description: The workflow description (prospective provenance)
    allOf:
    - $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/Workflow/schema.yaml
    x-jsonld-id: http://purl.org/wf4ever/wfdesc#Workflow
    x-jsonld-type: '@id'
  workflowRun:
    description: The workflow execution trace (retrospective provenance)
    allOf:
    - $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/schema.yaml
    x-jsonld-id: http://purl.org/wf4ever/wfprov#WorkflowRun
    x-jsonld-type: '@id'
  manifest:
    description: The RO manifest describing the research object
    allOf:
    - $ref: https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Manifest/schema.yaml
    x-jsonld-id: http://purl.org/wf4ever/ro#Manifest
    x-jsonld-type: '@id'
  metadata:
    type: object
    description: Additional metadata about the complete trace
    properties:
      created:
        type: string
        format: date-time
        description: When this trace was created
        x-jsonld-id: http://purl.org/dc/terms/created
        x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
      creator:
        type: string
        description: Who created this trace
        x-jsonld-id: http://purl.org/dc/terms/creator
        x-jsonld-type: '@id'
      description:
        type: string
        description: Human-readable description of this workflow execution
        x-jsonld-id: http://purl.org/dc/terms/description
      keywords:
        type: array
        items:
          type: string
        description: Keywords describing this workflow and execution
        x-jsonld-id: http://www.w3.org/ns/dcat#keyword
    x-jsonld-id: http://purl.org/wf4ever/profiles#metadata
required:
- researchObject
- workflow
- workflowRun
x-jsonld-extra-terms:
  CompleteProvenanceTrace: http://purl.org/wf4ever/profiles#CompleteProvenanceTrace
x-jsonld-vocab: http://purl.org/wf4ever/
x-jsonld-prefixes:
  wfdesc: http://purl.org/wf4ever/wfdesc#
  wfprov: http://purl.org/wf4ever/wfprov#
  ro: http://purl.org/wf4ever/ro#
  prov: http://www.w3.org/ns/prov#
  ore: http://www.openarchives.org/ore/terms/
  dcat: http://www.w3.org/ns/dcat#
  dcterms: http://purl.org/dc/terms/
  foaf: http://xmlns.com/foaf/0.1/
  rdfs: http://www.w3.org/2000/01/rdf-schema#

```

Links to the schema:

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever-profiles/complete-provenance-trace/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever-profiles/complete-provenance-trace/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/",
    "CompleteProvenanceTrace": "http://purl.org/wf4ever/profiles#CompleteProvenanceTrace",
    "researchObject": {
      "@context": {
        "@vocab": "http://purl.org/wf4ever/ro#",
        "title": "dcterms:title",
        "description": "dcterms:description",
        "aggregates": {
          "@id": "ore:aggregates",
          "@type": "@id",
          "@container": "@set"
        },
        "manifest": {
          "@id": "ro:manifest",
          "@type": "@id"
        },
        "created": {
          "@id": "dcterms:created",
          "@type": "xsd:dateTime"
        }
      },
      "@id": "ro:ResearchObject",
      "@type": "@id"
    },
    "workflow": {
      "@context": {
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
        }
      },
      "@id": "wfdesc:Workflow",
      "@type": "@id"
    },
    "workflowRun": {
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
            "type": "dcterms:type",
            "hreflang": "dcterms:language",
            "title": "rdfs:label",
            "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                    "type": "dcterms:type",
                    "hreflang": "dcterms:language",
                    "title": "rdfs:label",
                    "length": "dcterms:extent"
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
                    "type": "dcterms:type",
                    "hreflang": "dcterms:language",
                    "title": "rdfs:label",
                    "length": "dcterms:extent"
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
                    "type": "dcterms:type",
                    "hreflang": "dcterms:language",
                    "title": "rdfs:label",
                    "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
              },
              "@id": "prov:agent",
              "@type": "@id"
            }
          },
          "@id": "prov:qualifiedInfluence",
          "@type": "@id"
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
            "type": "dcterms:type",
            "hreflang": "dcterms:language",
            "title": "rdfs:label",
            "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
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
                "type": "dcterms:type",
                "hreflang": "dcterms:language",
                "title": "rdfs:label",
                "length": "dcterms:extent"
              }
            }
          },
          "@id": "prov:generated",
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
                        "type": "dcterms:type",
                        "hreflang": "dcterms:language",
                        "title": "rdfs:label",
                        "length": "dcterms:extent"
                      },
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  },
                  "@id": "dcterms:provenance",
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
                    "type": "dcterms:type",
                    "hreflang": "dcterms:language",
                    "title": "rdfs:label",
                    "length": "dcterms:extent"
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
                    "type": "dcterms:type",
                    "hreflang": "dcterms:language",
                    "title": "rdfs:label",
                    "length": "dcterms:extent"
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
                            "type": "dcterms:type",
                            "hreflang": "dcterms:language",
                            "title": "rdfs:label",
                            "length": "dcterms:extent"
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
                        "type": "dcterms:type",
                        "hreflang": "dcterms:language",
                        "title": "rdfs:label",
                        "length": "dcterms:extent"
                      },
                      "@id": "prov:actedOnBehalfOf",
                      "@type": "@id"
                    }
                  },
                  "@id": "dcterms:provenance",
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
                    "type": "dcterms:type",
                    "hreflang": "dcterms:language",
                    "title": "rdfs:label",
                    "length": "dcterms:extent"
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
                    "type": "dcterms:type",
                    "hreflang": "dcterms:language",
                    "title": "rdfs:label",
                    "length": "dcterms:extent"
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
                            "type": "dcterms:type",
                            "hreflang": "dcterms:language",
                            "title": "rdfs:label",
                            "length": "dcterms:extent"
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
                    "type": "dcterms:type",
                    "hreflang": "dcterms:language",
                    "title": "rdfs:label",
                    "length": "dcterms:extent"
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
        }
      },
      "@id": "wfprov:WorkflowRun",
      "@type": "@id"
    },
    "manifest": {
      "@context": {
        "@vocab": "http://purl.org/wf4ever/ro#",
        "describes": {
          "@id": "ore:describes",
          "@type": "@id"
        },
        "createdBy": {
          "@id": "dcterms:creator",
          "@type": "@id"
        },
        "createdOn": {
          "@id": "dcterms:created",
          "@type": "xsd:dateTime"
        }
      },
      "@id": "ro:Manifest",
      "@type": "@id"
    },
    "metadata": {
      "@context": {
        "created": {
          "@id": "dcterms:created",
          "@type": "xsd:dateTime"
        },
        "creator": {
          "@id": "dcterms:creator",
          "@type": "@id"
        },
        "description": "dcterms:description",
        "keywords": "dcat:keyword"
      },
      "@id": "http://purl.org/wf4ever/profiles#metadata"
    },
    "ResearchObject": "ro:ResearchObject",
    "Process": "wfdesc:Process",
    "Input": "wfdesc:Input",
    "Output": "wfdesc:Output",
    "Parameter": "wfdesc:Parameter",
    "name": "rdfs:label",
    "description": "rdfs:comment",
    "Workflow": "wfdesc:Workflow",
    "DataLink": "wfdesc:DataLink",
    "hasInput": {
      "@id": "wfdesc:hasInput",
      "@type": "@id",
      "@container": "@set"
    },
    "hasOutput": {
      "@id": "wfdesc:hasOutput",
      "@type": "@id",
      "@container": "@set"
    },
    "hasSource": {
      "@id": "wfdesc:hasSource",
      "@type": "@id"
    },
    "hasSink": {
      "@id": "wfdesc:hasSink",
      "@type": "@id"
    },
    "activityType": "@type",
    "agentType": "@type",
    "entityType": "@type",
    "featureType": "@type",
    "provType": "@type",
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
    "atLocation": {
      "@id": "prov:atLocation",
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
    "qualifiedDelegation": {
      "@id": "prov:qualifiedDelegation",
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
    "qualifiedInfluence": {
      "@id": "prov:qualifiedInfluence",
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
    "wasInfluencedBy": {
      "@id": "prov:wasInfluencedBy",
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
      "@id": "dcterms:provenance",
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
    "id": "@id",
    "links": "rdfs:seeAlso",
    "ProcessRun": "wfprov:ProcessRun",
    "WorkflowRun": "wfprov:WorkflowRun",
    "wasOutputFrom": {
      "@id": "prov:generated",
      "@type": "@id",
      "@container": "@set"
    },
    "Manifest": "ro:Manifest",
    "ro": "http://purl.org/wf4ever/ro#",
    "dcterms": "http://purl.org/dc/terms/",
    "ore": "http://www.openarchives.org/ore/terms/",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "prov": "http://www.w3.org/ns/prov#",
    "dcat": "http://www.w3.org/ns/dcat#",
    "foaf": "http://xmlns.com/foaf/0.1/",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "dct": "http://purl.org/dc/terms/",
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "oa": "http://www.w3.org/ns/oa#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever-profiles/complete-provenance-trace/context.jsonld)

## Sources

* [Wf4Ever Research Object Model](http://purl.org/wf4ever/model)
* [CWLProv - Provenance profiles for Common Workflow Language](https://w3id.org/cwl/prov)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/wf4ever-profiles/complete-provenance-trace`

