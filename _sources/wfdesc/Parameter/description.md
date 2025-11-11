# wfdesc:Parameter

## Description

A **Parameter** is the base class for describing parameters of workflow processes. In wfdesc, parameters represent any kind of data port that can be connected in a workflow.

## Class Hierarchy

```
wfdesc:Parameter (base class)
├── wfdesc:Input (input parameter)
└── wfdesc:Output (output parameter)
```

## Usage

Parameters are typically not used directly but through their subclasses (Input, Output). They represent the interface points of a Process and can be associated with Artifacts that describe the data types.

## Related Classes

- **Input**: A parameter that receives data into a process
- **Output**: A parameter that produces data from a process
- **Artifact**: Describes the type of data associated with a parameter
- **Process**: The class that has parameters
