---
uid: SystemRequirements
--- 

# System requirements

PI Adapter for OPC UA is supported on a variety of platforms and processors. Install kits are available for the following platforms:

| Operating System | Platform | Installation Kit | Processor(s) |
|-------------------|-------------|----------------------------------|-------------|
| Windows 10 Enterprise <br>Windows 10 IoT Enterprise | x64 | `OpcUa_win10-x64.msi`     | Intel/AMD 64-bit processors |
| Debian 9, 10 <br>Ubuntu 18.04, 20.04 | x64 | `OpcUa_linux-x64.deb`     | Intel/AMD 64-bit processors |
| Debian 9,10 <br>Ubuntu 18.04, 20.04 | ARM32 | `OpcUa_linux-arm.deb`  | ARM 32-bit processors |
| Debian 9,10 <br>Ubuntu 18.04, 20.04 | ARM64 | `OpcUa_linux-arm64.deb`  | ARM 64-bit processors |

Alternatively, you can use tar.gz files with binaries to build your own custom installers or containers for Linux. For more information on installing PI Adapter for OPC UA with Docker containers, see [Install PI Adapter for OPC UA using Docker](xref:InstallPIAdapterForOPCUAUsingDocker).

## Upgrade

The PI Adapter for OPC UA upgrade from version 1.1 to version 1.2 comes with the following recommendations:

### Upgrade and PI Web API

Upgrade PI Web API before you upgrade the adapter. This upgrade order ensures that no data gets lost and that quality information is automatically sent to PI Web API.

### Upgrade and OCS

Perform a type migration in OCS. Quality information in OCS will be discarded when you upgrade the adapter. A type migration helps to retrieve quality information. For more information, see also [Types best practices](https://docs.osisoft.com/bundle/ocs/page/add-organize-data/store-data/types/types-best-practices.html).
