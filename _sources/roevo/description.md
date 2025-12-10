# Research Object Evolution Ontology (roevo)

## Overview

The Research Object Evolution ontology (roevo) extends the [ro ontology](http://purl.org/wf4ever/ro) to capture the lifecycle and versioning of research objects using [PROV-O](https://www.w3.org/TR/prov-o/).

This ontology enables tracking of:
- Version history and evolution of research objects
- Snapshots and archives of research objects at different points in time
- Relationships between different versions (derivation, revision, etc.)
- Lifecycle states and transitions

## Namespace

`http://purl.org/wf4ever/roevo#`

## Key Classes

### Core Evolution Classes

- **VersionableResource** - A resource that can have multiple versions
- **LiveRO** - A live (current/working) research object that can be modified
- **SnapshotRO** - An immutable snapshot of a research object at a point in time
- **ArchivedRO** - A long-term archived version of a research object

### Versioning Classes

- **VersionInfo** - Information about a specific version
- **ChangeSpecification** - Specification of changes between versions

## Key Properties

### Versioning Properties

- **hasVersion** - Links a versionable resource to its versions
- **isVersionOf** - Inverse of hasVersion
- **wasRevisionOf** - Links a version to its previous version
- **wasSnapshotOf** - Links a snapshot to the live RO it was created from
- **wasArchivedFrom** - Links an archive to the snapshot it was created from

### Temporal Properties

- **createdAtTime** - When a version was created
- **modifiedAtTime** - When a resource was last modified
- **archivedAtTime** - When a resource was archived

### Change Tracking Properties

- **hasChangeLog** - Links to a change log document
- **hasAdditions** - Resources added in this version
- **hasRemovals** - Resources removed in this version
- **hasModifications** - Resources modified in this version

## Usage Patterns

### Creating a Snapshot

```turtle
@prefix roevo: <http://purl.org/wf4ever/roevo#> .
@prefix ro: <http://purl.org/wf4ever/ro#> .
@prefix prov: <http://www.w3.org/ns/prov#> .

# Live research object
:myRO a roevo:LiveRO, ro:ResearchObject ;
    roevo:hasVersion :myRO-v1, :myRO-v2 .

# Snapshot created from live RO
:myRO-v1 a roevo:SnapshotRO, ro:ResearchObject ;
    roevo:wasSnapshotOf :myRO ;
    roevo:createdAtTime "2025-01-15T10:30:00Z"^^xsd:dateTime ;
    prov:wasRevisionOf :myRO-v0 .
```

### Tracking Evolution

```turtle
# Version 2 revised from version 1
:myRO-v2 a roevo:SnapshotRO ;
    roevo:wasSnapshotOf :myRO ;
    prov:wasRevisionOf :myRO-v1 ;
    roevo:createdAtTime "2025-02-20T14:00:00Z"^^xsd:dateTime ;
    roevo:hasChangeLog :changelog-v2 .

# Change specification
:changelog-v2 a roevo:ChangeSpecification ;
    roevo:hasAdditions :newWorkflow.cwl ;
    roevo:hasModifications :existingData.csv ;
    roevo:hasRemovals :oldScript.py .
```

### Archiving

```turtle
# Archived version for long-term preservation
:myRO-v1-archived a roevo:ArchivedRO ;
    roevo:wasArchivedFrom :myRO-v1 ;
    roevo:archivedAtTime "2025-12-31T23:59:59Z"^^xsd:dateTime ;
    roevo:archiveLocation <https://archive.example.org/ro/myRO-v1> .
```

## Integration with PROV-O

roevo uses PROV-O concepts to provide provenance of research object evolution:

- **prov:Entity** - Research objects and their versions are PROV entities
- **prov:wasRevisionOf** - Links between versions
- **prov:wasDerivedFrom** - Derivation relationships
- **prov:generatedAtTime** - When a version was created
- **prov:Agent** - Persons or organizations creating versions

## Lifecycle States

Research objects can transition through different lifecycle states:

1. **Draft/Live** (LiveRO) - Active development, can be modified
2. **Snapshot** (SnapshotRO) - Point-in-time immutable copy
3. **Archived** (ArchivedRO) - Long-term preservation copy

## Use Cases

### Scientific Reproducibility

Track different versions of experimental workflows and datasets to ensure reproducibility of scientific results.

### Collaborative Research

Enable multiple researchers to work on different versions of research objects while maintaining version history.

### Long-term Preservation

Create immutable archived versions for institutional repositories and digital preservation.

### Audit Trail

Maintain complete change history for compliance and quality assurance in regulated research domains.

## References

- [W3C PROV-O](https://www.w3.org/TR/prov-o/)
- [Research Object Ontology](http://purl.org/wf4ever/ro)
- [Wf4Ever Research Object Model](http://wf4ever.github.io/ro/)
