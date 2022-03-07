## Enumeration types

PI Adapter for OPC UA supports the following enumeration types:

- MultiStateDiscreteType
- MultiStateValueDiscreteType
- TwoStateDiscreteType
- Any object that has a data type referenced as enumeration type

The adapter reads the enumeration mapping for data selection items that point to any of the enumeration types and sends these items as enums to the OMF endpoints.