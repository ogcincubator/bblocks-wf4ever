
# ro:FolderEntry (Datatype)

`ogc.bbr.wf4ever.ro.FolderEntry` *v1.0*

An entry within a folder that associates a name with a resource. FolderEntries provide the mapping between folder paths and actual resources, similar to filesystem directory entries.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# ro:FolderEntry

## Description

A **FolderEntry** is an entry in a folder that maps a name to a resource. FolderEntries provide the mapping between folder paths and actual resources, similar to file system directory entries.

## Relations

- Contained in a `ro:Folder` (via inverse of `ro:hasEntry`)
- Represents a `ro:Resource` via `ore:proxyFor`

## Examples

### Workflow entry
#### json
```json
{
  "@id": "workflow/.ro/entry-ndvi-cwl",
  "@type": "FolderEntry",
  "entryName": "ndvi.cwl",
  "proxyFor": "workflow/ndvi.cwl"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/FolderEntry/context.jsonld",
  "@id": "workflow/.ro/entry-ndvi-cwl",
  "@type": "FolderEntry",
  "entryName": "ndvi.cwl",
  "proxyFor": "workflow/ndvi.cwl"
}
```

#### ttl
```ttl
@prefix ore: <http://www.openarchives.org/ore/terms/> .
@prefix ro: <http://purl.org/wf4ever/ro#> .

<file:///github/workspace/workflow/.ro/entry-ndvi-cwl> a ro:FolderEntry ;
    ro:entryName "ndvi.cwl" ;
    ore:proxyFor <file:///github/workspace/workflow/ndvi.cwl> .


```


### Output data entry
#### json
```json
{
  "@id": "data/.ro/entry-output",
  "@type": "FolderEntry",
  "entryName": "ndvi_result.tif",
  "proxyFor": "data/output/ndvi_result.tif"
}

```

#### jsonld
```jsonld
{
  "@context": "https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/FolderEntry/context.jsonld",
  "@id": "data/.ro/entry-output",
  "@type": "FolderEntry",
  "entryName": "ndvi_result.tif",
  "proxyFor": "data/output/ndvi_result.tif"
}
```

#### ttl
```ttl
@prefix ore: <http://www.openarchives.org/ore/terms/> .
@prefix ro: <http://purl.org/wf4ever/ro#> .

<file:///github/workspace/data/.ro/entry-output> a ro:FolderEntry ;
    ro:entryName "ndvi_result.tif" ;
    ore:proxyFor <file:///github/workspace/data/output/ndvi_result.tif> .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: An entry within a folder associating a name with a resource
type: object
properties:
  '@id':
    type: string
    format: uri
    description: Unique identifier for the folder entry
  '@type':
    const: FolderEntry
    description: Type must be FolderEntry
  entryName:
    type: string
    description: Name of this entry within the folder
    x-jsonld-id: http://purl.org/wf4ever/ro#entryName
  proxyFor:
    type: string
    format: uri
    description: The resource that this entry represents
    x-jsonld-id: http://www.openarchives.org/ore/terms/proxyFor
    x-jsonld-type: '@id'
required:
- '@id'
- '@type'
- entryName
- proxyFor
x-jsonld-extra-terms:
  FolderEntry: http://purl.org/wf4ever/ro#FolderEntry
x-jsonld-vocab: http://purl.org/wf4ever/ro#
x-jsonld-prefixes:
  ro: http://purl.org/wf4ever/ro#
  ore: http://www.openarchives.org/ore/terms/

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/FolderEntry/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/FolderEntry/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "@vocab": "http://purl.org/wf4ever/ro#",
    "FolderEntry": "ro:FolderEntry",
    "entryName": "ro:entryName",
    "proxyFor": {
      "@id": "ore:proxyFor",
      "@type": "@id"
    },
    "ro": "http://purl.org/wf4ever/ro#",
    "ore": "http://www.openarchives.org/ore/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/ro/FolderEntry/context.jsonld)

## Sources

* [Research Object Ontology - FolderEntry](http://purl.org/wf4ever/ro#FolderEntry)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/ro/FolderEntry`

