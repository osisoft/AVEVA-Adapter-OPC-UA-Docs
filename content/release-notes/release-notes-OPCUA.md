---
uid: ReleaseNotesOPCUA
---

# AVEVA Adapter for OPC UA

AVEVA Adapter for OPC UA: 1.4.1.32<br>

Adapter Framework: 1.8

## Overview

AVEVA Adapter for OPC UA collects time series data and relevant metadata from an OPC UA (OPC Unified Architecture) server and sends it to configured "Open Message Format (OMF) endpoints such as PI Web API and AVEVA Data Hub. AVEVA Adapter for OPC UA can also collect health and diagnostics information. It supports buffering, unsolicited data collection, on-demand discovery of available data items on a data source, on-demand or automatic history recovery of data items, client and server level failover, and various Windows and Linux-based operating systems as well as containerization.

This version is released with the support for client failover and server failover functionality.

For more information see [AVEVA Adapter for OPC UA overview](xref:AVEVAAdapterForOPCUAOverview).

## Fixes and enhancements

### Fixes

The following issues reported from earlier versions are fixed in this release.

- The adapter no longer creates duplicate subscriptions for data selection items on startup in some scenarios

### Enhancements

The following enhancements are added in this release.

- Enhanced error handling while attempting to read server redundancy related nodes from the server
- The Adapter no longer reads the ServiceLevel node when not configured for server failover.
- Added support for manually configuring the redundancy set used during server failover

## Known issues

There are no known issues at this time.

## Setup

### System requirements

Refer to [System requirements](xref:SystemRequirements).

### Installation and upgrade

Refer to [Install the adapter](xref:InstallTheAdapter).

### Uninstallation

Refer to [Uninstall the adapter](xref:UninstallTheAdapter).

## Security information and guidance

AVEVA is [committed to releasing secure products](https://docs.osisoft.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html). This section is intended to provide relevant security-related information to guide your installation or upgrade decision.  

AVEVA [proactively discloses](https://docs.osisoft.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html#vulnerability-communication) aggregate information about the number and severity of security vulnerabilities addressed in each release. The tables below provide an overview of security issues addressed and their relative severity based on [standard scoring](https://docs.osisoft.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html#vulnerability-scoring).

### Overview of new vulnerabilities found or fixed

This section is intended to provide relevant security-related information to guide your installation or upgrade decision. AVEVA is proactively disclosing aggregate information about the number and severity of AVEVA Adapter for OPC UA security vulnerabilities that are fixed in this release.

| Component | Version | CVE or Reference | CVSS | Mitigation                                                                                                 |
| ----------| ------- | --------------------------------------------------------------------------------------------------- | ---- | ---------------------------------------------------------------------------------------------------------- |
| zlib      | 1.2.11  | [CVE-2018-25032](https://nvd.nist.gov/vuln/detail/CVE-2018-25032) | 7.5  | The AVEVA Adapter’s utilization of zlib through the .NET 6 Framework does not expose these vulnerabilities |
| zlib      | 1.2.11  | [CVE-2022-37434](https://nvd.nist.gov/vuln/detail/CVE-2022-37434) | 9.3  | The AVEVA Adapter’s utilization of zlib through the .NET 6 Framework does not expose these vulnerabilities. |

## Documentation overview

[EdgeCmd utility](https://docs.osisoft.com/bundle/edgecmd/page/index.html): Provides an overview on how to configure and administer AVEVA Adapters on Linux and Windows using command line arguments.

## Technical support and resources

Refer to [Technical support and feedback](xref:TechnicalSupportAndFeedback).
