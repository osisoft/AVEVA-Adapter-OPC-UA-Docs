### Data types

The following table lists OPC UA variable types that the adapter collects data from and types of streams that will be created.

| OPC UA data type | Stream data type |
|------------------|------------------|
| Boolean          | Boolean          |
| SByte            | Int16            |
| Int16            | Int16            |
| UInt16           | UInt16           |
| Int32            | Int32            |
| UInt32           | UInt32           |
| Int64            | Int64            |
| UInt64           | UInt64           |
| Double           | Float64          |
| Decimal          | Float32          |  
| Float            | Float32          |
| DateTime         | DateTime         |
| String           | String           |
| Number           | variable, depending on the actual value |
| Integer          | Integer          |
| UInteger         | UInteger         |
| Enumeration      | Int16            |

PI Adapter for OPC UA attempts to verify the data type for each data selection item before adding the item to the subscription on the OPC UA server. Data selection items with supported types and data selection items for which the type cannot be verified, are added to the subscription too. Data selection items with unsupported data type are not added to the subscription and a message including the **NodeId** and **TypeId** is logged.