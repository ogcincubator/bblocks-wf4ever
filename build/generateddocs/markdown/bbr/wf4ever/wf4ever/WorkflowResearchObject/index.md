
# wf4ever:WorkflowResearchObject (Datatype)

`ogc.bbr.wf4ever.wf4ever.WorkflowResearchObject` *v1.0*

A research object that aggregates at least one workflow description, along with associated resources and provenance.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wf4ever:WorkflowResearchObject

A research object that aggregates at least one workflow description.

## Examples

### KindGrove Workflow Research Object
#### json
```json
{
    "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/",
    "@type": "WorkflowResearchObject",
    "aggregates": [
        {
            "@id": "workflow/packed.cwl#main",
            "@type": "Workflow"
        }
    ]
}

```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A workflow research object
type: object
properties:
  '@type':
    oneOf:
    - const: WorkflowResearchObject
    - type: array
      contains:
        const: WorkflowResearchObject
  aggregates:
    type: array
    description: Must include at least one workflow
    contains:
      type: object
      properties:
        '@type':
          const: Workflow
required:
- '@type'
- aggregates

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/WorkflowResearchObject/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/WorkflowResearchObject/schema.yaml)

## Sources

* [Wf4Ever Ontology - WorkflowResearchObject](http://purl.org/wf4ever/wf4ever#WorkflowResearchObject)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wf4ever/WorkflowResearchObject`

