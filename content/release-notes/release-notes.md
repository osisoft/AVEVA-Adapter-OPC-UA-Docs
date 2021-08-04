---
uid: ReleaseNotes
---

# Release notes

PI Adapter for OPC UA 1.1.1
Adapter framework 1.2

## Overview

This represents the hot-fix release for PI Adapter for OPC UA. This product collects time series data and relevant metadata from an OPC UA (OPC Unified Architecture) server and sends it to configured OMF endpoints such as PI Web API and OSIsoft Cloud Services. PI Adapter for OPC UA can also collect health and diagnostics information. It supports buffering, unsolicited data collection, automatic discovery of available data items on a data source, and various Windows and Linux-based operating systems as well as containerization.

For more information see [PI Adapter for OPC UA overview](xref:PIAdapterForOPCUAOverview).

## Fixes and enhancements

### Fixes

The following items were resolved in this release of PI Adapter for OPC UA:

Work item | Description
--------- | -----------
189594 | Under certain conditions, the adapter failed to discover items on an OPC UA server. |
204744 | The adapter did not fully support fast sampling rates. |

## Known issues

There are no known issues at this time.

## System requirements

Refer to [System requirements](xref:SystemRequirements).

## Installation

Refer to [Install the adapter](xref:InstallTheAdapter).

## Uninstallation

Refer to [Uninstall the adapter](xref:UninstallTheAdapter).

## Security information and guidance

### OSIsoft’s commitment

Because the PI System often serves as a barrier protecting control system networks and mission-critical infrastructure assets, OSIsoft is committed to (1) delivering a high-quality product and (2) communicating clearly what security issues have been addressed. This release of PI Adapter for OPC UA is the highest quality and most secure version of PI Adapter for OPC UA released to date. OSIsoft's commitment to improving the PI System is ongoing, and each future version should raise the quality and security bar even further.

### Vulnerability communication

The practice of publicly disclosing internally discovered vulnerabilities is consistent with the [Common Industrial Control System Vulnerability Disclosure Framework](https://ics-cert.us-cert.gov/sites/default/files/ICSJWG-Archive/ICSJWG_Vulnerability_Disclosure_Framework_Final_1.pdf) developed by the [Industrial Control Systems Joint Working Group (ICSJWG)](https://ics-cert.us-cert.gov/Industrial-Control-Systems-Joint-Working-Group-ICSJWG). Despite the increased risk posed by greater transparency, OSIsoft is sharing this information to help you make an informed decision about when to upgrade to ensure your PI System has the best available protection.

For more information, refer to OSIsoft’s [Ethical Disclosure Policy](https://www.osisoft.com/ethical-disclosure-policy).

To report a security vulnerability, refer to OSIsoft's [Report a Security Vulnerability](https://www.osisoft.com/report-a-security-vulnerability).

### Vulnerability scoring

OSIsoft has selected the [Common Vulnerability Scoring System (CVSS)](https://www.first.org/cvss/v2/guide) to quantify the severity of security vulnerabilities for disclosure. To calculate the CVSS scores, OSIsoft uses the [National Vulnerability Database (NVD) calculator](https://nvd.nist.gov/cvss.cfm?calculator&amp;version=2) maintained by the National Institute of Standards and Technology (NIST).  OSIsoft uses Critical, High, Medium and Low categories to aggregate the CVSS Base scores. This removes some of the opinion-related errors of CVSS scoring.  As noted in the [CVSS specification](https://www.first.org/cvss/specification-document), Base scores range from 0 for the lowest severity to 10 for the highest severity.

### Overview of new vulnerabilities found or fixed

This section is intended to provide relevant security-related information to guide your installation or upgrade decision. OSIsoft is proactively disclosing aggregate information about the number and severity of PI Adapter for OPC UA security vulnerabilities that are fixed in this release.

No security-related information is applicable to this release.

## Technical support and resources

Refer to [Technical support and feedback](xref:TechnicalSupportAndFeedback).
