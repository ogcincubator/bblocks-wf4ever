
# wfdesc:WorkflowInstance (Datatype)

`ogc.bbr.wf4ever.wfdesc.WorkflowInstance` *v1.0*

A specialized workflow description that includes all concrete data, parameters, and settings required to execute a specific workflow run. It bridges the gap between abstract workflow descriptions and concrete workflow executions.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

## Workflow Instance

A `WorkflowInstance` represents a specialized workflow description that includes all the concrete data, parameters, and settings required to execute a specific workflow run.

### Purpose

A `WorkflowInstance` is a specialization of `wfdesc:Workflow` that bridges the gap between abstract workflow descriptions and concrete workflow executions. While a `wfdesc:Workflow` defines the general structure and capabilities, a `WorkflowInstance` contains all the specific values, configurations, and bound parameters needed to create a `wfprov:WorkflowRun`.

### Key Characteristics

- **Inherits from Workflow**: A `WorkflowInstance` is a subclass of `wfdesc:Workflow`, so it has all the structural properties (processes, data links, inputs, outputs)
- **Execution-ready**: Contains all bound parameters and concrete values needed for execution
- **Provenance bridge**: Forms the link between workflow descriptions and their execution traces
- **Reproducible**: Captures the exact configuration needed to reproduce a specific workflow execution

### Relationship to Other Classes

- **Extends**: `wfdesc:Workflow` (inherits structure)
- **Prepares**: `wfprov:WorkflowRun` (execution configuration)
- **Contains**: Concrete parameter values and execution settings

### Use Cases

1. **Workflow Execution Preparation**: Creating execution-ready configurations from abstract workflow definitions
2. **Reproducible Science**: Storing exact parameter combinations for reproducible research
3. **Provenance Linkage**: Connecting workflow descriptions to their execution traces  
4. **Parameterization**: Managing different parameter sets for the same workflow template
5. **Execution Planning**: Validating that all required inputs are provided before execution

### JSON-LD Context

When used in JSON-LD, the workflow instance inherits the wfdesc context and adds execution-specific terms:

```json
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/wfdesc#",
    "describedBy": {"@type": "@id"},
    "hasArtifact": {"@type": "@id"},
    "executionSettings": "http://purl.org/wf4ever/wfprov#executionSettings",
    "readyForExecution": {"@type": "http://www.w3.org/2001/XMLSchema#boolean"}
  }
}
```

### Best Practices

- **Complete Parameter Binding**: Ensure all required inputs have bound artifacts
- **Version Tracking**: Include workflow definition version and execution engine details
- **Validation**: Verify parameter types and constraints before marking as execution-ready
- **Documentation**: Include human-readable descriptions of the parameter choices
- **Provenance Preparation**: Structure data to facilitate easy transition to workflow runs
## Examples

### KindGrove Workflow Instance
#### json
```json
{
  "@type": "WorkflowInstance",
  "@id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c-instance",
  "name": "KindGrove Mangrove Biomass Analysis - Myanmar Instance",
  "description": "Execution-ready configuration for analyzing mangrove biomass in Myanmar using satellite imagery",
  "describedBy": "#kindgrove-workflow",
  "hasInput": [
    {
      "@id": "#bound-north",
      "@type": "Input",
      "name": "north",
      "description": "Northern boundary of analysis area",
      "hasArtifact": {
        "@type": "Artifact",
        "value": 16.1,
        "@id": "urn:sha1:e71003c6b7dd4093ce139ac0c51a6ba38d54a439"
      }
    },
    {
      "@id": "#bound-south", 
      "@type": "Input",
      "name": "south",
      "description": "Southern boundary of analysis area",
      "hasArtifact": {
        "@type": "Artifact",
        "value": 15.9
      }
    },
    {
      "@id": "#bound-east",
      "@type": "Input", 
      "name": "east",
      "description": "Eastern boundary of analysis area",
      "hasArtifact": {
        "@type": "Artifact",
        "value": 95.35
      }
    },
    {
      "@id": "#bound-west",
      "@type": "Input",
      "name": "west", 
      "description": "Western boundary of analysis area",
      "hasArtifact": {
        "@type": "Artifact",
        "value": 95.15
      }
    },
    {
      "@id": "#bound-cloud-cover",
      "@type": "Input",
      "name": "cloud_cover_max",
      "description": "Maximum allowed cloud cover percentage",
      "hasArtifact": {
        "@type": "Artifact", 
        "value": 20
      }
    },
    {
      "@id": "#bound-days-back",
      "@type": "Input",
      "name": "days_back", 
      "description": "Number of days back to search for imagery",
      "hasArtifact": {
        "@type": "Artifact",
        "value": 90
      }
    },
    {
      "@id": "#bound-output-dir",
      "@type": "Input",
      "name": "output_dir",
      "description": "Directory for output results",
      "hasArtifact": {
        "@type": "Artifact",
        "value": "results"
      }
    }
  ],
  "hasOutput": [
    {
      "@id": "#expected-biomass-map",
      "@type": "Output", 
      "name": "biomass_map",
      "description": "Generated mangrove biomass map"
    },
    {
      "@id": "#expected-statistics",
      "@type": "Output",
      "name": "statistics", 
      "description": "Statistical analysis results"
    }
  ],
  "executionSettings": {
    "engine": "cwltool",
    "version": "3.1.20251031082601",
    "environment": "container",
    "scheduler": "local",
    "resources": {
      "cpu": "4",
      "memory": "8GB", 
      "disk": "50GB"
    }
  },
  "readyForExecution": true,
  "validatedAt": "2025-11-03T10:15:30Z",
  "configurationHash": "sha256:a1b2c3d4e5f6789012345678901234567890123456789012345678901234567890"
}
```


