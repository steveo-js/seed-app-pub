# SEED — AI Workbench for Solution Engineers

A native macOS application for exploring, deploying, and stress-testing AI systems across multiple cloud providers. Connect to **Amazon Bedrock**, **Azure AI Foundry**, or **Claude (Anthropic API)** — all from one tool, with your credentials staying on your machine.

**Latest Version:** v0.1.175

[Download SEED-0.1.175-arm64.dmg](https://github.com/steveo-js/bedrock-app-pub/releases/download/v0.1.175/SEED-0.1.175-arm64.dmg)

---

## What SEED Does

### Claude Chat (Anthropic API)
Chat directly with Claude models (Opus 4.6, Sonnet 4.6, Haiku 4.5) using an API key from console.anthropic.com — no AWS or Azure account needed for this tab. Route traffic through a named proxy profile (URL or IP:Port) with automatic auth detection (Bearer token or HTTP Basic).

### AWS Bedrock Chat & Models
Chat with Amazon Bedrock models including Nova Micro, Nova Lite, Claude Sonnet 4, Claude Haiku 4.5, Llama 3.3 70B, and Mistral Large. Browse the full Bedrock catalog, enable additional models on demand, and manage model access — all without leaving the app.

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
| v0.1.175 | March 31, 2026 | Fixed Scenario Guide panel not opening — agent.scenarioId is a UUID instance key, now correctly resolves scenario template data by scenarioName |
| v0.1.174 | March 31, 2026 | Added Scenario Guide panel and empty state — scenario agents now surface KB reference data, agent roles, and example prompts directly in the chat UI so users know exactly what to ask |
| v0.1.173 | March 28, 2026 | Improved error messages: slow failures now diagnosed as firewall/security-group blocks rather than connection refused |
| v0.1.172 | March 28, 2026 | Fixed IP address HTTP/HTTPS detection; better error messages; Test button in setup form; badge turns red on failed check |
| v0.1.171 | March 28, 2026 | Added full debug logging for AI Hub chat; timeout increased to 30s |
| v0.1.170 | March 28, 2026 | Added Fetch Models and Check Connection buttons to the Chat toolbar |
| v0.1.169 | March 28, 2026 | Fix hub connect: test before save, HTTPS default for public hostnames, cache:no-store on hub fetches; fix stale update notification |
| v0.1.168 | March 28, 2026 | Added AI Hub Chat tab — connect to any JetStream AI Hub (LiteLLM/OpenAI-compatible) |
| v0.1.170 | March 28, 2026 | AI Hub replaces proxy in Claude routing UI; unified address+port input (default 4000), no http:// prefix in stored/displayed values |
| v0.1.169 | March 28, 2026 | Added IP:Port proxy input mode (default port 4000) with URL preview; rewrote public README to reflect full SEED feature set |
| v0.1.169 | March 28, 2026 | Added URL vs IP:Port mode toggle in proxy setup (default port 4000) with assembled-URL preview |
| v0.1.168 | March 28, 2026 | Claude direct API chat tab with proxy profiles, proxy auth detection (bearer/basic auto-detect), AWS/Azure toggle hidden on Chat tab |
| v0.1.167 | March 28, 2026 | Added Claude Chat tab with direct Anthropic API integration, named proxy profiles for routing, and Claude section in Settings |
