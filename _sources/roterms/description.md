# Research Object Terms (roterms)

## Overview

The Research Object Terms vocabulary (`roterms`) defines classes and properties that may be used with annotations on Research Objects and their resources. It provides a rich vocabulary for describing scientific concepts, tasks, hypotheses, and quality metrics.

## Namespace

`http://purl.org/wf4ever/roterms#`

## Key Classes

### Scientific Concepts

- **Hypothesis** - A scientific hypothesis being tested or explored
- **Conclusion** - A conclusion drawn from research
- **ExperimentalDesign** - Description of experimental methodology
- **ScientificMethod** - A specific scientific method or approach

### Resource Types

- **Sketch** - A sketch or preliminary design
- **Note** - A research note or annotation
- **ProspectivePlan** - A plan for future research
- **Software** - Software or code artifact
- **WebService** - A web service used in research

### Quality and Review

- **QualityAnnotation** - Annotation about quality aspects
- **Review** - A peer review or assessment
- **Rating** - A quality rating

## Key Properties

### Descriptive Properties

- **exampleValue** - Provides an example value for a parameter or input
  - Domain: Any resource
  - Range: Literal or Resource
  - Usage: Document expected input formats

- **defaultValue** - Specifies a default value
  - Domain: Parameter or Input
  - Range: Literal or Resource

- **sampleSize** - Sample size for statistical analysis
  - Domain: Dataset or Analysis
  - Range: Integer

### Functional Properties

- **performsTask** - Describes the task performed by a process or workflow
  - Domain: Process, Workflow, or Software
  - Range: Task or Literal description
  - Usage: Semantic description of functionality

- **requiresHardware** - Hardware requirements for execution
  - Domain: Software or Process
  - Range: Hardware specification

- **requiresSoftware** - Software dependencies
  - Domain: Software or Workflow
  - Range: Software package

### Provenance Properties

- **wasInputTo** - Resource was input to a process
  - Domain: Resource or Artifact
  - Range: Process or Activity

- **wasOutputFrom** - Resource was output from a process
  - Domain: Resource or Artifact
  - Range: Process or Activity

- **authoredBy** - Created by a specific person or agent
  - Domain: Any resource
  - Range: Agent (Person or Organization)

- **authoredOn** - Date/time of authoring
  - Domain: Any resource
  - Range: DateTime

### Scientific Properties

- **hypothesis** - Links to a hypothesis being tested
  - Domain: Experiment or Research Object
  - Range: Hypothesis

- **supports** - Evidence that supports a claim or hypothesis
  - Domain: Artifact or Result
  - Range: Hypothesis or Claim

- **refutes** - Evidence that refutes a claim or hypothesis
  - Domain: Artifact or Result
  - Range: Hypothesis or Claim

- **methodology** - Research methodology employed
  - Domain: Research Object or Experiment
  - Range: ScientificMethod or ExperimentalDesign

### Quality Properties

- **technicalStandard** - Technical standard conformed to
  - Domain: Resource
  - Range: Standard specification

- **validatedBy** - Validation process or tool used
  - Domain: Resource or Artifact
  - Range: Validation method

- **qualityScore** - Numerical quality score
  - Domain: Any resource
  - Range: Float (0-1 or 0-100)

## Usage Examples

### Example Values for Parameters

```json
{
  "@context": "http://purl.org/wf4ever/roterms",
  "@type": "wfdesc:Input",
  "name": "threshold",
  "roterms:exampleValue": 0.95,
  "roterms:defaultValue": 0.8,
  "description": "Confidence threshold for classification"
}
```

### Task Description

```json
{
  "@context": "http://purl.org/wf4ever/roterms",
  "@type": "wfdesc:Process",
  "name": "ImageClassifier",
  "roterms:performsTask": {
    "@type": "roterms:Task",
    "label": "Image Classification",
    "description": "Classifies images using deep learning"
  },
  "roterms:requiresSoftware": "TensorFlow 2.0+"
}
```

### Hypothesis Testing

```json
{
  "@context": "http://purl.org/wf4ever/roterms",
  "@type": "ro:ResearchObject",
  "roterms:hypothesis": {
    "@type": "roterms:Hypothesis",
    "description": "Higher temperature increases reaction rate",
    "@id": "urn:uuid:hypothesis-001"
  },
  "aggregates": [
    {
      "@id": "results.csv",
      "@type": "wf4ever:Dataset",
      "roterms:supports": "urn:uuid:hypothesis-001"
    }
  ]
}
```

### Quality Annotation

```json
{
  "@context": "http://purl.org/wf4ever/roterms",
  "@type": "roterms:QualityAnnotation",
  "annotates": "workflow.cwl",
  "roterms:qualityScore": 0.87,
  "roterms:validatedBy": "CWL Validator 1.2",
  "roterms:technicalStandard": "CWL v1.2"
}
```

## Integration with Other Vocabularies

### Dublin Core Terms

roterms complements Dublin Core with research-specific terms:

- Use `dcterms:creator` for general authorship
- Use `roterms:authoredBy` for explicit research authorship with provenance

### PROV-O

roterms extends PROV-O provenance:

- `roterms:wasInputTo` / `roterms:wasOutputFrom` complement PROV relationships
- Provides domain-specific provenance for scientific workflows

### Schema.org

roterms can be used alongside schema.org vocabulary for better web discoverability.

## Use Cases

### Documentation

Provide comprehensive documentation of workflow parameters with examples and defaults.

### Reproducibility

Document exact software versions, hardware requirements, and methodology for reproducible research.

### Quality Assurance

Track validation results, quality scores, and conformance to standards.

### Scientific Communication

Explicitly link research objects to hypotheses, conclusions, and scientific methods.

### Semantic Search

Enable semantic queries like "find all workflows that perform image classification" using `roterms:performsTask`.

## Best Practices

1. **Use exampleValue liberally** - Help users understand expected inputs
2. **Document dependencies** - Always specify software/hardware requirements
3. **Link to hypotheses** - Make scientific reasoning explicit
4. **Include quality metrics** - Document validation and quality scores
5. **Be specific with tasks** - Use controlled vocabularies for task descriptions

## References

- [Research Object Ontology](http://purl.org/wf4ever/ro)
- [Wf4Ever Research Object Model](http://wf4ever.github.io/ro/)
- [PROV-O](https://www.w3.org/TR/prov-o/)
- [Dublin Core Metadata Terms](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/)
