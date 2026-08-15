# Agentic AI Environment Summary

## Purpose

This document records the environment used for my hands-on Agentic AI engineering experiments.

The environment combines remote infrastructure, an AI agent runtime, an AI coding/reasoning system, containerized execution, development tooling, and external communication integrations.

## Infrastructure

### Contabo VPS

The primary Agentic AI environment runs on a Contabo VPS.

The VPS provides the persistent Linux environment used for Hermes, agent execution, Docker, Git, GitHub workflows, external integrations, gateway services, and troubleshooting.

I administer the environment remotely from a Windows workstation using SSH and PowerShell.

## AI Agent Stack

The environment separates the AI reasoning layer from the agent orchestration layer.

```text
Claude Code
    |
    | AI reasoning / coding
    v
Hermes
    |
    | Agent orchestration
    v
Tools + Execution + Integrations
```

### Claude Code

Claude Code is used as the AI reasoning and coding layer within the broader Agentic AI workflow.

### Hermes

Hermes provides the agent runtime and orchestration environment. It enables the agent to interact with tools, execute tasks, work with the environment, and connect to external services.

## Execution Environment

### Docker

Docker was tested as part of the controlled execution environment. The objective was to investigate how agent-generated commands can be executed within an isolated environment instead of giving the agent unrestricted access to the host.

### iron-proxy

`iron-proxy` was investigated as part of the controlled execution and network path.

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

Further testing is required before making stronger claims about the complete security properties of this configuration.

## Development Tooling

The environment includes Git and GitHub workflows for software development, including repository inspection, branch creation, repository access testing, Git history inspection, and preparation for open-source contribution.

## External Integrations

### Slack

Slack was configured and tested as an external communication integration.

### Telegram

Telegram integration was configured and investigated.

The Hermes gateway reported:

```text
[Telegram] Failed to connect to Telegram:
Any cannot be instantiated
```

The gateway subsequently attempted to reconnect.

**Current status: Under investigation — not fully operational.**

## Observability

Gateway logs were used to investigate agent and integration behavior.

The troubleshooting process included identifying the affected component, inspecting gateway logs, reading runtime errors, checking reconnect behavior, recording observed results, and separating confirmed facts from assumptions.

## Security Considerations

The environment is being developed with:

- Least privilege
- Sandboxed execution
- Controlled network access
- Secret protection
- Logging and observability
- Human oversight
- Failure transparency

The public repository must not contain API keys, access tokens, passwords, SSH private keys, cloud credentials, Telegram bot tokens, Slack credentials, or other sensitive secrets.

## Relationship to Open Source

The environment provides practical experience relevant to my investigation of cloud-native open-source Agentic AI workflows.

I am currently investigating the Kyverno AI Assistant project associated with:

`kyverno/kyverno#16665`

This does not claim a completed Kyverno contribution.

## Evidence Principle

Successful, unsuccessful, and incomplete experiments are documented according to their observed status rather than being presented as completed work.

## Summary

**Cloud Infrastructure + Agent Runtime + AI Reasoning + DevOps + Containerization + Integrations + Troubleshooting + Security**

This forms the technical foundation for my continued Agentic AI engineering and open-source contribution work.
