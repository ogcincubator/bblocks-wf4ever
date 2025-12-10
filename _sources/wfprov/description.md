# Workflow Provenance Ontology (wfprov)

## Overview

The Workflow Provenance ontology (wfprov) extends PROV-O to describe workflow execution traces. It links workflow runs to their descriptions and tracks the provenance of workflow executions.

## Namespace

`http://purl.org/wf4ever/wfprov#`

## Key Classes

- **WorkflowRun** - An execution of a workflow
- **ProcessRun** - An execution of a process
- **WorkflowEngine** - Software that executes workflows
- **Artifact** - Data entity used or generated

## Key Properties

- `wfprov:wasPartOfWorkflowRun` - Object property; domain `wfprov:ProcessRun`, range `wfprov:WorkflowRun`; sub-property of `prov:wasInformedBy`.
- `wfprov:usedInput` - Object property; domain `wfprov:ProcessRun`, range `wfprov:Artifact`; sub-property of `prov:used`.
- `wfprov:wasOutputFrom` - Object property; domain `wfprov:Artifact`, range `wfprov:ProcessRun`; sub-property of `prov:wasGeneratedBy`.
- `wfprov:describedByWorkflow` - Object property; domain `wfprov:WorkflowRun`, range `wfdesc:Workflow`.
- `wfprov:describedByProcess` - Object property; domain `wfprov:ProcessRun`, range `wfdesc:Process`.
- `wfprov:wasEnactedBy` - Object property; domain `wfprov:WorkflowRun`, range `wfprov:WorkflowEngine`; sub-property of `prov:wasAssociatedWith`.
- `wfprov:describedByParameter` - Object property; domain `wfprov:Artifact`, range `wfdesc:Parameter`.

## Usage

This ontology is used to describe the retrospective provenance of workflows - what actually happened during execution, linking it to the workflow description (wfdesc).
