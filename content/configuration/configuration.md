---
uid: AVEVAAdapterForOPCUAConfiguration
---

# Configuration

AVEVA Adapter for OPC UA enables you to configure data source and data selection. The adapter also provides the ability to configure security and to generate a data selection file instead of manual configuration.

The examples in the configuration topics use `curl`, a commonly available tool on both Windows and Linux. The adapter can be configured with any programming language or tool that supports making REST calls, or with the EdgeCmd utility. For more information, see the [EdgeCmd utility documentation](https://docs.osisoft.com/bundle/edgecmd/page/index.html). To validate configurations, you can perform data retrieval (GET commands) using a browser, if available on your device.

For more information on AVEVA Adapter configuration tools, see [Configuration tools](xref:ConfigurationTools).

## Quick start

These steps guide you through setup of each configuration file available for AVEVA Adapter for OPC UA. As you complete each step, perform each required configuration to establish a data flow from a data source to one or more endpoints. Some configurations are optional.

**Important:** If you want to complete the optional configurations, complete those tasks _before_ the required tasks.

1. Configure one or several OPC UA system components.See [System components](xref:SystemComponentsConfiguration#configure-system-components).

1. Configure an OPC UA data source for each OPC UA device.See [Data source](xref:AVEVAAdapterForOPCUADataSourceConfiguration#configure-opc-ua-data-source).

1. **Optional**: Configure client settings. See [Client settings](xref:AVEVAAdapterForOPCUAClientSettingsConfiguration#configure-opc-ua-client-settings).

1. **Optional**: Perform data source discovery. See [Discovery](xref:DataSourceDiscovery).

1. Configure an OPC UA data selection for each OPC UA data source.See [Data selection](xref:AVEVAAdapterForOPCUADataSelectionConfiguration#configure-opc-ua-data-selection).

1. **Optional**: Configure data filters, security, diagnostics and metadata, buffering, and logging.See the following topics:

    - [Data filters](xref:DataFiltersConfiguration#configure-data-filters)
    - [Security](xref:AVEVAAdapterForOPCUASecurityConfiguration#configure-opc-ua-adapter-security)
    - [Diagnostics and metadata](xref:GeneralConfiguration#configure-general)
    - [Buffering](xref:BufferingConfiguration#configure-buffering)
    - [Logging](xref:LoggingConfiguration#configure-logging)

1. Configure one or several egress and health endpoints.See [Egress endpoints](xref:EgressEndpointsConfiguration#configure-egress-endpoints) and [Health endpoints](xref:HealthEndpointConfiguration#configure-health-endpoint).
