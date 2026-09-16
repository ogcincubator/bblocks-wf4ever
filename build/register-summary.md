# Wf4Ever Building Blocks

Building blocks for the Wf4Ever ontologies suite (wfdesc, wfprov, ro, wf4ever) enabling
workflow description, provenance tracking, research object aggregation, and specialized artifact types.


This repository contains four separate building blocks for the **Wf4Ever ontologies**:

- **wfdesc**: Workflow Description Ontology for describing workflow structure (prospective provenance)
- **wfprov**: Workflow Provenance Ontology for tracking execution traces (retrospective provenance)
- **ro**: Research Object Ontology for packaging and aggregating research artifacts
- **wf4ever**: Extension ontology providing specialized artifact types (File, Dataset, Document, Image) and process types (WebServiceProcess, WorkflowResearchObject)

All examples are based on real CWL (Common Workflow Language) provenance data from
scientific workflow executions.


## Building Blocks

### `ogc.bbr.wf4ever.ro.Resource` — ro:Resource

**Type:** datatype

A resource that can be aggregated in a Research Object. Resources represent any artifact that contributes to the research outcome, such as data files, workflows, documentation, or external references.

### `ogc.bbr.wf4ever.ro.Folder` — ro:Folder

**Type:** datatype

A folder that organizes resources within a Research Object. Folders provide hierarchical structure, similar to filesystem directories, allowing logical grouping of related resources.

### `ogc.bbr.wf4ever.ro.SemanticAnnotation` — ro:SemanticAnnotation

**Type:** datatype

A semantic annotation is a specialization of ao:Annotation which requires that the annotation body points to an RDF Graph containing semantic information about the annotated resource.

### `ogc.bbr.wf4ever.ro` — Research Object Ontology (ro)

**Type:** schema

The Research Object ontology (ro) provides concepts for bundling and aggregating research artifacts, describing folder structures and annotations.

### `ogc.bbr.wf4ever.wf4ever.Dataset` — wf4ever:Dataset

**Type:** datatype

A dataset artifact - a collection of data values or files representing a scientific dataset.

### `ogc.bbr.wf4ever.wf4ever.Document` — wf4ever:Document

**Type:** datatype

A document artifact - textual or formatted content such as PDF, HTML, or text files.

### `ogc.bbr.wf4ever.wf4ever.File` — wf4ever:File

**Type:** datatype

A file artifact - a specialization of wfdesc:Artifact representing a file-based data entity used or produced by workflow execution.

### `ogc.bbr.wf4ever.wf4ever.Image` — wf4ever:Image

**Type:** datatype

An image artifact - visual representation such as PNG, JPEG, or raster geospatial imagery.

### `ogc.bbr.wf4ever.wf4ever.WebServiceProcess` — wf4ever:WebServiceProcess

**Type:** datatype

A web service process - a process description whose enactment involves making a web service call.

### `ogc.bbr.wf4ever.wfdesc` — Workflow Description Ontology (wfdesc)

**Type:** schema

The Workflow Description ontology (wfdesc) describes the structure of workflows, including processes, inputs, outputs, and data flow.

### `ogc.bbr.wf4ever.wfdesc.Artifact` — wfdesc:Artifact

**Type:** datatype

An artifact representing a data value, file, or resource that can be used as input or generated as output by workflow processes. Artifacts provide concrete data representations for parameter binding.

### `ogc.bbr.wf4ever.wfdesc.WorkflowInstance` — wfdesc:WorkflowInstance

**Type:** datatype

A specialized workflow description that includes all concrete data, parameters, and settings required to execute a specific workflow run. It bridges the gap between abstract workflow descriptions and concrete workflow executions.

### `ogc.bbr.wf4ever.ro.AggregatedAnnotation` — ro:AggregatedAnnotation

**Type:** datatype

An annotation about resources within a Research Object. Annotations provide additional metadata, provenance information, or contextual details about aggregated resources, stored as part of the Research Object itself.

### `ogc.bbr.wf4ever.ro.Manifest` — ro:Manifest

**Type:** datatype

