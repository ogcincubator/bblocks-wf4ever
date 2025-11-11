
# wf4ever:WebServiceProcess (Datatype)

`ogc.bbr.wf4ever.wf4ever.WebServiceProcess` *v1.0*

A web service process - a process description whose enactment involves making a web service call.

[*Status*](http://www.opengis.net/def/status): Under development

## Description

# wf4ever:WebServiceProcess

A process whose enactment involves making a web service call (e.g., OGC API Processes, WPS).

## Examples

### OGC API Processes Service
#### json
```json
{"@id": "#ndvi-service", "@type": "WebServiceProcess", "endpoint": "https://zoo-project.org/ogcapi/processes/ndvi", "method": "POST"}

```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
description: A web service process
type: object
properties:
  '@type':
    oneOf:
    - const: WebServiceProcess
    - type: array
      contains:
        const: WebServiceProcess
  endpoint:
    type: string
    format: uri
    description: Web service endpoint URL
  method:
    type: string
    description: HTTP method (GET, POST, etc.)
required:
- '@type'

```

Links to the schema:

* YAML version: [schema.yaml](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/WebServiceProcess/schema.json)
* JSON version: [schema.json](https://geolabs.github.io/bblocks-wf4ever/build/annotated/bbr/wf4ever/wf4ever/WebServiceProcess/schema.yaml)

## Sources

* [Wf4Ever Ontology - WebServiceProcess](http://purl.org/wf4ever/wf4ever#WebServiceProcess)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/GeoLabs/bblocks-wf4ever](https://github.com/GeoLabs/bblocks-wf4ever)
* Path: `_sources/wf4ever/WebServiceProcess`

