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

1. Configure one or several OPC UA system components.<br>See [System components](xref:SystemComponentsConfiguration#configure-system-components).

2. Configure an OPC UA data source for each OPC UA device.<br>See [Data source](xref:PIAdapterForOPCUADataSourceConfiguration#configure-opc-ua-data-source).

3. **Optional**: Configure client settings.<br> See [Client settings](xref:PIAdapterForOPCUAClientSettingsConfiguration#configure-opc-ua-client-settings).

4. Configure an OPC UA data selection for each OPC UA data source.<br>See [Data selection](xref:PIAdapterForOPCUADataSelectionConfiguration#configure-opc-ua-data-selection).<br>**Note:** If you do not configure data selection, a default OPC UA data selection file will be created if the OPC UA data source is valid.

5. **Optional**: Configure data filters, security, diagnostics and metadata, buffering, and logging.<br>See the following topics:

    - [Data filters](xref:DataFiltersConfiguration#configure-data-filters)
    - [Security](xref:PIAdapterForOPCUASecurityConfiguration#configure-opc-ua-adapter-security)
    - [Diagnostics and metadata](xref:GeneralConfiguration#configure-general)
    - [Buffering](xref:BufferingConfiguration#configure-buffering)
    - [Logging](xref:LoggingConfiguration#configure-logging)

6. Configure one or several egress and health endpoints.<br>See [Egress endpoints](xref:EgressEndpointsConfiguration#configure-egress-endpoints) and [Health endpoints](xref:HealthEndpointConfiguration#configure-health-endpoint).
 