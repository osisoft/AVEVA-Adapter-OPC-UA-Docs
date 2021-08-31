---
uid: DataSourceDiscovery
---

# Data source discovery

A discovery against the data source of an OPC UA adapter allows you to specify the optional **query** parameter. The query discovers the contents of the data source and narrows down the scope of the discovery. You can add the discovered items to the data selection.

**Note:** Only one discovery at a time is supported.

## Query string

The string of the **query** parameter must contain string items in the following form: <br>`ns=<NamespaceIndex>;<IdentifierType>=<Identifer>`<br><br>

| String item      | Required | Description |
|------------------|----------|-------------|
| **NamespaceIndex**       | Optional |  <!-- Needs a description -->
| **Identifier** | Optional | <!-- Needs a description -->

### Query rules

The following rules apply for specifying the query string:

- Only one query at a time is supported. That query can contain as many topics with the same wait time as needed. If you need different wait times for different topics, you need to create a new query once the query from the previous discovery has completed.
- Partial queries are terminated by a multi-level wildcard (`#`).
- A query cannot be terminated by a trailing slash (`/`).
- A query cannot start with a leading slash (`/`) or `$`.
- Topics are case sensitive.
- White spaces are supported.

**Note:** The data source might contain tens of thousands of metrics. Use the `#` judiciously and narrow down the query string to something specific or break down the query into different discoveries.

#### Wildcards

Wildcards are allowed in the query with the following specifications:

- A single-level wildcard replaces one topic level and is indicated by `+`.
- A multi-level wildcard covers many topic levels and is indicated by `#`.
- Wildcards can be combined.
- `#` must not be used more than once and can only be used at the end of the topic.
- No query, an empty string, or `null` as the query parameter is equivalent to `#`.

## Discovery query example

The query parameter of the OPC UA component must be specified in the following form:
`ns=<NamespaceIndex>;<IdentifierType>=<Identifer>`.

### Data source discovery initiation

```json
{
	"id" : "SampleA",
	"query" : "ns=6;s=MyDevice"
}
```

### Data source discovery results

```json
[
    {
	    "id": "SampleA",
	    "query": "ns=6;s=MyDevice",
	    "startTime": "2020-12-14T14:19:01.4383791-08:00",
	    "endTime": "2020-12-14T14:19:31.8549164-08:00",
	    "progress": 30,
	    "itemsFound": 700,
	    "newItems": 200,
	    "resultUri": "http://127.0.0.1:5590/api/v1/Configuration/OpcUaComponentId/Discoveries/40/result",
	    "autoSelect": false,
	    "status": "Complete",
	    "errors": null
	}
]
```

### OPC UA discovered selection items

```json
[
 {
    "Selected": true,
    "Name": "CustomStreamName",
    "NodeId": "ns=5;s=Random1",
    "StreamId": "CustomStreamName"
  },
  {
    "Selected": true,
    "Name": "5.Sinusoid1",
    "NodeId": "ns=5;s=Sinusoid1",
    "StreamId": null
  }
]
```