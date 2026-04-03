# SEED — AI Workbench for Solution Engineers

A native macOS application for exploring, deploying, and stress-testing AI systems across multiple cloud providers. Connect to **Amazon Bedrock** or **Azure AI Foundry** — all from one tool, with your credentials staying on your machine.

**Latest Version:** v0.1.184

[Download SEED-0.1.184-arm64.dmg](https://github.com/steveo-js/seed-app-pub/releases/download/v0.1.184/SEED-0.1.184-arm64.dmg)

---

## What SEED Does

### AI Hub Chat
Connect SEED to a JetStream AI Hub (LiteLLM / OpenAI-compatible) to test virtual key access, available models, MCP server integrations, and guardrail policies — all without writing code. Enter your hub address, port, and API key once; SEED fetches the full model list and streams responses in real time. Use this tab to verify that virtual keys have the right model permissions, that MCP tools are wired up correctly, and that guardrails are triggering as expected.

### AWS Bedrock Models
Browse the full Bedrock catalog, enable additional models on demand, and manage model access — all without leaving the app. Ships with six built-in models (Nova Micro, Nova Lite, Claude Sonnet 4, Claude Haiku 4.5, Llama 3.3 70B, Mistral Large); add any catalog model with a single click.

### AWS Bedrock Agents
Create, configure, and chat with Amazon Bedrock Agents. Supports:
- **Knowledge Base attachment** — ground agents in your documents via OpenSearch Serverless vector stores
- **Supervisor agents** — orchestrate multiple sub-agents with live activity tracing
- **Multi-agent scenarios** — pre-built scenario templates that provision a full supervisor + sub-agent mesh in one click

### Azure AI Foundry
Connect to Azure AI Foundry via Azure CLI login (with auto-provisioning of resource groups, AI Services accounts, and model deployments) or by entering an existing endpoint manually. Supports Azure Agents (OpenAI Assistants API), Azure Knowledge Bases (vector stores), and multi-agent scenarios mirroring the AWS feature set.

### Knowledge Bases
Create knowledge bases backed by Amazon OpenSearch Serverless (AWS) or Azure vector stores. Upload documents, trigger ingestion, browse file contents, and attach to agents — all from the UI.

### Attack Panel
A built-in red-team toolkit for testing AI system resilience. Includes pre-built attack prompts organized by category (prompt injection, jailbreaks, data extraction, role manipulation, and more) plus scenario-specific attack packs that align with the active multi-agent scenario.

### Multi-Agent Scenarios
Pre-built scenario templates that stand up realistic multi-agent environments for demos and security research:
- **Healthcare** — patient triage, clinical decision support
- **Financial Services** — fraud analysis, compliance review
- **Legal** — contract review, case research
- **Customer Support** — escalation routing, knowledge retrieval

---

## How to Install

1. Download the DMG above
2. Open it and drag **SEED** into your **Applications** folder
3. Eject the disk image
4. Open **SEED** from Applications

> **If macOS shows "damaged and can't be opened":** Open Terminal and run `xattr -cr /Applications/SEED.app`, then launch the app normally. This removes the internet quarantine flag macOS applies to downloaded apps.

**System requirements:** macOS 12 Monterey or later · Apple Silicon (arm64) · Internet connection

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| v0.1.184 | April 3, 2026 | AI Hub model dropdown now grouped by provider (Anthropic Direct, Anthropic via Bedrock, Amazon Nova, Meta/Llama, Mistral, Cohere, AI21, DeepSeek) based on model ID prefix |
| v0.1.183 | April 3, 2026 | Scenario auto-detection: syncing AWS agents now restores scenario links by name pattern; new scan button and manual Link to Scenario menu option for manual/auto re-linking of orphaned agents and KBs |
| v0.1.182 | April 3, 2026 | Custom Groups: tag any agent or KB into named groups via the row action menu — shows as a new My Groups section in the sidebar, independent of scenarios |
| v0.1.181 | April 3, 2026 | Agent sync fixes: restore createdBySeed via resource prefix matching and recover isSupervisor from AWS agentCollaboration field, so scenario agents group correctly and supervisor panels reappear after a config reset |
| v0.1.180 | April 2, 2026 | Fix Guide button disappearing for scenario agents with older template names |
| v0.1.179 | April 1, 2026 | Resizable Agents list column — drag the right edge to resize between 200–520 px |
| v0.1.178 | April 1, 2026 | Resizable Scenario Guide panel with auto-scaling text, collapsible Sub-Agents panel, and global interface text size setting in Settings |
| v0.1.177 | April 1, 2026 | On launch, automatically show the update modal when a new version is available; footer button now reads Later instead of Close when an update is present |
| v0.1.176 | April 1, 2026 | Renamed Chat tab to AI Hub Chat |
| v0.1.175 | March 31, 2026 | Fixed Scenario Guide panel not opening — agent.scenarioId is a UUID instance key, now correctly resolves scenario template data by scenarioName |
| v0.1.174 | March 31, 2026 | Added Scenario Guide panel and empty state — scenario agents now surface KB reference data, agent roles, and example prompts directly in the chat UI so users know exactly what to ask |
| v0.1.173 | March 28, 2026 | Improved error messages: slow failures now diagnosed as firewall/security-group blocks rather than connection refused |
| v0.1.172 | March 28, 2026 | Fixed IP address HTTP/HTTPS detection; better error messages; Test button in setup form; badge turns red on failed check |
| v0.1.171 | March 28, 2026 | Added full debug logging for AI Hub chat; timeout increased to 30s |
| v0.1.170 | March 28, 2026 | Added Fetch Models and Check Connection buttons to the Chat toolbar |
| v0.1.169 | March 28, 2026 | Fix hub connect: test before save, HTTPS default for public hostnames, cache:no-store on hub fetches; fix stale update notification |
| v0.1.168 | March 28, 2026 | Added AI Hub Chat tab — connect to any JetStream AI Hub (LiteLLM/OpenAI-compatible) |
| v0.1.167 | March 28, 2026 | Added Claude Chat tab with direct Anthropic API integration, named proxy profiles for routing, and Claude section in Settings |
