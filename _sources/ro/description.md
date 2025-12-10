# Research Object Ontology (ro)

## Overview

The Research Object ontology (ro) provides concepts for bundling and aggregating research artifacts. It enables the packaging of workflows, data, and metadata into a single research object.

## Namespace

`http://purl.org/wf4ever/ro#`

## Key Classes

- **ResearchObject** - A bundled collection of resources
- **Resource** - Any research artifact
- **Folder** - Directory structure
- **FolderEntry** - Entry in a folder
- **AggregatedAnnotation** - Annotation about resources
- **Manifest** - Manifest describing the research object

## Key Properties

- `ro:entryName` - Functional data property naming a `ro:FolderEntry` within a `ro:Folder` (range `xsd:string`).
- `ro:annotatesAggregatedResource` - Object property linking a `ro:AggregatedAnnotation` to the annotated aggregated `ro:Resource`.

Note: Other RO behaviours like aggregation (`ore:aggregates`) and manifests are defined via ORE/DC terms and not as RO-native properties in this ontology file.

## Usage

This ontology is used to package workflow descriptions, execution provenance, and data into cohesive research objects that can be shared and preserved.
