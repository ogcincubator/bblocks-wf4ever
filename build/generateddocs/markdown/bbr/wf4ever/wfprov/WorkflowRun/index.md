
# wfprov:WorkflowRun (Datatype)

`ogc.bbr.wf4ever.wfprov.WorkflowRun` *v1.0*

An execution instance of a workflow. A WorkflowRun is a special type of ProcessRun that represents the execution of a complete workflow (wfdesc:Workflow), containing multiple ProcessRuns for its sub-processes.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

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

## Examples

### Mangrove Workflow Run
#### json
```json
{
  "id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "@id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "type": "Activity",
  "@type": [
    "http://purl.org/wf4ever/wfprov#WorkflowRun",
    "http://www.w3.org/ns/prov#Activity"
  ],
  "http://www.w3.org/2000/01/rdf-schema#label": [
    {
      "@value": "Run of workflow/packed.cwl#main"
    }
  ],
  "http://www.w3.org/ns/prov#startedAtTime": [
    {
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime",
      "@value": "2025-11-03T15:14:02.032122"
    }
  ],
  "http://www.w3.org/ns/prov#endedAtTime": [
    {
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime",
      "@value": "2025-11-03T15:14:17.060218"
    }
  ],
  "http://www.w3.org/ns/prov#wasAssociatedWith": [
    {
      "@id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60"
    },
    {
      "@id": "urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f"
    }
  ],
  "http://purl.org/wf4ever/wfprov#describedByWorkflow": [
    {
      "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main"
    }
  ]
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/context.jsonld",
  "id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "@id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
  "type": "Activity",
  "@type": [
    "http://purl.org/wf4ever/wfprov#WorkflowRun",
    "http://www.w3.org/ns/prov#Activity"
  ],
  "http://www.w3.org/2000/01/rdf-schema#label": [
    {
      "@value": "Run of workflow/packed.cwl#main"
    }
  ],
  "http://www.w3.org/ns/prov#startedAtTime": [
    {
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime",
      "@value": "2025-11-03T15:14:02.032122"
    }
  ],
  "http://www.w3.org/ns/prov#endedAtTime": [
    {
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime",
      "@value": "2025-11-03T15:14:17.060218"
    }
  ],
  "http://www.w3.org/ns/prov#wasAssociatedWith": [
    {
      "@id": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60"
    },
    {
      "@id": "urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f"
    }
  ],
  "http://purl.org/wf4ever/wfprov#describedByWorkflow": [
    {
      "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main"
    }
  ]
}
```

