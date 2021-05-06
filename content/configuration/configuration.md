---
uid: OPCUAConfiguration
---

# Configuration

PI Adapter for OPC UA enables you to configure data source and data selection. The adapter also provides the ability to configure security and to generate a data selection file instead of manual configuration.

The examples in the configuration topics use `curl`, a commonly available tool on both Windows and Linux. The adapter can be configured with any programming language or tool that supports making REST calls, or with the EdgeCmd utility. For more information, see the [EdgeCmd utility documentation (https://osisoft.github.io/Edgecmd-Docs/content/edgecmd-utility.html)](https://osisoft.github.io/Edgecmd-Docs/content/edgecmd-utility.html). To validate successful configurations, you can perform data retrieval (GET commands) using a browser, if available on your device.

For more information on PI adapter configuration tools, see [Configuration tools](xref:ConfigurationTools).

## Quick start

This Quick Start guides you through setup of each configuration file available for PI Adapter for OPC UA. As you complete each step, perform each required configuration to establish a data flow from a data source to one or more endpoints. Some configurations are optional.

**Important:** If you want to complete the optional configurations, complete those tasks before the required tasks.

1. Configure one or several OPC UA system components.<br>See [System components configuration](xref:SystemComponentsConfiguration#configure-system-components).

2. Configure an OPC UA data source for each OPC UA device.<br>See [PI Adapter for OPC UA data source configuration](xref:PIAdapterForOPCUADataSourceConfiguration#configure-opc-ua-data-source).

3. **Optional**: Configure client settings.<br> See [PI Adapter for OPC UA client settings configuration](xref:PIAdapterForOPCUAClientSettingsConfiguration#configure-opc-ua-client-settings).

4. Configure an OPC UA data selection for each OPC UA data source.<br>See [PI Adapter for OPC UA data selection configuration](xref:PIAdapterForOPCUADataSelectionConfiguration#configure-opc-ua-data-selection).<br><br>**Note:** If you do not configure data selection, a default OPC UA data selection file will be created if the OPC UA data source is valid.

5. **Optional**: Configure data filters and security<br>See the following topics:

    - [Data filters configuration](xref:DataFiltersConfiguration#configure-data-filters)
    - [PI Adapter for OPC UA security configuration](xref:pi-adapter-for-opc-ua-security-configuration#configure-opc-ua-adapter-security)

6. Configure one or several egress endpoints.<br>See [Egress endpoints configuration](xref:EgressEndpointsConfiguration#configure-egress-endpoints).

7. **Optional**: Configure health endpoints, general (diagnostics and metadata), buffering, and logging. See the following topics:

    - [Health endpoint configuration](xref:HealthEndpointConfiguration#configure-health-endpoint)
    - [General configuration](xref:GeneralConfiguration#configure-general)
    - [Buffering configuration](xref:BufferingConfiguration#configure-buffering)
    - [Logging configuration](xref:LoggingConfiguration#configure-logging)
 