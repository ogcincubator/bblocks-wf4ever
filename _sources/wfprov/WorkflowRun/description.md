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
