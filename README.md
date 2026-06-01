# AI SOC Agent

An AI-powered Security Operations Center (SOC) assistant designed to help analysts triage alerts, investigate suspicious activity, and accelerate incident response workflows. This project is in early stages and made with data from the cyber range.

## Overview

AI SOC Agent combines modern Large Language Models (LLMs) with traditional security operations concepts to assist with:

- Alert triage
- Threat analysis
- MITRE ATT&CK mapping
- Incident summarization
- KQL query generation
- Threat intelligence enrichment
- Security investigation guidance

The goal is to reduce analyst workload and provide actionable security insights from raw security telemetry.

---

## Features

### Alert Analysis

Analyze security alerts and provide:

- Severity assessment
- Threat classification
- Analyst recommendations
- Investigation guidance

### MITRE ATT&CK Mapping

Automatically identify and map activity to relevant ATT&CK techniques and tactics.

### KQL Generation

Generate Microsoft Sentinel KQL queries from natural language requests.

**Input**

> Show failed logins from foreign countries.

**Output**

```kql
SigninLogs
| where ResultType != 0
| summarize FailedAttempts=count() by IPAddress, Country
| order by FailedAttempts desc
```

### Incident Summarization

Convert raw logs and alerts into analyst-friendly incident reports.

### Threat Intelligence Enrichment

Enrich indicators with:

- Geolocation data
- IP reputation
- Threat intelligence sources
- Known malicious infrastructure

---

## Architecture

```text
                ┌─────────────────┐
                │ Security Alerts │
                └────────┬────────┘
                         │
                         ▼
              ┌──────────────────┐
              │ Alert Processor  │
              └────────┬─────────┘
                       │
                       ▼
              ┌──────────────────┐
              │  AI Analysis     │
              └────────┬─────────┘
                       │
       ┌───────────────┼───────────────┐
       ▼               ▼               ▼
 MITRE Mapping   Threat Enrichment   KQL Generator
       │               │               │
       └───────────────┼───────────────┘
                       ▼
              ┌──────────────────┐
              │ Analyst Output   │
              └──────────────────┘
```

---

## Technology Stack

### Backend

- Python
- FastAPI
- OpenAI API
- SQLite/PostgreSQL

### Security

- Microsoft Sentinel
- KQL
- MITRE ATT&CK
- Sigma Rules

### Frontend

- Streamlit (Initial Version)
- React (Future)

---

## Current Status

🚧 **Early Development**

This project is currently in the initial build phase.

### Planned MVP

- [ ] Alert ingestion
- [ ] AI-powered alert triage
- [ ] MITRE ATT&CK mapping
- [ ] Incident summaries
- [ ] KQL generation
- [ ] Threat intelligence enrichment

---

## Future Roadmap

### Phase 1

- Alert classification
- Severity scoring
- MITRE mapping

### Phase 2

- Threat intelligence enrichment
- KQL query generation
- Analyst dashboard

### Phase 3

- Multi-agent architecture
- Automated response workflows
- SOAR integrations

### Phase 4

- Microsoft Sentinel integration
- Microsoft Defender integration
- Case management support

---

## Example Use Case

### Brute Force Detection

**Input**

```json
{
  "event": "Multiple failed logins followed by success",
  "host": "JKVMedr",
  "user": "joshlab"
}
```

**Output**

- Severity: High
- MITRE Technique: T1110 (Brute Force)
- Recommended Actions:
  - Review authentication logs
  - Verify MFA activity
  - Reset credentials if compromise is suspected

---

## Project Goals

This project aims to demonstrate practical skills in:

- Security Operations (SOC)
- Detection Engineering
- Threat Hunting
- Cloud Security
- KQL Development
- AI-Assisted Security Analysis
- Security Automation

---

## Disclaimer

This project is intended for educational, research, and defensive cybersecurity purposes only.

AI-generated recommendations should always be reviewed by a qualified security analyst before implementation in production environments.

---

## Author

**Joshua Kitchen**

Cloud Security | Threat Detection | AI Security | Offensive Security

Building security tools that combine cloud security, threat hunting, and artificial intelligence.
