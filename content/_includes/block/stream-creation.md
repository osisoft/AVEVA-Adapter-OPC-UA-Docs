## Stream creation

The OPC UA adapter creates a stream with three properties for each selected OPC UA item. The properties are described in the following table:

| Property name | Data type | Description |
|---------------|-----------|-------------|
| Timestamp     | DateTime  | Timestamp of the given OPC UA item value update. |
| Value         | Based on type of incoming OPC UA value | Value of the given OPC UA item update, which includes multiple properties in addition to the data value.<br><br>**Note:**<br>For OPC UA items that support EURange, the additional **Minimum**/**Maximum** properties in OCS and the **Zero**/**Span** properties in PI Web API are populated.<br>For OPC UA items that support EngineeringUnits, such as AnalogItem, the additional **UOM** property in OCS and the **Eng Units** property in PI Web API are populated.<sup>1</sup>  |
| Quality | Unsigned integer | Data quality of the given OPC UA item update.  |

<sup>1</sup> **Note:** `Null` values with `Good` quality are discarded. `Null` values with `Bad` or `Questionable` quality send the default value `0` or `null` to the destination.

The OPC UA adapter sends metadata with each stream it creates. Metadata common for every adapter type are:

- **ComponentId**: Specifies the data source, for example _OpcUa1_
- **ComponentType**: Specifies the type of adapter, for example _OpcUa_

Metadata specific to the OPC UA adapter are

- **BrowseName**: The browse name as provided by the OPC UA server
- **SourceId**: The NodeId provided by the OPC UA server

**Note:** A configured metadata level allows you to set the amount of metadata for the adapter. Specify the metadata level in the [General configuration](xref:GeneralConfiguration). For the OPC UA adapter, the following metadata is sent for the individual level:

- `None`: No metadata
- `Low`: AdapterType (ComponentType) and DataSource (ComponentId)
- `Medium`: AdapterType (ComponentType), DataSource (ComponentId), BrowseName, and DisplayName
- `High`: AdapterType (ComponentType), DataSource (ComponentId), BrowseName, DisplayName, and SourceId

Each stream created by  the adapter for a given OPC UA item has a unique identifier (Stream ID). If you specify a custom stream ID for the OPC UA item in data selection configuration, the OPC UA adapter uses that stream ID to create the stream. Otherwise, the adapter constructs the stream ID using the following format, which is constructed from the OPC UA item node ID:

```code
<AdapterComponentID>.<NamespaceIndex>.<Identifier>
```
NamespaceIndex refers to the number specified in the `ns` keyword in the **NodeId** parameter of the data selection configuration item. For more information, see [PI Adapter for OPC UA data source configuration](xref:PIAdapterForOPCUADataSourceConfiguration#opc-ua-data-source-parameters).

**Note:** The naming convention is affected by StreamPrefix and DefaultStreamIdPattern settings in the data source configuration.
