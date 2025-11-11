# ro:ResearchObject

## Description

A **ResearchObject** groups together resources, data, methods, and contextual information. It provides a structured way to package research results with their provenance, making them portable, shareable, and preservable.

## Relations

- Aggregates `ro:Resource` via `ore:aggregates`
- Has a `ro:Manifest` via `ore:isDescribedBy` (from ORE standard)
- Can contain a `ro:Folder` to organize resources
- Can have `ro:AggregatedAnnotation` to annotate resources

## Example

See the real-world example from a CWLProv 0.6.0 execution showing a complete Research Object with workflow definition, provenance traces, and content-addressed data files from a mangrove biomass analysis.
