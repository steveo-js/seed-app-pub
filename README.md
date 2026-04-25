# SEED — AI Workbench for Solution Engineers

A native macOS application for exploring, deploying, and stress-testing AI systems across multiple cloud providers. Connect to **Amazon Bedrock** or **Azure AI Foundry** — all from one tool, with your credentials staying on your machine.

**Latest Version:** v0.1.239

[Download SEED-0.1.239-arm64.dmg](https://github.com/steveo-js/seed-app-pub/releases/download/v0.1.239/SEED-0.1.239-arm64.dmg)

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
| v0.1.239 | April 24, 2026 | Added Amazon QuickSight integration — pick a scenario (Sales Performance, Marketing Analytics, or Operations & SLA), build a full dashboard (IAM role, S3 bucket, data source, SPICE dataset, analysis, and published dashboard), view it in the AWS QuickSight console, and generate simulated activity. Available from the new ◉ QuickSight tab in Pre-Built Scenarios. |
| v0.1.238 | April 24, 2026 | Fixed Q Business chat: removed userId from ChatSyncCommand — anonymous identity applications require userId to be omitted, not set to a string |
| v0.1.237 | April 24, 2026 | Fixed Q Business data source sync: added CloudWatch Logs permissions to the app role (Q Business uses it internally to write sync logs), and made PutRolePolicy idempotent so existing roles get updated permissions automatically |
| v0.1.236 | April 24, 2026 | Fixed Q Business sync failure error detail (now surfaces actual AWS error message instead of generic sync failed), handled INCOMPLETE sync status as success, and added debugLog instrumentation to all 10 Q Business API routes so Q Business operations now appear in the debug log |
| v0.1.235 | April 24, 2026 | Fixed Q Business sync start error: poll data source status until ACTIVE before starting sync job, preventing 'DataSource status is: CREATING' error |
| v0.1.234 | April 24, 2026 | Added Q Business orphan cleanup: 🗑 button in the Q Business sidebar section scans AWS for SEED-QBiz-* IAM roles and seed-qbiz-* S3 buckets not tracked in SEED and deletes them; failed builds now auto-cleanup their partial AWS resources instead of leaving orphans |
| v0.1.233 | April 24, 2026 | Fixed Q Business data source role trust policy: removed ArnLike condition so CreateDataSource validation can succeed before the data source ARN exists |
| v0.1.232 | April 24, 2026 | Fixed Q Business role assumption error: removed ArnLike condition from application role trust policy since no application ARN exists yet at creation time |
| v0.1.231 | April 24, 2026 | Fixed displayName validation error in Q Business — all SDK displayName fields now sanitize spaces to hyphens to match AWS pattern [a-zA-Z0-9][a-zA-Z0-9_-]* |
| v0.1.230 | April 24, 2026 | Fixed Q App creation error: sanitize title to match required pattern [a-zA-Z0-9][a-zA-Z0-9_-]* (spaces replaced with hyphens) |
| v0.1.229 | April 24, 2026 | Added Amazon Q Business support: three pre-built scenarios (HR Policy, IT Self-Service, Enterprise Docs), Q Business chat, traffic generation, and Q Apps |
| v0.1.228 | April 16, 2026 | Fixed KB role assumption errors: trust policy now uses wildcard region and refreshes on reuse; retry loop handles IAM propagation delays |
| v0.1.227 | April 16, 2026 | Fixed manual credentials being ignored when an SSO profile was previously selected |
| v0.1.226 | April 16, 2026 | Improved KB build error messages with specific missing permissions and AWS Console links for all OSS, Bedrock, S3, and IAM steps |
| v0.1.225 | April 16, 2026 | Fix false model-not-available error for inference-profile-only models, improve MCP prepare error messages, add Enable All button and multi-select bulk actions to Models page |
| v0.1.223 | April 6, 2026 | Fixed AgentCore Gateway creation failing with 'already exists' when a previous attempt created the gateway but failed before saving its ID — now recovers by listing existing gateways/targets and reusing them instead of failing. |
| v0.1.222 | April 6, 2026 | Fixed AgentCore Gateway method failing with 'MCP server target does not support current credential provider type' — AWS mcpServer Gateway Targets do not support API_KEY credential injection, so auth is now handled by the Lambda env vars directly. For authenticated backends the Lambda calls the raw MCP URL; for unauthenticated backends it routes through the Gateway URL as before. |
| v0.1.221 | April 6, 2026 | Added two new MCP connection methods — Lambda (Bedrock calls a SEED-deployed Lambda directly) and AgentCore Gateway (Lambda + AWS-managed MCP proxy) — letting users choose per-assignment whether to use SEED Broker, Lambda, or AgentCore Gateway. Connection method selector added to the catalog picker modal and MCP detail view assign UI. Agent badges and MCPView assigned-agent list now show which method each agent uses. |
| v0.1.219 | April 6, 2026 | MCP detail view shows assigned agents with remove/bulk-assign; multi-select mode in agent list for bulk MCP assignment |
| v0.1.218 | April 6, 2026 | Fixed MCP OpenAPI schema validation: handle anyOf/oneOf/allOf, additionalProperties objects, null types, and description length limits |
| v0.1.217 | April 6, 2026 | Fixed MCP SSE parsing for servers like DeepWiki that prefix responses with 'event: message' lines |
| v0.1.216 | April 6, 2026 | MCP Server Catalog page for managing remote MCP servers centrally, with catalog-based assignment to agents via ••• menu picker |
| v0.1.215 | April 6, 2026 | Per-agent MCP configuration via ••• menu, MCP feedback toasts, loading spinners, and 🔌 MCP badge on agent rows |
| v0.1.214 | April 6, 2026 | Added MCP server integration: connect remote MCP servers (Context7, DeepWiki, etc.) to scenario agents via the ⋯ menu; SEED brokers tool calls during chat using RETURN_CONTROL |
| v0.1.213 | April 5, 2026 | Fix: Guardrail test prompts redesigned to reliably trigger Bedrock guardrails — denied topic prompts embed exact prohibited phrases, PROMPT_ATTACK uses clear jailbreak language, MISCONDUCT uses actual criminal/fraud requests |
| v0.1.212 | April 5, 2026 | Fix: Enable Guardrail failing with duplicate name error — route now looks up existing guardrail by name before creating, so re-enabling after a sync wipe reuses the AWS guardrail instead of erroring |
| v0.1.211 | April 5, 2026 | Fixed guardrailId (and tags) being wiped on every agent sync — the sync route now preserves all local-only fields from the existing config record that AWS doesn't return |
| v0.1.210 | April 5, 2026 | Fixed split scenario groups (KBs and agents with mismatched scenarioIds now merged by name); added Expand all / Collapse all buttons to the Assets panel header |
| v0.1.209 | April 5, 2026 | Renamed Apply Guardrail to Enable Guardrail; when a guardrail is already active the menu now shows Disable Guardrail which removes the guardrail config from all agents and deletes the guardrail resource from AWS |
| v0.1.208 | April 5, 2026 | Stable A-Z sort, drag-to-reorder, and pin-to-top for scenario groups, standalone agents, and standalone KBs in the Agents list — order and pins persist in localStorage |
| v0.1.207 | April 5, 2026 | Added per-scenario ⋯ actions menu to scenario cards in the Agents list, consolidating Generate Activity, Apply Guardrail, and Delete All into a single always-visible dropdown button |
| v0.1.206 | April 5, 2026 | Stricter guardrails across all 8 scenarios (raised content filter strengths, added missing filter types); renamed Builds tab and page to Activity |
| v0.1.205 | April 5, 2026 | Generate Activity button is now always visible below the Scenarios/Agent/KB buttons in the Agents column — replaces hidden hover-only buttons |
| v0.1.204 | April 5, 2026 | Synthetic traffic generation — per-scenario 💬 and 💬 All buttons generate realistic chat sessions including guardrail-triggering prompts; progress tracked in builds tray as Traffic records with ⚡ guardrail indicators |
| v0.1.203 | April 5, 2026 | Fixed scenario agents not appearing in their groups — scenarioMatcher now covers all 8 scenarios, and sync recovers original UUID for agents re-joined after being dropped |
| v0.1.202 | April 5, 2026 | Guardrail retrofit for all 8 scenarios — real-company guardrail configs, 🛡 button on scenario groups to apply/re-apply without rebuilding |
| v0.1.201 | April 5, 2026 | Fixed non-SEED agents not syncing to Other section (alias/KB fetch failures no longer silently drop agents); smooth column resize by updating DOM directly during drag instead of re-rendering on every pixel |
| v0.1.200 | April 4, 2026 | Reverted Bedrock Agent model IDs back to inference profiles — on-demand base IDs broke models that require inference profiles (e.g. newer Nova); improved model error messages in agent chat |
| v0.1.199 | April 4, 2026 | Added 40-character minimum validation on agent Instructions field for AWS Bedrock; live counter turns amber and blocks submission until the constraint is met |
| v0.1.198 | April 4, 2026 | Fixed invalid model identifier errors for Bedrock Agents by switching from cross-region inference profiles to on-demand base model IDs; improved error messages in agent chat |
| v0.1.197 | April 3, 2026 | Build page improvements: 90-day history retention, search and status filter, no-delete policy, and red X for interrupted steps after cancellation |
| v0.1.196 | April 3, 2026 | Redesigned guardrail test prompts for Legal Research and AML Operations scenarios with more effective triggers; fixed Use button sending label prefix instead of just the prompt. |
| v0.1.195 | April 3, 2026 | Fixed build cancel not auto-closing tray card and history not showing in Builds tab. Dismiss now hides from tray but keeps in history; cancel auto-hides tray card; added per-item remove in Builds tab. |
| v0.1.194 | April 3, 2026 | Added guardrail-testing prompts to Legal Research and AML Operations scenario guides (legal/financial advice denial, PII triggers, prompt injection); renamed Assets panel from Agents. |
| v0.1.193 | April 3, 2026 | Added Builds tab with full build history (persisted to localStorage), cancel-with-rollback on running builds, and a live running-count badge on the tab so builds are never lost or invisible. |
| v0.1.192 | April 3, 2026 | Fixed agent panel header layout: Scenarios, +Agent, and +KB buttons now move to a dedicated second row with equal flex sizing so they stay properly positioned at any column width. |
| v0.1.191 | April 3, 2026 | Fixed guardrail build errors in Legal Research and AML Operations scenarios: shortened topic definitions to stay under the 200-char AWS limit, and corrected PROMPT_ATTACK output strength to NONE (AWS only applies this filter to inputs). |
| v0.1.190 | April 3, 2026 | Model variety across all scenarios: supervisors and sub-agents now default to diverse models (Claude Haiku, Mistral Large, Llama 3.3, Nova Micro) matched to each agent's role, replacing the previous pattern of llama3-3 for all supervisors and nova-lite for all sub-agents. |
| v0.1.189 | April 3, 2026 | 3 new scenarios: Software Development Lifecycle (hierarchical multi-agent with nested supervisor), Legal Research & Contract Intelligence (AWS Bedrock Guardrails + Code Interpreter), and Financial Crime & AML Operations (4 sub-agents + guardrails + PII protection). Adds type system and build runner support for hierarchical supervisors, guardrails, and Code Interpreter action groups. |
| v0.1.188 | April 3, 2026 | Background builds: scenario builds now run independently in a persistent Builds Tray at the bottom of every screen with step progress, elapsed time, and Open button on completion; toast notifications fire regardless of which tab you are on; multiple concurrent builds supported. |
| v0.1.187 | April 3, 2026 | Fixed KB scenario auto-recovery on sync and supervisor sub-agents not reappearing after config reset — refresh now calls ListAgentCollaborators and detectKBScenario to rebuild both automatically. |
| v0.1.186 | April 3, 2026 | Agents & KBs column is now collapsible — click the ◀ chevron in the header to collapse to a 28px strip showing a vertical Agents label, then click the strip to expand again. |
| v0.1.185 | April 3, 2026 | AI Hub model picker replaced with two-level collapsible tree: Integration (AWS Bedrock, Anthropic Direct) then Vendor (Anthropic, Amazon Nova, Meta/Llama, etc.) — vendors collapsed by default for compact navigation |
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
