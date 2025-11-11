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
