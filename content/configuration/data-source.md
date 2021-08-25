---
uid: PIAdapterForOPCUADataSourceConfiguration
---

# Data source

To use the adapter, you must configure the data source from which it polls data.

## Configure OPC UA data source

Complete the following steps to configure an OPC UA data source. Use the `PUT` method in conjunction with the `api/v1/configuration/<ComponentId>/DataSource` REST endpoint to initialize the configuration.

1. Using a text editor, create an empty text file.

2. Copy and paste an example configuration for an OPC UA data source into the file.

    For sample JSON, see [OPC UA data source examples](#opc-ua-data-source-examples).

3. Update the example JSON parameters for your environment.

    For a table of all available parameters, see [OPC UA data source parameters](#opc-ua-data-source-parameters).

4. Save the file. For example, as `ConfigureDataSource.json`.

5. Open a command line session. Change directory to the location of `ConfigureDataSource.json`.

6. Enter the following cURL command (which uses the `PUT` method) to initialize the data source configuration.

    ```bash
    curl -d "@ConfigureDataSource.json" -H "Content-Type: application/json" -X PUT "http://localhost:5590/api/v1/configuration/OpcUa1/DataSource"
    ```

    **Notes:**
  
    * If you installed the adapter to listen on a non-default port, update `5590` to the port number in use.
    * If you use a component ID other than `OpcUa1`, update the endpoint with your chosen component ID.
    * For a list of other REST operations you can perform, like updating or deleting a data source configuration, see [REST URLs](#rest-urls).
    <br/>
    <br/>

7. Configure data selection.

    For more information, see [PI Adapter for OPC UA data selection configuration](xref:PIAdapterForOPCUADataSelectionConfiguration).

## OPC UA data source schema

The full schema definition for the OPC UA data source configuration is in the `OpcUa_DataSource_schema.json` file located in one of the following folders:

Windows: `%ProgramFiles%\OSIsoft\Adapters\OpcUa\Schemas`

Linux: `/opt/OSIsoft/Adapters/OpcUa/Schemas`

## OPC UA data source parameters

The following parameters are available for configuring an OPC UA data source:

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| **EndpointURL** | Required | `string` | The endpoint URL of the OPC UA server in opc.tcp format. The following is an example of the URL format: opc.tcp://OPCServerHost:Port/OpcUa/SimulationServer<br><br>**Note:** If you change the EndpointURL on a configured adapter that has _ComponentID_DataSelection_ .json file exported, you need to remove the _ComponentID_DataSelection.json_ file from the configuration directory to trigger a new browse (export). <br><br>Allowed value: well-formed opc.tcp address|
| **UseSecureConnection**|Optional | `boolean` | When set to true, the adapter connects to a secure endpoint using OPC UA certificate exchange operation. The default is true. When set to false, the adapter connects to an unsecured endpoint of the server and certificate exchange operation is not required.<br><br>**Note:** OSIsoft recommends setting this option to false for testing purposes only. <br><br> Allowed value: `true` or `false`<br>Default value: `true`|
| **UserName** | Optional | `string` | User name for accessing the OPC UA server. <br><br>Allowed value: any string <br> Default value: `null`|
| **Password** | Optional | `string` | Password for accessing the OPC UA server.<br><br>**Note:** OSIsoft recommends using REST to configure the data source when the password must be specified because REST will encrypt the password. If you do not use REST, the plain text password will be stored on-disk. <br><br>Allowed value: any string <br> Default value: `null`|
| **RootNodeIds** | Optional | `string` | List of comma-separated NodeIds of those objects from which the adapter browses the OPC UA server address space. This option allows to select only subsets of the OPC UA address by explicitly listing one or more NodeIds which are used to start the initial browse.<br><br>Examples:<br>`"ns=5;s=85/0:Simulation"`<br>`"ns=3;s=DataItems"`<br><br>If not specified, it means that the whole address space will be browsed. <br><br>Allowed value: comma-separated collection of node Ids<br> Default value: `null`|
| **IncomingTimestamp** | Optional | `string` | Specifies whether the incoming timestamp is taken from the source, from the OPC UA server, or should be created by the adapter instance. <br> **Source** - Default and recommended setting. The timestamp is taken from the source timestamp field. The source is what provides data for the item to the OPC UA server, such as a field device.<br> **Server** - In case the OPC UA item has an invalid source timestamp field, the Server timestamp can be used.<br> **Adapter** - The adapter generates a timestamp for the item upon receiving it from the OPC UA server. <br><br>Allowed value: `Source`, `Server`, or `Adapter` <br> Default value: `Source`|
| **StreamIdPrefix** | Optional | `string` | Specifies what prefix is used for Stream IDs. The naming convention is `{StreamIdPrefix}{StreamId}`. An empty string means no prefix will be added to the Stream IDs and names. A `null` value defaults to _ComponentID_ followed by a period.<br><br>Example: `OpcUa1.{NamespaceIndex}.{Identifier}`<br><br>**Note:** Every time you change the StreamIdPrefix of a configured adapter, for example when you delete and add a data source, you need to restart the adapter for the changes to take place. New streams are created on adapter restart and pre-existing streams are no longer updated. <br><br>Allowed value: any string <br> Default value: `null`|
| **DefaultStreamIdPattern** | Optional | `string` | Specifies the default stream Id pattern to use. Possible parameters: `{NamespaceIndex}`<sup>1</sup>, `{Identifier}`. <br><br>Allowed value: any string<br>Default value: `{NamespaceIndex}.{Identifier}` |

<sup>1</sup> NamespaceIndex refers to the number specified in the `ns` keyword in the **RootNodeIds** parameter.

## OPC UA data source examples

The following are examples of valid OPC UA data source configurations:

### Minimal data source configuration

```json
{
    "EndpointUrl": "opc.tcp://<IP-Address>:<Port>/<TestOPCUAServer>"
}
```

### Complete data source configuration

```json
{
    "EndpointUrl": "opc.tcp://<IP-Address>:<Port>/<TestOPCUAServer>",
    "UseSecureConnection": true,
    "UserName": null,
    "Password": null,
    "RootNodeIds": null,
    "IncomingTimestamp": "Source",
    "StreamIdPrefix": null,
    "DefaultStreamIdPattern": "{NamespaceIndex}.{Identifier}"
}
```

## REST URLs

| Relative URL | HTTP verb | Action |
| ------------ | --------- | ------ |
| api/v1/configuration/_ComponentId_/DataSource  | GET | Retrieves the OPC UA data source configuration |
| api/v1/configuration/_ComponentId_/DataSource  | POST | Creates the OPC UA data source configuration |
| api/v1/configuration/_ComponentId_/DataSource  | PUT | Configures or updates the OPC UA data source configuration |
| api/v1/configuration/_ComponentId_/DataSource | DELETE | Deletes the OPC UA data source configuration |

**Note:** Replace _ComponentId_ with the Id of your OPC UA component, for example OpcUa1.
