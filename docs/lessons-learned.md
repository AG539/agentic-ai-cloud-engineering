# Lessons Learned from the Hermes Agent Environment

## Overview

Building and operating the Hermes Agentic AI environment on a Contabo VPS provided practical experience with infrastructure, agent orchestration, AI reasoning, sandboxed execution, external integrations, Git/GitHub workflows, and troubleshooting.

## 1. AI Model vs Agent Runtime

Claude Code provides the AI reasoning and coding layer, while Hermes provides the agent runtime and orchestration layer.

```text
Claude Code
    |
    v
Hermes
    |
    v
Tools + Execution + Integrations
```

An AI model alone is not a complete engineering agent. A useful agent also requires tools, execution controls, permissions, integrations, and observability.

## 2. Remote Infrastructure

Running Hermes on a Contabo VPS introduced real infrastructure considerations including SSH access, Linux permissions, network exposure, credentials, persistent services, Docker, external integrations, and logging.

This reinforced that Agentic AI infrastructure should be treated as an engineering system.

## 3. Least Privilege

Agent capabilities should be deliberately scoped.

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

An agent performing repository analysis may only require read access, while an agent modifying infrastructure requires stronger permissions.

## 4. Sandboxing

Docker sandbox testing demonstrated the value of isolating agent-generated commands from the host environment.

However, containerization should not automatically be considered a complete security solution.

A production system would still need to consider container privileges, mounted volumes, network access, secrets, resource limits, host access, and container escape risks.

## 5. Network Controls

The environment also investigated `iron-proxy` as part of the controlled execution and network path.

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

Further testing is required before making stronger claims about the security guarantees of this configuration.

## 6. Integration Failures

Telegram provided an important troubleshooting example.

The Hermes gateway reported:

```text
[Telegram] Failed to connect to Telegram:
Any cannot be instantiated
```

The gateway subsequently attempted to reconnect.

This demonstrated that individual components of an agent system can fail independently.

Telegram is therefore documented as **under investigation**, rather than being incorrectly described as fully operational.

## 7. Observability

Gateway logs were essential for investigating the Telegram problem.

The troubleshooting process involved:

1. Identifying the affected integration.
2. Inspecting gateway logs.
3. Reading the runtime error.
4. Checking reconnect behavior.
5. Recording the observed state.
6. Separating confirmed facts from assumptions.

This reinforced the importance of observability in autonomous systems.

## 8. Failed Experiments Are Evidence

An unsuccessful experiment is still valuable engineering evidence when it is properly documented.

The Telegram failure provided information about integration behavior, runtime errors, retry behavior, component boundaries, and remaining work.

Documenting failures honestly is more useful than presenting an artificially perfect project.

## 9. Communication Integrations

Slack and Telegram are not merely messaging features.

When an agent is connected to a communication platform, important questions include:

- Who can interact with the agent?
- What commands can be issued?
- What information can be returned?
- What permissions does the agent have?
- Can messages trigger sensitive actions?
- How are users authenticated?
- Are actions logged?

## 10. GitHub Permissions

AI agents interacting with GitHub should follow least privilege.

A useful progression is:

```text
Read repository
      |
      v
Create branch
      |
      v
Modify files
      |
      v
Create pull request
      |
      v
Approve / merge
```

Permissions should increase only when the task requires them.

## 11. Human Oversight

Not every action should be autonomous.

Lower-risk activities include repository exploration, documentation generation, static analysis, and code searching.

Higher-risk activities include changing production infrastructure, deleting resources, modifying access controls, merging important code, and publishing sensitive information.

Higher-risk actions should receive stronger controls and, where appropriate, human approval.

## 12. Agentic AI Requires More Than Prompting

A useful agent requires more than a powerful model or a good prompt.

```text
Reasoning
   +
Tools
   +
Execution environment
   +
Permissions
   +
Integrations
   +
Observability
   +
Security controls
   +
Failure handling
```

The engineering challenge is making these components work together reliably.

## 13. Cloud Engineering Connection

Many Cloud and DevOps principles apply directly to Agentic AI:

| Cloud / DevOps | Agentic AI |
|---|---|
| Least privilege | Agent permissions |
| Network controls | Agent network access |
| Containers | Agent isolation |
| Monitoring | Agent observability |
| Logging | Agent action history |
| IAM | Tool authorization |
| CI/CD | Automated workflows |
| Secrets management | Agent credential protection |
| Infrastructure as Code | Reproducible environments |

Agentic AI engineering therefore extends many established infrastructure and security practices.

## 14. Open Source Connection

This experimentation is helping me prepare for open-source contribution and my investigation of the Kyverno AI Assistant project associated with:

`kyverno/kyverno#16665`

The Hermes work has raised practical questions about agent permissions, safe maintainer automation, repository access, human review, auditing, and failure handling.

This document does not claim a completed Kyverno contribution.

## 15. Next Improvements

Future work will focus on:

1. More granular agent permissions.
2. Stronger network restrictions.
3. Better secret isolation.
4. More detailed agent activity logging.
5. Human approval workflows for high-impact actions.
6. Stronger sandbox controls.
7. Better integration health monitoring.
8. GitHub permission scoping.
9. Protection against malicious or untrusted inputs.
10. Recovery mechanisms for unsafe or failed actions.

## Key Takeaway

> **Building an AI agent is an engineering problem, not just an AI problem.**

The model is only one part of the system.

A responsible engineering agent also requires infrastructure, runtime orchestration, tools, sandboxing, permissions, network controls, integrations, observability, security, human oversight, and failure handling.

This work is shaping my development at the intersection of Cloud Engineering, DevOps, Cloud Security, and Agentic AI.
