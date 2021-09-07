---
uid: DataSourceDiscovery
---

# Data source discovery

A discovery against the data source of an OPC UA adapter allows you to specify the optional **query** parameter. The discovery query limits the number of objects to browse.

**Note:** Only one discovery at a time is supported.

## Query string

The string of the **query** parameter must contain string items in the following form: <br>`RootNodeIds=<nodeId>`<br><br>
| String item      | Required | Description |
|------------------|----------|-------------|
| **RootNodeIds**  | Optional |  The node Ids that the adapter will subscribe to when the discovery is posted.<br>**Note:** To specify multiple node IDs in the query, separate the node IDs with a comma. If **RootNodeIds** is not specified, the adapter subscribes to all topics. |

<br>**Note:** A NodeId is a unique identification on the OPC UA server that consists of namespace index and identifier.

### Query rules

The following rules apply for specifying the query string:

- Multiple comma-separated nodeIds are supported.
- The nodeId specified in the query string must be valid.
- `RootNodeIds=` must be followed by a nodeId.
- Empty string and all white spaces string is equivalent to no query specified.
- White spaces in the `RooteNodeIds=` section of the query are not supported

**Note:** The data source might contain large amounts of items. Use the root nodeIds in the query string to browse only items that you need.

## Discovery query example

The query parameter of the OPC UA component must be specified as shown in this example:
`RootNodeIds=ns=4;s=Boilers, ns=4;s=Pumps`.

### Data source discovery initiation

```json
{
	"id" : "SampleA",
	"query" : "RootNodeIds=ns=6;s=MyDevice"
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