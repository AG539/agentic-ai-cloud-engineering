# Agentic AI & Cloud Engineering

**Agnes Livingstone**
Cloud / DevOps Engineer | Cloud Security | Agentic AI

This repository documents my hands-on engineering work at the intersection of **cloud infrastructure, DevOps, cloud security, AI-assisted software engineering, and Agentic AI**.

My focus is on understanding how AI agents can interact with real engineering environments while maintaining appropriate **security boundaries, permissions, observability, reproducibility, and human oversight**.

---

## Technical Focus

- Cloud Engineering
- DevOps and CI/CD
- Cloud Security
- Infrastructure as Code
- Linux and virtual machines
- Git and GitHub workflows
- Docker and sandboxed execution
- AI-assisted software engineering
- Agentic AI
- Secure automation
- Open-source contribution

### Technologies & Tools

**Cloud & Infrastructure**

- AWS
- Terraform
- Linux
- Virtual machines
- Networking and security

**DevOps & Security**

- Git
- GitHub
- CI/CD
- Docker
- Trivy
- Grafana / Loki
- Infisical
- IAM and access control

**AI Engineering**

- Hermes
- Claude Code
- Ollama
- AI agent workflows
- Agent sandboxing
- Controlled automation

---

# Agentic AI Engineering

A major focus of my current engineering development is understanding how AI agents can perform useful engineering tasks rather than simply generate text.

My hands-on work includes operating an Agentic AI environment on a **Contabo VPS**, using **Hermes as the agent runtime/orchestration layer** and **Claude Code as the AI reasoning and coding layer**.

The environment has been used to investigate:

- Agent execution
- Tool use
- Sandboxed execution
- Docker-based workflows
- Git and GitHub operations
- External communication integrations
- Gateway services
- Logging and troubleshooting
- Permission boundaries
- Secure automation

The high-level architecture is:

```text
                 Claude Code
              AI reasoning/coding
                      |
                      v
                   Hermes
          Agent runtime/orchestration
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
       Tools       Docker     Integrations
                    Sandbox
                      |
                      v
                Controlled execution
```

This separation between **reasoning** and **agent orchestration** is an important part of my understanding of Agentic AI systems.

---

# Hermes Agent Environment

The `projects/hermes/` directory documents my hands-on Hermes environment.

The environment is hosted on a **Contabo VPS** and includes experimentation with:

- Hermes agent runtime
- Claude Code
- Docker
- Sandboxed execution
- Git/GitHub
- Gateway services
- Slack integration
- Telegram integration
- Logging and troubleshooting
- Controlled agent execution

The purpose of this work is not simply to run an AI assistant, but to understand the engineering considerations involved when an agent is given access to real tools and infrastructure.

Where capabilities or integrations remain incomplete, they are documented as **under investigation** rather than presented as successful.

---

# Evidence & Documentation

This repository contains documentation and evidence from the actual development environment.

### Architecture

- [Agent Architecture](docs/agent-architecture.md)

Describes the relationship between Claude Code, Hermes, tools, execution environments, and integrations.

### Environment

- [Hermes Setup](docs/hermes-setup.md)

Documents the environment setup and operational workflow.

### Lessons Learned

- [Lessons Learned](docs/lessons-learned.md)

Records practical engineering lessons from configuring, operating, and troubleshooting the Agentic AI environment.

### Evidence

- [Environment Evidence](evidence/environment/environment-summary.md)
- [Agent Execution Evidence](evidence/execution/execution-summary.md)
- [Integration Status](evidence/integrations/integrations-summary.md)
- [Troubleshooting Evidence](evidence/troubleshooting/troubleshooting-summary.md)

These documents distinguish between:

- Completed work
- Successful experiments
- Failed experiments
- Unresolved issues
- Ongoing investigation

The intention is to maintain an accurate engineering record rather than overstate results.

---

# Current Open-Source Focus

I am currently preparing to contribute to the **Kyverno AI Assistant** project associated with:

**kyverno/kyverno#16665**

My current investigation focuses on understanding the engineering problem and the requirements for building a useful and secure AI assistant for software-maintainer workflows.

Areas of investigation include:

- Understanding the issue and proposed workflow
- Studying the existing Kyverno codebase
- Understanding repository and GitHub workflows
- Agent architecture
- Permission boundaries
- Sandboxed execution
- GitHub-based automation
- Safe maintainer interactions
- Testing and failure handling
- Auditability
- Human approval for sensitive actions

I am also evaluating how the experience gained from building and operating my Hermes Agentic AI environment can inform my approach to the Kyverno AI Assistant problem.

**This repository does not claim a completed Kyverno contribution.** It documents the technical preparation and Agentic AI engineering experience supporting my planned contribution.

---

# Engineering Principles

My approach to Agentic AI is influenced by the same principles I apply to cloud and security engineering.

### Least Privilege

Agents should receive only the permissions required for a specific task.

### Isolation

Potentially unsafe agent actions should execute within appropriate boundaries rather than receiving unrestricted access to the host environment.

### Auditability

Important actions should produce records that can be inspected and reviewed.

### Human Oversight

High-impact, irreversible, or security-sensitive actions should require appropriate human review or approval.

### Reproducibility

Engineering work should be documented clearly enough for another engineer to understand the environment and reproduce relevant experiments.

### Failure Transparency

Failed experiments and unresolved issues are part of engineering work.

For example, the Telegram integration in the Hermes environment encountered a runtime error during connection initialization. That failure is documented rather than being presented as a successful integration.

---

# Portfolio Structure

```text
agentic-ai-cloud-engineering/
│
├── README.md
│
├── docs/
│   ├── hermes-setup.md
│   ├── agent-architecture.md
│   └── lessons-learned.md
│
├── projects/
│   └── hermes/
│       └── README.md
│
└── evidence/
    ├── environment/
    │   └── environment-summary.md
    │
    ├── execution/
    │   └── execution-summary.md
    │
    ├── integrations/
    │   └── integrations-summary.md
    │
    ├── troubleshooting/
    │   └── troubleshooting-summary.md
    │
    └── screenshots/
```

---

# Security & Responsible Disclosure

This repository is intended to document engineering work without exposing sensitive infrastructure information.

The repository must never contain:

- API keys
- Access tokens
- Passwords
- SSH private keys
- Cloud credentials
- Telegram bot tokens
- Slack credentials
- Other secrets

Screenshots and logs should be reviewed and redacted before being committed if they contain sensitive information.

The public documentation focuses on the engineering process, architecture, observations, and lessons learned rather than exposing operational secrets.

---

# Current Learning Direction

My engineering development is progressing across:

```text
Cloud Engineering
        |
        v
DevOps
        |
        v
Cloud Security
        |
        v
AI-Assisted Engineering
        |
        v
Agentic AI
        |
        v
Open-Source Contribution
```

I am particularly interested in building AI systems that can interact with real engineering environments responsibly, with clear permissions, security controls, observable actions, and appropriate human oversight.

---

# Open-Source Goal

My goal is not simply to learn about open source.

I want to become a consistent contributor who can:

1. Understand an existing codebase.
2. Read and reason about an unfamiliar technical problem.
3. Communicate effectively with maintainers.
4. Investigate issues systematically.
5. Make focused changes.
6. Write and run appropriate tests.
7. Document technical decisions.
8. Respond to review feedback.
9. Contribute improvements that are genuinely useful to the community.

My current Kyverno AI Assistant investigation is part of that progression.

This repository will evolve as my Agentic AI engineering experiments and open-source contributions progress.