### Basic Workflow Instance
#### json
```json
{
  "@type": "WorkflowInstance", 
  "@id": "#simple-analysis-instance",
  "name": "Basic Data Analysis Instance",
  "describedBy": "#data-processing-workflow",
  "hasInput": [
    {
      "@id": "#input-file",
      "@type": "Input",
      "name": "input_file",
      "hasArtifact": {
        "@type": "Artifact",
        "value": "data.csv"
      }
    },
    {
      "@id": "#threshold-param", 
      "@type": "Input",
      "name": "threshold",
      "hasArtifact": {
        "@type": "Artifact", 
        "value": 0.5
      }
    }
  ],
  "hasOutput": [
    {
      "@id": "#output-results",
      "@type": "Output",
      "name": "results",
      "description": "Analysis results"
    }
  ],
  "executionSettings": {
    "engine": "local-python",
    "environment": "conda",
    "scheduler": "local"
  },
  "readyForExecution": true
}
```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A specialized workflow description that includes all concrete data, parameters,
  and settings required to execute a specific workflow run
type: object
properties:
  '@type':
    const: WorkflowInstance
    description: Type identifier for workflow instance
  '@id':
    type: string
    format: uri
    description: Unique identifier for this workflow instance
  name:
    type: string
    description: Human-readable name for this workflow instance
  description:
    type: string
    description: Description of this workflow instance
  describedBy:
    type: string
    format: uri
    description: URI reference to the workflow definition this instance is based on
  hasInput:
    type: array
    description: Input parameters with bound artifacts and concrete values
    items:
      type: object
      properties:
        '@type':
          const: Input
        '@id':
          type: string
          format: uri
        name:
          type: string
        description:
          type: string
        hasArtifact:
          type: object
          properties:
            '@type':
              const: Artifact
            '@id':
              type: string
              format: uri
            value:
              description: Concrete value bound to this parameter
          required:
          - '@type'
          - value
      required:
      - '@type'
      - hasArtifact
  hasOutput:
    type: array
    description: Expected output parameters for this workflow instance
    items:
      type: object
      properties:
        '@type':
          const: Output
        '@id':
          type: string
          format: uri
        name:
          type: string
        description:
          type: string
      required:
      - '@type'
  hasSubProcess:
    type: array
    description: Sub-processes contained in this workflow instance
    items:
      type: object
      properties:
        '@type':
          enum:
          - Process
          - Workflow
        '@id':
          type: string
          format: uri
        name:
          type: string
      required:
      - '@type'
  hasDataLink:
    type: array
    description: Data links between processes in this workflow instance
    items:
      type: object
      properties:
        '@type':
          const: DataLink
        '@id':
          type: string
          format: uri
        hasSource:
          type: string
          format: uri
        hasSink:
          type: string
          format: uri
      required:
      - '@type'
  executionSettings:
    type: object
    description: Engine and environment configuration for execution
    properties:
      engine:
        type: string
        description: Name of the workflow execution engine
        examples:
        - cwltool
        - zoo-project
        - nextflow
        - snakemake
      version:
        type: string
        description: Version of the execution engine
      environment:
        type: string
        description: Execution environment type
        enum:
        - container
        - conda
        - local
        - hpc
        - cloud
        default: local
      scheduler:
        type: string
        description: Job scheduler or execution backend
        examples:
        - local
        - slurm
        - kubernetes
        - aws-batch
      resources:
        type: object
        description: Resource requirements and limits
        properties:
          cpu:
            type:
            - string
            - number
            description: CPU requirement (cores or description)
          memory:
            type: string
            description: Memory requirement (e.g., '4GB', '512MB')
          disk:
            type: string
            description: Disk space requirement
          gpu:
            type:
            - string
            - number
            description: GPU requirement
    additionalProperties: true
  readyForExecution:
    type: boolean
    description: Whether all required parameters are bound and the workflow is ready
      to execute
    default: false
  validatedAt:
    type: string
    format: date-time
    description: Timestamp when this workflow instance was validated as execution-ready
  configurationHash:
    type: string
    description: Hash of the configuration for reproducibility tracking
required:
- '@type'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/WorkflowInstance/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfdesc/WorkflowInstance/schema.yaml)

## Sources

* [Workflow Description Ontology - WorkflowInstance](http://purl.org/wf4ever/wfdesc#WorkflowInstance)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfdesc/WorkflowInstance`

