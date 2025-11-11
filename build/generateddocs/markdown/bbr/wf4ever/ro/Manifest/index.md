
# ro:Manifest (Datatype)

`ogc.bbr.wf4ever.ro.Manifest` *v1.0*

A manifest that describes the structure and contents of a Research Object. The manifest provides metadata about the Research Object, its aggregated resources, annotations, and organizational structure.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# ro:Manifest

## Description

A **Manifest** describes the structure and content of a Research Object. The manifest provides metadata about the Research Object, its aggregated resources, annotations, and organizational structure.

## Relations

- Describes a `ro:ResearchObject` via `ore:describes`
- Created by an agent (person or system) via `dcterms:creator`

## Examples

### Simple manifest
#### json
```json
{
  "@id": ".ro/manifest.json",
  "@type": "Manifest",
  "describes": "../",
  "createdBy": "https://orcid.org/0000-0001-2345-6789",
  "createdOn": "2025-11-07T10:00:00Z"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Manifest/context.jsonld",
  "@id": ".ro/manifest.json",
  "@type": "Manifest",
  "describes": "../",
  "createdBy": "https://orcid.org/0000-0001-2345-6789",
  "createdOn": "2025-11-07T10:00:00Z"
}
```

#### ttl
```ttl
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ore: <http://www.openarchives.org/ore/terms/> .
@prefix ro: <http://purl.org/wf4ever/ro#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<file:///github/workspace/.ro/manifest.json> a ro:Manifest ;
    dcterms:created "2025-11-07T10:00:00+00:00"^^xsd:dateTime ;
    dcterms:creator <https://orcid.org/0000-0001-2345-6789> ;
    ore:describes <file:///github/> .


```


### KindGrove Research Object Manifest
#### json
```json
{
  "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/manifest.json",
  "@type": "Manifest",
  "describes": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/",
  "conformsTo": "https://w3id.org/cwl/prov/0.6.0",
  "createdOn": "2025-11-03T15:14:17.166945",
  "createdBy": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Manifest/context.jsonld",
  "@id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/manifest.json",
  "@type": "Manifest",
  "describes": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/",
  "conformsTo": "https://w3id.org/cwl/prov/0.6.0",
  "createdOn": "2025-11-03T15:14:17.166945",
  "createdBy": "urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60"
}
```

#### ttl
```ttl
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ore: <http://www.openarchives.org/ore/terms/> .
@prefix ro: <http://purl.org/wf4ever/ro#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/metadata/manifest.json> a ro:Manifest ;
    dcterms:created "2025-11-03T15:14:17.166945"^^xsd:dateTime ;
    dcterms:creator <urn:uuid:5b925446-32a4-4104-9724-fa7360e1ef60> ;
    ro:conformsTo "https://w3id.org/cwl/prov/0.6.0" ;
    ore:describes <arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/> .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A manifest describing a Research Object
type: object
properties:
  '@id':
    type: string
    format: uri
    description: Unique identifier for the manifest
  '@type':
    const: Manifest
    description: Type must be Manifest
  describes:
    type: string
    format: uri
    description: The Research Object that this manifest describes
    x-jsonld-id: http://www.openarchives.org/ore/terms/describes
    x-jsonld-type: '@id'
  createdBy:
    type: string
    format: uri
    description: Agent that created this manifest
    x-jsonld-id: http://purl.org/dc/terms/creator
    x-jsonld-type: '@id'
  createdOn:
    type: string
    format: date-time
    description: Creation date of the manifest
    x-jsonld-id: http://purl.org/dc/terms/created
    x-jsonld-type: http://www.w3.org/2001/XMLSchema#dateTime
required:
- '@id'
- '@type'
- describes
x-jsonld-extra-terms:
  Manifest: http://purl.org/wf4ever/ro#Manifest
x-jsonld-vocab: http://purl.org/wf4ever/ro#
x-jsonld-prefixes:
  ro: http://purl.org/wf4ever/ro#
  ore: http://www.openarchives.org/ore/terms/
  dcterms: http://purl.org/dc/terms/

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Manifest/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Manifest/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/ro#",
    "Manifest": "ro:Manifest",
    "describes": {
      "@id": "ore:describes",
      "@type": "@id"
    },
    "createdBy": {
      "@id": "dcterms:creator",
      "@type": "@id"
    },
    "createdOn": {
      "@id": "dcterms:created",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    },
    "ro": "http://purl.org/wf4ever/ro#",
    "ore": "http://www.openarchives.org/ore/terms/",
    "dcterms": "http://purl.org/dc/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/Manifest/context.jsonld)

## Sources

* [Research Object Ontology - Manifest](http://purl.org/wf4ever/ro#Manifest)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/ro/Manifest`