A manifest that describes the structure and contents of a Research Object. The manifest provides metadata about the Research Object, its aggregated resources, annotations, and organizational structure.

### `ogc.bbr.wf4ever.ro.FolderEntry` — ro:FolderEntry

**Type:** datatype

An entry within a folder that associates a name with a resource. FolderEntries provide the mapping between folder paths and actual resources, similar to filesystem directory entries.

### `ogc.bbr.wf4ever.wfprov` — Workflow Provenance Ontology (wfprov)

**Type:** schema

The Workflow Provenance ontology (wfprov) extends PROV-O to describe workflow execution traces, linking workflow runs to their descriptions.

### `ogc.bbr.wf4ever.wfdesc.Parameter` — wfdesc:Parameter

**Type:** datatype

A parameter (input or output) of a workflow process. This is the base class for Input, Output, and Configuration.

### `ogc.bbr.wf4ever.wfprov.WorkflowEngine` — wfprov:WorkflowEngine

**Type:** datatype

A software agent that executes workflows. The WorkflowEngine is responsible for enacting workflow and process executions, managing the execution environment and resources.

### `ogc.bbr.wf4ever.ro.ResearchObject` — ro:ResearchObject

**Type:** datatype

A Research Object that bundles resources, data, methods, and contextual information. It provides a structured way to package research outputs with their provenance, making them portable, shareable, and preservable.

### `ogc.bbr.wf4ever.wf4ever` — Wf4Ever Extension Ontology

**Type:** schema

The wf4ever ontology extends ro, wfdesc and wfprov with specialized artifact and process types commonly used in workflow research objects.

### `ogc.bbr.wf4ever.wfdesc.Input` — wfdesc:Input

**Type:** datatype

An input parameter to a workflow process. Inputs receive data from external sources or from outputs of other processes via DataLinks.

### `ogc.bbr.wf4ever.wfdesc.Output` — wfdesc:Output

**Type:** datatype

An output parameter from a workflow process. Outputs produce data that can be consumed by inputs of other processes or as final workflow results.

### `ogc.bbr.wf4ever.wfprov.Artifact` — wfprov:Artifact

**Type:** datatype

A data entity that was used as input or generated as output during a workflow execution. Artifacts are the data products consumed or produced by process runs.

### `ogc.bbr.wf4ever.wfdesc.DataLink` — wfdesc:DataLink

**Type:** datatype

A connection between processes in a workflow, linking an output of one process to an input of another process. DataLinks define the data flow in a workflow.

### `ogc.bbr.wf4ever.wfdesc.Process` — wfdesc:Process

**Type:** datatype

A computational process or task in a workflow. Processes have inputs, outputs, and perform computations. This is the base class for atomic processes and composite Workflows.

### `ogc.bbr.wf4ever.wfdesc.Workflow` — wfdesc:Workflow

**Type:** datatype

A composite process that contains sub-processes connected by data links. Workflows are directed graphs where nodes are processes and edges are data flow connections.

### `ogc.bbr.wf4ever.wfprov.ProcessRun` — wfprov:ProcessRun

**Type:** datatype

An execution instance of a process. A ProcessRun represents the actual execution of a process described by wfdesc:Process, tracking what happened during that execution including inputs used, outputs generated, and timing information.

### `ogc.bbr.wf4ever.wf4ever.WorkflowResearchObject` — wf4ever:WorkflowResearchObject

**Type:** datatype

A research object that aggregates at least one workflow description, along with associated resources and provenance.

### `ogc.bbr.wf4ever.wfprov.WorkflowRun` — wfprov:WorkflowRun

**Type:** datatype

An execution instance of a workflow. A WorkflowRun is a special type of ProcessRun that represents the execution of a complete workflow (wfdesc:Workflow), containing multiple ProcessRuns for its sub-processes.

### `ogc.bbr.wf4ever.wf4ever-profiles.complete-provenance-trace` — Complete Workflow Provenance Trace

**Type:** schema

Master profile combining Research Object, Workflow Description, and Workflow Execution Provenance

