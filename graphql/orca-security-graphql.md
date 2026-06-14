# Orca Security GraphQL Schema

## Overview

This document describes the conceptual GraphQL schema for the Orca Security cloud security platform. Orca Security exposes a REST API for its Cloud Native Application Protection Platform (CNAPP), covering Cloud Security Posture Management (CSPM), Cloud Workload Protection Platform (CWPP), Cloud Infrastructure Entitlement Management (CIEM), Data Security Posture Management (DSPM), vulnerability management, malware detection, and attack path analysis.

The GraphQL schema below represents the data model derived from the Orca Security REST API surface, translating its resource-oriented endpoints into a strongly-typed graph that reflects the relationships between cloud assets, alerts, risks, compliance findings, and security policies.

## API Reference

- Documentation: https://docs.orcasecurity.io/docs/api-overview
- API Reference: https://app.orcasecurity.io/api-doc
- Authentication: https://docs.orcasecurity.io/docs/orca-api

## Authentication

Orca Security uses token-based authentication. API tokens are generated from the Orca console and passed as `Authorization: Token <value>` headers. The API is region-specific; the appropriate regional endpoint must be used.

## Schema Source

This is a conceptual schema derived from the Orca Security REST API documentation and platform capabilities. It models the domain objects and relationships exposed through the Orca platform across:

- Cloud asset inventory (VMs, containers, storage, databases, functions, networks)
- Alert and risk management
- Vulnerability and CVE tracking
- Compliance framework mapping
- Attack path analysis
- Data security and sensitive data discovery
- Identity and access management findings
- Integrations and webhooks

## Key Types

### Cloud Assets

The asset model covers the full cloud inventory across AWS, Azure, GCP, and Oracle Cloud:

- `Asset` — base asset interface with ID, name, type, cloud account, and region
- `CloudAsset` — enriched asset with risk score, alert counts, and compliance status
- `VM` — virtual machine with OS, configuration, installed packages, and vulnerability data
- `Container` — container workload with image, registry, and runtime details
- `Storage` — object storage buckets and file shares with sensitivity classification
- `Database` — managed database instances with exposure and configuration findings
- `Function` — serverless function assets with runtime and trigger details
- `Network` — VPCs, subnets, security groups, and firewall rules
- `LoadBalancer` — load balancer assets with exposure and TLS configuration

### Alerts and Risks

- `Alert` — security finding raised by Orca's detection engine
- `AlertDetails` — full alert context including asset, rule, and remediation
- `AlertStatus` — lifecycle state (open, in-progress, dismissed, resolved)
- `AlertSeverity` — critical, high, medium, low, informational
- `AlertCategory` — CSPM, CWPP, CIEM, DSPM, vulnerability, malware, best practice
- `Risk` — aggregated risk object with score and contributing factors
- `RiskScore` — numeric score with components and trend data
- `RiskFactor` — individual contributing factor to a risk score

### Vulnerabilities

- `Vulnerability` — software vulnerability found on an asset
- `CVE` — Common Vulnerabilities and Exposures entry
- `CVSSScore` — CVSS v2/v3 scoring data
- `ExploitAvailability` — exploit availability and maturity data

### Compliance

- `Compliance` — compliance posture object for an account or asset
- `Framework` — compliance framework (CIS, SOC 2, PCI DSS, HIPAA, NIST, etc.)
- `FrameworkControl` — individual control within a compliance framework
- `ComplianceStatus` — pass, fail, not applicable, or manual review
- `Finding` — compliance finding mapped to a control
- `FindingType` — type classification of a compliance finding
- `FindingRemediation` — remediation guidance for a compliance finding

### Policies and Remediations

- `Policy` — Orca security policy or custom rule
- `PolicyViolation` — asset-level policy violation
- `Remediation` — remediation record with status tracking
- `RemediationStatus` — pending, in-progress, completed, or accepted risk
- `RemediationStep` — individual step in a remediation workflow

### Attack Paths

- `AttackPath` — chained sequence of risks forming an exploitable attack route
- `AttackNode` — individual node in an attack path (asset, identity, or finding)
- `AttackEdge` — connection between nodes in an attack path
- `AttackSurface` — the internet-exposed or lateral-movement-reachable surface

### Data Security

- `DataAsset` — asset containing data with sensitivity classification
- `Sensitive` — sensitive data classification result
- `PIIData` — personally identifiable information finding
- `Secrets` — exposed secrets (API keys, credentials, tokens) found in assets

### Threat Detection

- `MalwareDetection` — malware finding with type, hash, and affected file
- `LateralMovement` — lateral movement opportunity between assets

### Identity and Access

- `User` — Orca platform user
- `IAMUser` — cloud IAM user discovered in cloud accounts
- `IAMRole` — cloud IAM role with attached policies and permissions
- `Credential` — credential object (key, certificate, or password)
- `APIKey` — API key finding with exposure status
- `Token` — token credential with scope and expiration data

### Cloud Accounts and Integrations

- `CloudAccount` — connected cloud account with provider, status, and asset counts
- `CloudProvider` — cloud provider enumeration (AWS, Azure, GCP, OCI)
- `Discovery` — asset discovery run metadata
- `Webhook` — outbound webhook integration configuration
- `Integration` — third-party integration (Jira, Slack, PagerDuty, SIEM, etc.)

## Schema File

See `orca-security-schema.graphql` for the full type definitions.
