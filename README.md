# Wf4Ever Ontologies Building Blocks

This repository contains [OGC Building Blocks](https://ogcincubator.github.io/bblocks-docs) for the **Wf4Ever ontologies suite**, enabling workflow description, provenance tracking, and research object aggregation with semantic annotations.

Note - wf4ever is a legacy and RO-crate should be used according to the authors. TBD - provide link to RO-crate BB when available.

[![Build Status](https://github.com/ogcincubator/bblocks-wf4ever/workflows/Process%20building%20blocks/badge.svg)](https://github.com/ogcincubator/bblocks-wf4ever/actions)

## Overview

The Wf4Ever ontologies provide a comprehensive framework for describing scientific workflows and their execution:

- **Prospective Provenance**: Describes what a workflow is designed to do (wfdesc)
- **Retrospective Provenance**: Tracks what actually happened during execution (wfprov)  
- **Research Object Packaging**: Aggregates and contextualizes research artifacts (ro)
- **Specialized Artifact Types**: Provides concrete implementations for common workflow artifacts (wf4ever)

This repository provides Building Blocks that make these ontologies **reusable**, **testable**, and **interoperable** with modern workflows and APIs.

## Building Blocks

### Ontology Building Blocks

#### 1. wfdesc - Workflow Description Ontology
**ID**: `ogc.bbr.wf4ever.wfdesc`  
**Namespace**: `http://purl.org/wf4ever/wfdesc#`  
**Purpose**: Describe workflow structure, processes, inputs, outputs

Key concepts:
- `Workflow`: A directed graph of processes
- `Process`: An atomic computational step
- `Input`/`Output`: Data parameters with types
- `DataLink`: Connections between process outputs and inputs

#### 2. wfprov - Workflow Provenance Ontology
**ID**: `ogc.bbr.wf4ever.wfprov`  
**Namespace**: `http://purl.org/wf4ever/wfprov#`  
**Purpose**: Track workflow execution traces

Key concepts:
- `WorkflowRun`: An execution instance of a workflow
- `ProcessRun`: Execution of an individual process
- `Artifact`: Data artifacts consumed/produced during execution
- Temporal information (start/end times, durations)

#### 3. ro - Research Object Ontology
**ID**: `ogc.bbr.wf4ever.ro`  
**Namespace**: `http://purl.org/wf4ever/ro#`  
**Purpose**: Package and aggregate research artifacts

Key concepts:
- `ResearchObject`: Container for aggregating resources
- `Resource`: Any aggregated artifact (data, workflows, papers)
- `Manifest`: Metadata about the aggregation
- Annotations and semantic relationships

#### 4. wf4ever - Extension Ontology
**ID**: `ogc.bbr.wf4ever.wf4ever`  
**Namespace**: `http://purl.org/wf4ever/wf4ever#`  
**Purpose**: Specialized artifact and process types for workflow systems

Key concepts:
- `File`: File-based artifacts (JSON, GeoTIFF, etc.)
- `Dataset`: Scientific dataset collections
- `Document`: Textual/formatted content (PDF, HTML)
- `Image`: Graphical/raster data
- `WebServiceProcess`: Web service-based processes
- `WorkflowResearchObject`: Research objects containing workflows

## Features

✅ **JSON-LD Contexts**: Semantic uplift for JSON documents  
✅ **JSON Schemas**: Validation and documentation  
✅ **Examples**: Real CWL provenance data from scientific workflows  
✅ **Validation**: Automatic testing with pass/fail examples  
✅ **Ontology Documentation**: Auto-generated from OWL/RDF sources  
✅ **Complete Coverage**: 25 classes + 15 properties across 4 ontologies

## Getting Started

### View the Register

Browse the online register with full documentation and examples:

🔗 **[Live Register](https://ogcincubator.github.io/bblocks-wf4ever/)**

### Use in Your Project

Reference building blocks directly from the register:

```yaml
# In your bblocks-config.yaml
imports:
  - https://ogcincubator.github.io/bblocks-wf4ever/
```

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$ref": "https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/wfdesc/schema.yaml"
}
```

```jsonld
{
  "@context": "https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/wfdesc/context.jsonld"
}
```

### Building Locally

Build the register locally using Docker:

```bash
./build.sh
```

View the results locally:

```bash
./view.sh
```

Then open http://localhost:9090/register/

## Examples

### Workflow Description (wfdesc)

```json
{
  "@context": "https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/wfdesc/context.jsonld",
  "@id": "workflow:HelloWorld",
  "@type": "Workflow",
  "hasSubProcess": [
    {
      "@id": "workflow:echo",
      "@type": "Process",
      "hasInput": [{
        "@id": "workflow:message",
        "label": "Message to echo"
      }],
      "hasOutput": [{
        "@id": "workflow:echoed_message",
        "label": "Echoed message"
      }]
    }
  ]
}
```

### Workflow Execution Provenance (wfprov)

```json
{
  "@context": "https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/wfprov/context.jsonld",
  "@id": "run:execution-123",
  "@type": "WorkflowRun",
  "describedByWorkflow": "workflow:HelloWorld",
  "startedAtTime": "2025-11-07T10:00:00Z",
  "endedAtTime": "2025-11-07T10:05:00Z",
  "wasEnactedBy": "engine:cwltool-3.1"
}
```

### Research Object (ro)

```json
{
  "@context": "https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/ro/context.jsonld",
  "@id": "ro:my-research",
  "@type": "ResearchObject",
  "aggregates": [
    { "@id": "workflow:HelloWorld", "@type": "Workflow" },
    { "@id": "run:execution-123", "@type": "WorkflowRun" },
    { "@id": "data:results.json", "@type": "Resource" }
  ]
}
```

### Specialized Artifact Types (wf4ever)

```json
{
  "@context": "https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/wf4ever/context.jsonld",
  "@id": "artifact:mangrove_mask.tif",
  "@type": ["wfprov:Artifact", "wf4ever:File"],
  "basename": "mangrove_mask.tif",
  "format": "image/tiff",
  "checksum": "sha1:0999fb93da...",
  "size": 2048576
}
```

## Related Building Blocks

- **[CWL Building Blocks](https://github.com/ogcincubator/bblocks-cwl)**: Common Workflow Language schemas and validation
- **[OGC API - Processes](https://github.com/ogcincubator/bblocks-ogcapi-processes)**: Geoprocessing API building blocks
- **[PROV-O](https://www.w3.org/TR/prov-o/)**: W3C Provenance Ontology

## Future Extensions

This repository focuses on the core ontology building blocks. Future work may include:

- **Transformers**: Bidirectional conversion between wfdesc and OGC API - Processes
- **Mappings**: Integration with STAC and other geospatial standards
- **Validators**: Advanced constraint checking for workflow definitions and provenance traces

## Documentation

- **[Building Blocks Documentation](https://ogcincubator.github.io/bblocks-docs)**: Framework overview
- **[Wf4Ever Project](https://wf4ever.github.io/)**: Original ontologies project
- **[CWL Specification](https://www.commonwl.org/)**: Common Workflow Language
- **[OGC API - Processes](https://ogcapi.ogc.org/processes/)**: OGC geoprocessing standard

## Contributing

Contributions are welcome! Please see the [Building Blocks contribution guide](https://ogcincubator.github.io/bblocks-docs/build/contribution).

To add examples or improve documentation:
1. Fork this repository
2. Edit source files in `_sources/`
3. Run `./build.sh` to test
4. Submit a pull request

## License

The Wf4Ever ontologies are available under open licenses. See individual building block metadata for details.

## Acknowledgements

This work builds upon the [Wf4Ever Project](https://www.wf4ever-project.org/) funded by the European Commission's Seventh Framework Programme (FP7).

Building Blocks framework developed by the [OGC](https://www.ogc.org/)
