---
uid: SystemRequirements
--- 

# System requirements

PI Adapter for OPC UA is supported on a variety of platforms and processors. Install kits are available for the following platforms:

| Operating System | Platform | Installation Kit | Processor(s) |
|-------------------|-------------|----------------------------------|-------------|
| Windows 10 Enterprise <br>Windows 10 IoT Enterprise | x64 | `OpcUa_win10-x64.msi`     | Intel/AMD 64-bit processors |
| Debian 9, 10 <br>Ubuntu 18.04, 20.04 | x64 | `OpcUa_linux-x64.deb`     | Intel/AMD 64-bit processors |
| Debian 9, 10 <br>Ubuntu 20.04 | ARM32 | `OpcUa_linux-arm.deb`  | ARM 32-bit processors |
| Debian 10 <br>Ubuntu 18.04, 20.04 | ARM64 | `OpcUa_linux-arm64.deb`  | ARM 64-bit processors |

Alternatively, you can use tar.gz files with binaries to build your own custom installers or containers for Linux. For more information on installing PI Adapter for OPC UA with Docker containers, see [Install PI Adapter for OPC UA using Docker](xref:InstallPIAdapterForOPCUAUsingDocker).

## PI Web API compatibility

This version of PI Adapter for OPC UA is compatible with PI Web API 2021 and later.

## PI Adapter for OPC UA upgrade

If you configured PI Adapter for OPC UA 1.1 to send data to PI Web API 2019, or OCS, or both and want to upgrade from version 1.1 to version 1.2, read [OPC UA Adapter - Upgrade from v1.1 to v1.2](https://osisoft.lightning.force.com/lightning/r/Knowledge__kav/ka08W000000frOFQAY/view). This knowledge article contains important information about upgrade scenarios.
