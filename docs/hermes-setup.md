# Hermes Agent Environment — Setup and Configuration

## 1. Purpose

This document records the setup and validation of my Hermes-based Agentic AI environment.

The environment was created to gain hands-on experience operating an AI agent on remote Linux infrastructure and to understand how agent reasoning, orchestration, tools, sandboxed execution, external integrations, and development workflows work together.

The setup also provides a foundation for exploring how AI agents can safely participate in software-engineering and open-source workflows.

## 2. Infrastructure

### Remote Server

The Hermes environment is hosted on a **Contabo VPS** running Linux.

The VPS provides the persistent environment for the agent infrastructure.

### Local Workstation

My primary workstation is a Windows computer.

I use Windows PowerShell and SSH to connect to and administer the remote Contabo VPS.

```text
Windows Workstation
        |
        | SSH
        v
Contabo VPS
        |
        v
Linux Environment
```

## 3. Hermes Agent

Hermes was installed and configured on the Contabo VPS.

The Hermes environment provides the agent runtime and orchestration layer used to execute engineering-oriented tasks.

The setup was validated through controlled agent execution tests before proceeding to external integrations.

The experimentation focused on understanding:

- Agent task execution
- Tool usage
- Shell interaction
- Filesystem access
- External integrations
- Gateway behavior
- Logging
- Sandbox execution

## 4. Claude Code — AI Reasoning Layer

Claude Code is used as the AI reasoning and coding layer within the broader Agentic AI workflow.

An important architectural distinction in this environment is:

```text
Claude Code
    |
    | AI reasoning / coding
    v
Hermes
    |
    | Agent orchestration
    v
Tools / Execution / Integrations
```

Claude Code provides reasoning and coding capabilities, while the agent environment provides the surrounding tools, execution mechanisms, integrations, and operational controls.

## 5. Docker Sandbox

Docker was used to investigate controlled execution for agent-generated commands and tasks.

The purpose of sandboxing is to reduce the risk associated with allowing an AI agent to execute commands directly against the host environment.

The testing focused on:

- Containerized execution
- Isolation between the agent and host
- Command execution boundaries
- Tool access
- Potential risks from agent-generated commands

## 6. iron-proxy

`iron-proxy` forms part of the controlled execution/network path investigated during the Hermes setup.

The conceptual execution path is:

```text
Hermes Agent
     |
     v
Docker
     |
     v
iron-proxy
     |
     v
Controlled external access
```

Further testing is required to fully characterize the security properties and limitations of this configuration.

## 7. Git and GitHub

Git was verified as part of the development environment.

The work included:

- Checking Git availability
- Inspecting Git configuration
- Testing Git commands
- Investigating repository accessibility
- Working with Git branches
- Preparing repositories for development
- Establishing a workflow for open-source contribution

The environment was subsequently used to prepare for investigation of the Kyverno project and issue `kyverno/kyverno#16665`.

## 8. Slack Integration

Slack integration was configured and tested as part of the Hermes environment.

The purpose was to investigate how an AI agent can interact with an external collaboration platform.

The integration work focused on:

- Configuration
- Connectivity
- Agent communication
- Troubleshooting
- Understanding the integration within the overall Hermes architecture

## 9. Telegram Integration

Telegram integration was configured and investigated.

The integration progressed to connection attempts, but the Hermes gateway reported:

```text
[Telegram] Failed to connect to Telegram:
Any cannot be instantiated
```

The gateway subsequently reported that the Telegram reconnect attempt had failed and scheduled another retry.

### Current status

Telegram connectivity should therefore be considered:

**Under investigation — not fully operational.**

## 10. Gateway Logs and Troubleshooting

Hermes gateway logs were used to investigate the behavior of external integrations.

The troubleshooting process followed:

1. Identifying the affected integration.
2. Inspecting the gateway logs.
3. Reading the runtime error.
4. Checking connection and retry behavior.
5. Investigating configuration/runtime causes.
6. Recording findings.

This demonstrated the importance of observability when operating Agentic AI infrastructure.

## 11. Security Considerations

Operating an AI agent with access to infrastructure and development tools introduces security considerations.

The environment is being approached using:

### Least Privilege

The agent should have only the permissions required for the task.

### Sandboxed Execution

Potentially unsafe commands should be executed in an appropriate isolated environment where possible.

### Controlled Network Access

External network access should be restricted rather than automatically granting unrestricted connectivity.

### Secret Protection

Credentials, API keys, authentication tokens, and other sensitive information should not be committed to the public repository.

### Auditability

Agent actions should be observable through appropriate logs and records.

### Human Oversight

High-impact or irreversible actions should receive appropriate human review.

### Failure Transparency

Failures should be documented and investigated rather than hidden.

## 12. Current Environment Status

| Component | Status |
|---|---|
| Contabo VPS | Operational |
| Linux environment | Operational |
| Hermes | Configured and tested |
| Claude Code | Configured as AI reasoning/coding layer |
| Docker | Tested for sandbox execution |
| iron-proxy | Configured/investigated |
| Git | Operational |
| GitHub workflows | Tested/investigated |
| Slack | Configured/tested |
| Telegram | Under investigation |
| Kyverno repository | Prepared for further investigation |

## 13. Lessons From the Setup

Several practical lessons emerged:

1. An AI model is not the same as an agent runtime.
2. Agent execution requires security boundaries.
3. Integrations can fail independently.
4. Logs are essential for diagnosing agent infrastructure.
5. Remote infrastructure introduces additional operational concerns.
6. Failed experiments are valuable when accurately documented.

## 14. Relationship to Kyverno

The Hermes environment is part of my broader preparation for contributing to cloud-native open-source projects.

I am currently investigating the **Kyverno AI Assistant** project associated with:

`kyverno/kyverno#16665`

This documentation provides practical background for questions involving permissions, sandboxing, observability, integrations, and human control.

It does not claim a completed Kyverno implementation or contribution.

## 15. Future Work

Planned work includes:

- Continue troubleshooting the Telegram integration.
- Improve Hermes observability.
- Investigate controlled GitHub automation.
- Explore more granular agent permissions.
- Improve sandbox and network controls.
- Continue investigating Kyverno `#16665`.
- Make legitimate and reviewable contributions to Kyverno.
- Document future Agentic AI experiments and open-source contributions.

## 16. Security Notice

This repository is public.

No secrets is committed to it, including API keys, access tokens, passwords, SSH private keys, Telegram bot tokens, Slack credentials, cloud credentials, or other sensitive configuration.

Configuration examples should use placeholders rather than real credentials.