#### ttl
```ttl
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix wfprov: <http://purl.org/wf4ever/wfprov#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c> a wfprov:WorkflowRun,
        prov:Activity ;
    rdfs:label "Run of workflow/packed.cwl#main" ;
    wfprov:describedByWorkflow <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/workflow/packed.cwl#main> ;
    prov:endedAtTime "2025-11-03T15:14:17.060218"^^xsd:dateTime ;
    prov:startedAtTime "2025-11-03T15:14:02.032122"^^xsd:dateTime ;
    prov:wasAssociatedWith <urn:uuid:2dee96f7-ed94-4ef7-8562-6f26cdecd46f>,
        <urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An execution instance of a workflow
allOf:
- $ref: https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/ProcessRun/schema.yaml
- type: object
  properties:
    describedByWorkflow:
      type: string
      format: uri
      description: Links to the workflow description (wfdesc:Workflow) that was executed
      x-jsonld-id: http://purl.org/wf4ever/wfprov#describedByWorkflow
      x-jsonld-type: '@id'
    http://purl.org/wf4ever/wfprov#describedByWorkflow:
      description: Workflow description in expanded form
      type: array
      items:
        type: object
    hadSubProcessRun:
      type: array
      items:
        type: object
        properties:
          id:
            type: string
            format: uri
        required:
        - id
      description: The process runs that were part of this workflow execution
      x-jsonld-reverse: wfprov:wasPartOfWorkflowRun
      x-jsonld-type: '@id'
      x-jsonld-container: '@set'
    wasEnactedBy:
      type: string
      format: uri
      description: The workflow engine that executed this workflow
      x-jsonld-id: http://www.w3.org/ns/prov#wasAssociatedWith
      x-jsonld-type: '@id'
  anyOf:
  - required:
    - describedByWorkflow
  - required:
    - http://purl.org/wf4ever/wfprov#describedByWorkflow
x-jsonld-extra-terms:
  WorkflowRun: http://purl.org/wf4ever/wfprov#WorkflowRun
x-jsonld-vocab: http://purl.org/wf4ever/wfprov#
x-jsonld-prefixes:
  wfprov: http://purl.org/wf4ever/wfprov#
  prov: http://www.w3.org/ns/prov#
  wfdesc: http://purl.org/wf4ever/wfdesc#

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/wfprov#",
    "wasInfluencedBy": {
      "@context": {
        "type": "dct:type"
      },
      "@id": "prov:wasInfluencedBy",
      "@type": "@id"
    },
    "qualifiedInfluence": {
      "@context": {
        "influencer": {
          "@context": {
            "type": "dct:type"
          },
          "@id": "prov:influencer",
          "@type": "@id"
        },
        "entity": {
          "@context": {
            "type": "dct:type"
          },
          "@id": "prov:entity",
          "@type": "@id"
        },
        "agent": {
          "@context": {
            "type": "dct:type"
          },
          "@id": "prov:agent",
          "@type": "@id"
        }
      },
      "@id": "prov:qualifiedInfluence",
      "@type": "@id"
    },
    "href": {
      "@type": "@id",
      "@id": "oa:hasTarget"
    },
    "rel": {
      "@context": {
        "@base": "http://www.iana.org/assignments/relation/"
      },
      "@id": "http://www.iana.org/assignments/relation",
      "@type": "@id"
    },
    "type": "@type",
    "hreflang": "dct:language",
    "title": "rdfs:label",
    "length": "dct:extent",
    "ProcessRun": "wfprov:ProcessRun",
    "WorkflowRun": "wfprov:WorkflowRun",
    "wasOutputFrom": {
      "@id": "prov:generated",
      "@type": "@id",
      "@container": "@set"
    },
    "id": "@id",
    "describedByProcess": {
      "@id": "wfprov:describedByProcess",
      "@type": "@id"
    },
    "usedInput": {
      "@id": "wfprov:usedInput",
      "@type": "@id",
      "@container": "@set"
    },
    "startedAtTime": {
      "@id": "prov:startedAtTime",
      "@type": "xsd:dateTime"
    },
    "endedAtTime": {
      "@id": "prov:endedAtTime",
      "@type": "xsd:dateTime"
    },
    "wasPartOfWorkflowRun": {
      "@id": "wfprov:wasPartOfWorkflowRun",
      "@type": "@id"
    },
    "wasEnactedBy": {
      "@id": "prov:wasAssociatedWith",
      "@type": "@id"
    },
    "describedByWorkflow": {
      "@id": "wfprov:describedByWorkflow",
      "@type": "@id"
    },
    "hadSubProcessRun": {
      "@reverse": "wfprov:wasPartOfWorkflowRun",
      "@type": "@id",
      "@container": "@set"
    },
    "activityType": "@type",
    "agentType": "@type",
    "entityType": "@type",
    "featureType": "@type",
    "provType": "@type",
    "Activity": "prov:Activity",
    "ActivityInfluence": "prov:ActivityInfluence",
    "Agent": "prov:Agent",
    "AgentInfluence": "prov:AgentInfluence",
    "Association": "prov:Association",
    "Attribution": "prov:Attribution",
    "Bundle": "prov:Bundle",
    "Collection": "prov:Collection",
    "Communication": "prov:Communication",
    "Delegation": "prov:Delegation",
    "Derivation": "prov:Derivation",
    "EmptyCollection": "prov:EmptyCollection",
    "End": "prov:End",
    "Entity": "prov:Entity",
    "EntityInfluence": "prov:EntityInfluence",
    "Generation": "prov:Generation",
    "Influence": "prov:Influence",
    "InstantaneousEvent": "prov:InstantaneousEvent",
    "Invalidation": "prov:Invalidation",
    "Location": "prov:Location",
    "Organization": "prov:Organization",
    "Person": "prov:Person",
    "Plan": "prov:Plan",
    "PrimarySource": "prov:PrimarySource",
    "Quotation": "prov:Quotation",
    "Revision": "prov:Revision",
    "Role": "prov:Role",
    "SoftwareAgent": "prov:SoftwareAgent",
    "Start": "prov:Start",
    "Usage": "prov:Usage",
    "ServiceDescription": "prov:ServiceDescription",
    "DirectQueryService": "prov:DirectQueryService",
    "Accept": "prov:Accept",
    "Contribute": "prov:Contribute",
    "Contributor": "prov:Contributor",
    "Copyright": "prov:Copyright",
    "Create": "prov:Create",
    "Creator": "prov:Creator",
    "Modify": "prov:Modify",
    "Publish": "prov:Publish",
    "Publisher": "prov:Publisher",
    "Replace": "prov:Replace",
    "RightsAssignment": "prov:RightsAssignment",
    "RightsHolder": "prov:RightsHolder",
    "Submit": "prov:Submit",
    "Dictionary": "prov:Dictionary",
    "EmptyDictionary": "prov:EmptyDictionary",
    "KeyEntityPair": "prov:KeyEntityPair",
    "Insertion": "prov:Insertion",
    "Removal": "prov:Removal",
    "atTime": {
      "@id": "prov:atTime",
      "@type": "xsd:dateTime"
    },
    "generatedAtTime": {
      "@id": "prov:generatedAtTime",
      "@type": "xsd:dateTime"
    },
    "invalidatedAtTime": {
      "@id": "prov:invalidatedAtTime",
      "@type": "xsd:dateTime"
    },
    "value": "prov:value",
    "provenanceUriTemplate": "prov:provenanceUriTemplate",
    "pairKey": {
      "@id": "prov:pairKey",
      "@type": "rdfs:Literal"
    },
    "removedKey": {
      "@id": "prov:removedKey",
      "@type": "rdfs:Literal"
    },
    "actedOnBehalfOf": {
      "@id": "prov:actedOnBehalfOf",
      "@type": "@id"
    },
    "agent": {
      "@id": "prov:agent",
      "@type": "@id"
    },
    "alternateOf": {
      "@id": "prov:alternateOf",
      "@type": "@id"
    },
    "atLocation": {
      "@id": "prov:atLocation",
      "@type": "@id"
    },
    "entity": {
      "@id": "prov:entity",
      "@type": "@id"
    },
    "generated": {
      "@id": "prov:generated",
      "@type": "@id"
    },
    "hadActivity": {
      "@id": "prov:hadActivity",
      "@type": "@id"
    },
    "activity": {
      "@id": "prov:activity",
      "@type": "@id"
    },
    "hadGeneration": {
      "@id": "prov:hadGeneration",
      "@type": "@id"
    },
    "hadMember": {
      "@id": "prov:hadMember",
      "@type": "@id"
    },
    "hadPlan": {
      "@id": "prov:hadPlan",
      "@type": "@id"
    },
    "hadPrimarySource": {
      "@id": "prov:hadPrimarySource",
      "@type": "@id"
    },
    "hadRole": {
      "@id": "prov:hadRole",
      "@type": "@id"
    },
    "hadUsage": {
      "@id": "prov:hadUsage",
      "@type": "@id"
    },
    "influenced": {
      "@id": "prov:influenced",
      "@type": "@id"
    },
    "influencer": {
      "@id": "prov:influencer",
      "@type": "@id"
    },
    "invalidated": {
      "@id": "prov:invalidated",
      "@type": "@id"
    },
    "qualifiedAssociation": {
      "@id": "prov:qualifiedAssociation",
      "@type": "@id"
    },
    "qualifiedAttribution": {
      "@id": "prov:qualifiedAttribution",
      "@type": "@id"
    },
    "qualifiedCommunication": {
      "@id": "prov:qualifiedCommunication",
      "@type": "@id"
    },
    "qualifiedDelegation": {
      "@id": "prov:qualifiedDelegation",
      "@type": "@id"
    },
    "qualifiedDerivation": {
      "@id": "prov:qualifiedDerivation",
      "@type": "@id"
    },
    "qualifiedEnd": {
      "@id": "prov:qualifiedEnd",
      "@type": "@id"
    },
    "qualifiedGeneration": {
      "@id": "prov:qualifiedGeneration",
      "@type": "@id"
    },
    "qualifiedInvalidation": {
      "@id": "prov:qualifiedInvalidation",
      "@type": "@id"
    },
    "qualifiedPrimarySource": {
      "@id": "prov:qualifiedPrimarySource",
      "@type": "@id"
    },
    "qualifiedQuotation": {
      "@id": "prov:qualifiedQuotation",
      "@type": "@id"
    },
    "qualifiedRevision": {
      "@id": "prov:qualifiedRevision",
      "@type": "@id"
    },
    "qualifiedStart": {
      "@id": "prov:qualifiedStart",
      "@type": "@id"
    },
    "qualifiedUsage": {
      "@id": "prov:qualifiedUsage",
      "@type": "@id"
    },
    "specializationOf": {
      "@id": "prov:specializationOf",
      "@type": "@id"
    },
    "used": {
      "@id": "prov:used",
      "@type": "@id"
    },
    "wasAssociatedWith": {
      "@id": "prov:wasAssociatedWith",
      "@type": "@id"
    },
    "wasAttributedTo": {
      "@id": "prov:wasAttributedTo",
      "@type": "@id"
    },
    "wasDerivedFrom": {
      "@id": "prov:wasDerivedFrom",
      "@type": "@id"
    },
    "wasEndedBy": {
      "@id": "prov:wasEndedBy",
      "@type": "@id"
    },
    "wasGeneratedBy": {
      "@id": "prov:wasGeneratedBy",
      "@type": "@id"
    },
    "wasInformedBy": {
      "@id": "prov:wasInformedBy",
      "@type": "@id"
    },
    "wasInvalidatedBy": {
      "@id": "prov:wasInvalidatedBy",
      "@type": "@id"
    },
    "wasQuotedFrom": {
      "@id": "prov:wasQuotedFrom",
      "@type": "@id"
    },
    "wasRevisionOf": {
      "@id": "prov:wasRevisionOf",
      "@type": "@id"
    },
    "wasStartedBy": {
      "@id": "prov:wasStartedBy",
      "@type": "@id"
    },
    "has_anchor": {
      "@id": "prov:has_anchor",
      "@type": "@id"
    },
    "has_provenance": {
      "@id": "dct:provenance",
      "@type": "@id"
    },
    "has_query_service": {
      "@id": "prov:has_query_service",
      "@type": "@id"
    },
    "describesService": {
      "@id": "prov:describesService",
      "@type": "@id"
    },
    "pingback": {
      "@id": "prov:pingback",
      "@type": "@id"
    },
    "dictionary": {
      "@id": "prov:dictionary",
      "@type": "@id"
    },
    "derivedByInsertionFrom": {
      "@id": "prov:derivedByInsertionFrom",
      "@type": "@id"
    },
    "derivedByRemovalFrom": {
      "@id": "prov:derivedByRemovalFrom",
      "@type": "@id"
    },
    "insertedKeyEntityPair": {
      "@id": "prov:insertedKeyEntityPair",
      "@type": "@id"
    },
    "hadDictionaryMember": {
      "@id": "prov:hadDictionaryMember",
      "@type": "@id"
    },
    "pairEntity": {
      "@id": "prov:pairEntity",
      "@type": "@id"
    },
    "qualifiedInsertion": {
      "@id": "prov:qualifiedInsertion",
      "@type": "@id"
    },
    "qualifiedRemoval": {
      "@id": "prov:qualifiedRemoval",
      "@type": "@id"
    },
    "asInBundle": {
      "@id": "prov:asInBundle",
      "@type": "@id"
    },
    "mentionOf": {
      "@id": "prov:mentionOf",
      "@type": "@id"
    },
    "name": "rdfs:label",
    "links": "rdfs:seeAlso",
    "prov": "http://www.w3.org/ns/prov#",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "dct": "http://purl.org/dc/terms/",
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "oa": "http://www.w3.org/ns/oa#",
    "wfprov": "http://purl.org/wf4ever/wfprov#",
    "wfdesc": "http://purl.org/wf4ever/wfdesc#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wfprov/WorkflowRun/context.jsonld)

## Sources

* [Workflow Provenance Ontology - WorkflowRun](http://purl.org/wf4ever/wfprov#WorkflowRun)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wfprov/WorkflowRun`

