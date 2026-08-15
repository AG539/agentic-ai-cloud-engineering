# Agentic AI Architecture

## Overview

This document describes the architecture of my experimental Agentic AI environment and the relationship between infrastructure, agent runtime, AI reasoning, execution, integrations, and development tools.

The environment is built around:

- Contabo VPS
- Linux
- Hermes
- Claude Code
- Docker
- iron-proxy
- Git
- GitHub
- Slack
- Telegram

## High-Level Architecture

```text
                    +----------------------+
                    | Windows Workstation  |
                    | PowerShell / SSH     |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    |     Contabo VPS      |
                    |       Linux          |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    |       Hermes         |
                    | Agent Runtime /      |
                    |   Orchestration      |
                    +----------+-----------+
                               |
              +----------------+----------------+
              |                |                |
              v                v                v
       +--------------+  +-----------+  +--------------+
       | Claude Code  |  |   Tools   |  | Integrations |
       | AI Reasoning |  |           |  | Slack/Telegram|
       +--------------+  +-----+-----+  +--------------+
                                |
                                v
                         +-------------+
                         |   Docker    |
                         |   Sandbox   |
                         +------+------+
                                |
                                v
                         +-------------+
                         | iron-proxy  |
                         | Controlled  |
                         | network     |
                         +-------------+
```

## 1. Windows Workstation

The Windows workstation acts as the administrative client environment.

PowerShell and SSH are used to connect to and manage the remote Contabo VPS.

The workstation is not the primary Hermes runtime environment. The agent infrastructure operates on the remote Linux VPS.

## 2. Contabo VPS

The Contabo VPS provides the remote Linux infrastructure on which the Agentic AI environment operates.

It provides compute, persistent storage, network connectivity, Docker execution, and the runtime environment required by Hermes.

Remote access makes infrastructure security important, including SSH security, credentials, permissions, and network exposure.

## 3. Hermes Agent Runtime

Hermes provides the agent runtime and orchestration layer.

Its role is different from the underlying AI reasoning system.

Conceptually:

```text
User Task
    |
    v
Hermes
    |
    +-- Reasoning / coding capability
    +-- Tools
    +-- Shell interaction
    +-- Filesystem interaction
    +-- Sandbox execution
    +-- External integrations
```

## 4. Claude Code — AI Reasoning Layer

Claude Code is used as the AI reasoning and coding layer.

```text
Claude Code
     |
     | Reasoning / coding
     v
Hermes
     |
     | Agent orchestration
     v
Tools / Execution / Integrations
```

The model provides reasoning and coding capabilities, while the agent runtime provides the mechanisms through which those capabilities interact with tools and execution environments.

## 5. Docker and Sandboxing

Docker provides containerized execution for agent-generated commands and experiments.

The sandbox concept is:

```text
Agent
  |
  v
Docker
  |
  v
Sandboxed execution
```

Containerization can add an execution boundary, but it should not automatically be treated as a complete security solution.

A production system would also consider privileges, volumes, network access, secrets, resource limits, host access, and escape risks.

## 6. iron-proxy

`iron-proxy` forms part of the controlled execution and network path investigated during the setup.

```text
Agent
  |
  v
Docker / Sandbox
  |
  v
iron-proxy
  |
  v
Controlled external access
```

Further testing is required before making stronger claims about its complete security properties.

## 7. Git and GitHub

Git and GitHub provide the software-development layer for repository access, version control, branching, collaboration, and open-source contribution.

The environment was used to prepare for investigation of Kyverno and `kyverno/kyverno#16665`.

## 8. Communication Integrations

Slack and Telegram were explored as external communication interfaces.

They introduce their own authentication, permission, network, data-handling, and failure considerations.

Slack was configured/tested. Telegram remains under investigation because of the observed runtime error.

## 9. Control and Data Flow

A simplified task flow is:

```text
User / Engineer
       |
       v
     Task
       |
       v
     Hermes
       |
       v
Claude Code
       |
       | Reasoning / planning
       v
   Agent Action
       |
       v
      Tool
       |
       +------------------+
       |                  |
       v                  v
   Git/GitHub           Docker
                           |
                           v
                      iron-proxy
                           |
                           v
                    External resource
```

## 10. Security Boundaries

Potential boundaries include:

- Infrastructure boundary: Contabo VPS
- Agent boundary: Hermes
- Execution boundary: Docker
- Network boundary: iron-proxy
- Repository boundary: Git/GitHub permissions
- Communication boundary: Slack/Telegram authentication

## 11. Least-Privilege Model

```text
Task
  |
  v
Required capability
  |
  v
Minimum permission
  |
  v
Controlled execution
  |
  v
Observable result
```

An agent should not receive broad access simply because broad access makes automation easier.

## 12. Human Oversight

Low-risk activities such as repository exploration, documentation generation, and static analysis may be suitable for greater automation.

Higher-risk actions such as production changes, deletion, permission changes, sensitive publishing, and important merges should receive stronger controls and appropriate human review.

## 13. Observability

Important information includes:

- Commands executed
- Tools invoked
- Integration status
- Runtime errors
- Retry behavior
- Authentication failures
- Network failures
- Sandbox failures

Hermes gateway logs were used to investigate integration failures, including the Telegram runtime problem.

## 14. Failure Handling

Individual components can fail independently:

```text
Hermes
 |
 +-- Core agent     -> may work
 +-- Docker         -> may work
 +-- GitHub         -> may work
 +-- Slack          -> may work
 +-- Telegram       -> currently failing
```

Component-level monitoring and status reporting are therefore important.

## 15. Current Architecture Status

| Component | Status |
|---|---|
| Windows workstation | Operational |
| SSH access | Operational |
| Contabo VPS | Operational |
| Linux environment | Operational |
| Hermes | Configured and tested |
| Claude Code | Used as AI reasoning/coding layer |
| Docker | Tested |
| Sandbox execution | Tested |
| iron-proxy | Configured/investigated |
| Git | Operational |
| GitHub | Tested/investigated |
| Slack | Configured/tested |
| Telegram | Under investigation |

## 16. Security Limitations

This is an experimental engineering environment, not a production-ready autonomous agent platform.

Further work would be required around:

- Fine-grained permissions
- Secret management
- Network policies
- Container isolation
- Resource limits
- Audit logging
- Approval workflows
- Prompt injection resistance
- Supply-chain security
- Recovery from unsafe actions

## 17. Relevance to Kyverno

The architecture is relevant to my investigation of the Kyverno AI Assistant project associated with `kyverno/kyverno#16665`.

The investigation raises questions about:

- Agent permissions
- Repository access
- Isolation
- Auditing
- Human approval
- Failure handling
- Safe automation

This documentation does not claim a completed Kyverno implementation or contribution.

## Conclusion

The environment demonstrates that an AI agent is a layered engineering system:

```text
Infrastructure
      |
      v
Agent Runtime
      |
      v
AI Reasoning
      |
      v
Tools
      |
      v
Execution Environment
      |
      v
Network / External Services
      |
      v
Observability and Security Controls
```

Understanding and securing these layers is central to reliable Agentic AI engineering.
