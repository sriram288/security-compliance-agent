# Security Compliance Agent

AI-powered Security & Compliance Agent for multi-cloud environments (AWS + GCP).

It automates:

- Vulnerability collection from multiple sources
- Intelligent triage and prioritization
- Remediation recommendations
- GitLab ticket creation
- Evidence packaging for compliance (SOC 2, ISO 27001, CIS Benchmarks)

Built with **LangGraph + OpenAI + DefectDojo**.

## Architecture (High Level)
Collectors → DefectDojo → LangGraph Agent (OpenAI) → GitLab Issues
↑
AWS Inspector, ECR, GCP SCC, SonarQube, Wazuh


## Features

- Multi-source vulnerability ingestion
- AI-based prioritization using severity, EPSS, exploitability, and asset context
- Automated remediation suggestions
- Automatic GitLab issue creation
- Designed for EKS deployment
- Human-in-the-loop support (Dry-run mode)

## Tech Stack

| Component          | Technology                  |
|--------------------|-----------------------------|
| AI Agent           | LangGraph + LangChain       |
| LLM                | OpenAI (GPT-4o / GPT-4.1)   |
| Findings Store     | DefectDojo                  |
| Orchestration      | Kubernetes (EKS) + Helm     |
| Collectors         | Python                      |
| Ticketing          | GitLab Issues API           |
| Secrets Management | AWS Secrets Manager + ESO   |

## Repository Structure

```text
security-compliance-agent/
├── agent/                  # LangGraph AI Agent
├── collectors/             # Data collectors (AWS, GCP, SonarQube, Wazuh)
├── k8s/                    # Raw Kubernetes manifests
├── helm/                   # Helm chart
├── docker-compose.yml      # Local development
├── .env.example
├── docs/
│   └── architecture.md
├── LICENSE
└── README.md

Prerequisites

- Python 3.11+
- Docker & Docker Compose
- OpenAI API key
- Access to:
  - DefectDojo
  - GitLab
  - AWS (Inspector + ECR)
  - GCP (SCC + Artifact Registry) – optional for pilot
  - SonarQube & Wazuh – optional for pilot
