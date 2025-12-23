
# wf4ever:WorkflowResearchObject (Datatype)

`ogc.bbr.wf4ever.wf4ever.WorkflowResearchObject` *v1.0*

A research object that aggregates at least one workflow description, along with associated resources and provenance.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wf4ever:WorkflowResearchObject

A research object that aggregates at least one workflow description.

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

* YAML version: [schema.yaml](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/WorkflowResearchObject/schema.json)
* JSON version: [schema.json](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/WorkflowResearchObject/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@type": {
      "@context": {}
    },
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://ogcincubator.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/WorkflowResearchObject/context.jsonld)

## Sources

* [Wf4Ever Ontology - WorkflowResearchObject](http://purl.org/wf4ever/wf4ever#WorkflowResearchObject)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-wf4ever](https://github.com/ogcincubator/bblocks-wf4ever)
* Path: `_sources/wf4ever/WorkflowResearchObject`

