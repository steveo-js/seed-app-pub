# SEED — AI Workbench for Solution Engineers

A native macOS application for exploring, deploying, and stress-testing AI systems across multiple cloud providers. Connect to **Amazon Bedrock** or **Azure AI Foundry** — all from one tool, with your credentials staying on your machine.

**Latest Version:** v0.1.367

[Download SEED-0.1.367-arm64.dmg](https://github.com/steveo-js/seed-app-pub/releases/download/v0.1.367/SEED-0.1.367-arm64.dmg)

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
| v0.1.367 | October 8, 2026 | Populate Data for agent scenarios with per-scenario limits; per-gateway limits and $ budgets in Chat Populate Data |
| v0.1.366 | October 8, 2026 | Fix AI Hub chat using the wrong API: Anthropic models now use /v1/messages, OpenAI/Bedrock models use /v1/responses, with automatic fallback |
| v0.1.365 | August 28, 2026 | Removed Amazon Q Business, Amazon QuickSight, and Amazon Quick (Quick Flows) capabilities. Existing AWS resources are untouched and must be cleaned up in the AWS console. |
| v0.1.364 | August 26, 2026 | Populate Data — run Attacks, Guardrail Tests and Usage Spike across up to 5 gateways at once from the Chat menu, populating the JetStream console from multiple virtual keys |
| v0.1.363 | August 25, 2026 | Guardrail tests move from a blocking modal to a side panel beside the conversation. Run any test individually from its row, or run all 28 as a cancellable background task reported in the Activity tray. Every prompt and response now stays in the chat, because tests are sent single-turn rather than clearing the conversation between them |
| v0.1.362 | August 25, 2026 | Setup moves into the account menu above Check for Updates, leaving the profile icon as the only control on the right-hand side of the header |
| v0.1.361 | August 25, 2026 | The account menu's AWS and Azure connections are now collapsible cards — click to expand details and the switch/re-login actions. Both start collapsed so the whole menu fits without scrolling, and a provider whose credentials need attention opens itself |
| v0.1.360 | August 25, 2026 | Header top-right consolidated into one account menu: the profile icon is now rightmost and holds Settings, Check for Updates and Help alongside AWS and Azure switch/re-login. Adds AWS Re-login with SSO, keeps it available when credentials have expired, makes the status dot honest about a dead session, and fixes the menu opening behind the Builds tray |
| v0.1.359 | August 25, 2026 | Renames the AI Hub Manager tab to Gateways across the UI, in-app help, user guide and README, including the 31 error messages and empty-state links that point users at it. Naming only, no behaviour change |
| v0.1.358 | August 25, 2026 | Renames the AI Hub Chat tab to just Chat across the UI, in-app help, user guide and README. AI Hub Manager is unchanged. Naming only, no behaviour change |
| v0.1.357 | August 25, 2026 | AI Hub Chat: the Clear button moves from the top header to immediately right of Send, beside the conversation it acts on |
| v0.1.356 | August 25, 2026 | AI Hub Chat cleanup: Attacks, Guardrail Tests, Usage Spike, Check Connection, Reset Connection and Disconnect all consolidated into one grouped dropdown, leaving the toolbar at profile, model, Fetch Models and the menu. Kill is removed from AI Hub Chat — Reset Connection already did everything it did, and it never stopped a running usage spike. Kill is unchanged in agent chats |
| v0.1.355 | August 24, 2026 | Usage spike now sends realistic, varied work — eight back-office tasks with generated records instead of one instruction repeated — and every call shows the real prompt and reply, both in the chat transcript (long prompts behind a show-full-prompt toggle) and printed to the terminal when SEED is launched from a shell |
| v0.1.354 | August 24, 2026 | Fixes the AI Hub Chat usage-spike dialog being headed 'Trigger Runaway' — it now reads 'Usage Spike' there and keeps 'Trigger Runaway' on a harness agent |
| v0.1.353 | August 24, 2026 | Adds the deliberate token-usage spike to AI Hub Chat, governed inline by JetStream with token counts from the Hub's own usage accounting. Also fixes the burst planner collapsing to hundreds of tiny calls on a fast transport, and concurrent workers racing past the target: a 200k-token spike went from 165 calls in 54s to 3 calls in 8s, and from 50% overshoot to 5% |
| v0.1.352 | August 24, 2026 | Fixes a data-loss bug where every refresh silently deleted AgentCore Harness agents from SEED's config, leaving orphaned billable harnesses in AWS; sync now preserves all non-Classic records and recovers missing harness records from AWS. The asset-type filter is renamed Type and separates Classic / AgentCore Runtime / AgentCore Harness / Knowledge base / Q Business / QuickSight / Quick |
| v0.1.351 | August 24, 2026 | Agents page redesign: one searchable, filterable asset list with user-chosen grouping; fixes the status dot that showed 28 of 55 agents as perpetually pending, Collapse-all missing 9 of 11 sections, models with a version dot rendering as a bare number, and Q Business apps falling into an Unknown account group |
| v0.1.350 | August 24, 2026 | Runaway Autonomous Agent scenario on AgentCore Harness: knowledge bases reachable as an audited MCP tool, and an operator-driven token usage spike with live measured telemetry and cost estimates. |
| v0.1.349 | August 22, 2026 | AgentCore Harness: a third agent platform on AWS Bedrock AgentCore Harness (the managed agent loop) with streaming replies, tool-use traces, and MCP tools via the shared tools gateway. |
| v0.1.348 | August 18, 2026 | Fixes preset seeding so an MCP server already in the catalog is adopted rather than skipped, which left it permanently unattached to the tools gateway. Also records end-to-end verification of MCP tools on all three routing modes against live AWS. |
| v0.1.347 | August 18, 2026 | Adds MCP tools for AgentCore Runtime agents: an account-level AgentCore Gateway in MCP mode fronting AWS Knowledge, DeepWiki and Context7, plus a bounded tool-calling loop in the generated Python covering all three routing modes. Tool schemas are baked at deploy, credentials stay in the AWS vault. |
| v0.1.346 | August 18, 2026 | Scenario builds and agent saves now verify every model against the bound AI Hub before creating anything — that the hub serves it, and for gateway routing that the gateway will forward it — reporting failures per agent with the hub's equivalent model named. An unreachable hub warns rather than blocks. |
| v0.1.345 | August 18, 2026 | Hub- and gateway-routed agents now choose models from the AI Hub's own list instead of SEED's Bedrock catalog, with gateway-incompatible ids greyed out; blocked gateway deploys name the hub's colon-free equivalent for the same model where one exists. |
| v0.1.344 | August 18, 2026 | Gateway-routed agents on Bedrock-style model ids (amazon.nova-lite-v1:0) failed with 400 at the gateway, which screens inbound model ids against a character set with no colon. SEED now refuses such deploys with a clear message, declares only routable models on the target, and attributes the error to the gateway rather than the Hub. |
| v0.1.343 | August 18, 2026 | Fixes the gateway's Authorization header (credentialPrefix had a trailing space, producing 'Bearer  <key>' and a 401 from the hub), and stops reporting a failed inference target as a successful provision — provisioning now waits for the target and surfaces AWS's own failure reasons. |
| v0.1.342 | August 17, 2026 | Gateway provisioning: declare Bedrock-style model ids (amazon.nova-pro-v1:0) as glob patterns, since AgentCore's model format forbids the colon that made CreateGatewayTarget fail validation. Patterns are deduplicated, and the hub card reports which models were globbed or dropped. |
| v0.1.341 | August 17, 2026 | Gateway preflight now resolves hub hostnames through public DNS (DoH, then public resolvers) instead of the system resolver, fixing false carrier-grade-NAT rejections under split-horizon DNS; the TLS probe is pinned to the public address; unverifiable resolution warns instead of blocking; certificate failures are named precisely. |
| v0.1.340 | August 17, 2026 | Fix AgentCore agents failing to start when instructions span multiple lines (reported as a misleading init timeout); add Redeploy to repair already-deployed agents; surface the real runtime traceback; stop the gateway preflight passing hubs AWS cannot route to |
| v0.1.339 | August 17, 2026 | AI Hub Manager now lists AgentCore agents with no hub as 'No AI Hub Configured', kept distinct from agents whose hub simply wasn't recorded |
| v0.1.338 | August 17, 2026 | AI Hub Manager tab for central hub management, plus per-build AI Hub selection so AgentCore deployments bind to a hub you choose instead of whichever was active |
| v0.1.337 | August 14, 2026 | AgentCore Gateway routing: front the JetStream AI Hub with an AWS AgentCore Gateway inference target so the Hub becomes a discoverable AWS resource and the Hub API key moves into the AgentCore token vault |
| v0.1.336 | August 6, 2026 | Group the Assets panel by AWS account in AWS mode — collapsible per-account sections (account name + id), the connected account first and marked 'current', so it's clear at a glance which agents/scenarios/KBs live in which account |
| v0.1.335 | August 5, 2026 | Stamp AgentCore Runtime agents with jetstream:* relationship tags (model, inference profile, knowledge base, sub-agent collaborators, scenario, routing mode) so JetStream's connector can graph agent relationships in its blueprints / AI manifest the way it does for Classic Bedrock Agents |
| v0.1.334 | August 5, 2026 | Edit AgentCore Runtime agents in place — change model, instructions, description, and JetStream routing without delete-and-recreate (uses the real AgentCore UpdateAgentRuntime API; supervisors keep their sub-agents) |
| v0.1.333 | August 5, 2026 | Add a read-only Model-Invocation Logging detection step to the AWS setup flow — shows whether Amazon Bedrock model-invocation logging is enabled for the account/region (covering both Classic and AgentCore Runtime agents), with destinations and data types; detection only, configured in the environment |
| v0.1.332 | August 5, 2026 | Readable AWS resource names for AgentCore Runtime agents — runtime and IAM role now use the agent's friendly name (plus a short id) instead of an opaque UUID, so they're identifiable in the AWS console |
| v0.1.331 | August 5, 2026 | Add Sensitive Data Exfiltration pre-built scenario (Phase 3b): supervisor + 3 KB-grounded records agents (customer PII, employee payroll, infrastructure secrets), a DLP guardrail, and an OWASP LLM attack pack — a governance-focused POV scenario |
| v0.1.330 | August 5, 2026 | Phase 3a: synthetic traffic generation + Attack Panel now work on AgentCore Runtime scenarios; traffic gen detects JetStream AI Hub inline blocks |
| v0.1.329 | August 4, 2026 | Multi-agent AgentCore Runtime scenarios (Phase 2) — build a full supervisor + KB-grounded sub-agent scenario on the real AWS Bedrock AgentCore Runtime, with a per-scenario JetStream routing toggle (AI Hub inline governance vs Bedrock direct + AWS-native telemetry); supervisor delegates via the real InvokeAgentRuntime data-plane call |
| v0.1.328 | August 4, 2026 | Remove account model-invocation logging opt-in (JetStream connector already provisions it); routing toggle unchanged |
| v0.1.327 | August 4, 2026 | JetStream governance routing for AgentCore Runtime agents (hub inline vs bedrock direct + account model-invocation logging opt-in) |
| v0.1.326 | August 3, 2026 | Add AgentCore Runtime badge to knowledge base rows, matching existing AWS/RAG badge style |
| v0.1.325 | August 3, 2026 | Fully remove Custom Lambda agent platform code (Classic and AgentCore Runtime remain); real AgentCore Gateway feature unaffected |
| v0.1.324 | August 3, 2026 | Remove Custom Lambda as a creation option (Classic and AgentCore Runtime only going forward); existing Custom Lambda agents/scenarios unaffected |
| v0.1.323 | August 3, 2026 | Add early-access AgentCore Runtime support (real AWS Bedrock AgentCore service); rename Custom Lambda platform for accuracy |
| v0.1.322 | August 2, 2026 | Add AgentCore badge to distinguish AgentCore vs Classic agents/scenarios/KBs in the Agents list |
| v0.1.321 | August 2, 2026 | Fix AgentCore inference-profile model resolution and knowledge base retrieval parameter |
| v0.1.320 | August 2, 2026 | Fix AgentCore agents never actually executing (dependency packaging + wrong API); fix silently swallowed chat errors |
| v0.1.319 | August 2, 2026 | Fix S3 Vectors KB ingestion failing on reasonably-sized document chunks (2048-byte filterable metadata limit) |
| v0.1.318 | August 2, 2026 | Surface real ingestion failure reasons instead of a generic error in scenario builds |
| v0.1.317 | August 1, 2026 | Fix AgentCore chat failing due to required agentAliasId that AgentCore agents don't have |
| v0.1.316 | July 31, 2026 | Critical fix: stop /api/agents/sync from silently deleting AgentCore agents from local config |
| v0.1.315 | July 31, 2026 | Fix AgentCore agent creation failing with 'role cannot be assumed by Lambda' (IAM propagation delay) |
| v0.1.314 | July 31, 2026 | Fix AgentCore agent creation failing with 'specified bucket does not exist' |
| v0.1.313 | July 31, 2026 | Add AgentCore scenario building for multi-agent LangGraph setups |
| v0.1.298 | July 31, 2026 | Improved Bedrock Agents error handling with actionable guidance for maintenance mode errors |
| v0.1.297 | July 14, 2026 | Added AgentCore platform support with automatic code generation for LangGraph and CrewAI, Lambda deployment with S3 versioning, and dual-platform agent creation UI |
| v0.1.268 | July 10, 2026 | Fix migration losing track of its target knowledge base/data source on sync, which caused duplicate-name errors on retry |
| v0.1.267 | July 10, 2026 | Fix shared KB IAM role S3 access being scoped to a single bucket, which silently broke other knowledge bases' S3 access whenever the role was set up for a different one |
| v0.1.266 | July 9, 2026 | Fix S3 Vectors ingestion failures (missing vector bucket policy), surface real ingestion failure reasons, and add a Cancel button to the bulk migration wizard |
| v0.1.265 | July 9, 2026 | Add Migrate All to S3 Vectors bulk migration for AWS scenario knowledge bases, skipping any already migrated |
| v0.1.264 | July 9, 2026 | Fix migration to S3 Vectors failing with a data-source name collision against the old knowledge base's still-existing data source |
| v0.1.263 | July 9, 2026 | Fix migration to S3 Vectors failing on knowledge bases discovered via AWS sync (blank cached S3 bucket name produced an invalid ARN) |
| v0.1.262 | July 9, 2026 | Add S3 Vectors knowledge-base storage backend with migration wizard from OpenSearch Serverless |
| v0.1.261 | July 6, 2026 | Fix ⋯ menu viewport clipping on small screens; surface raw hub error messages in chat |
| v0.1.260 | June 19, 2026 | Guardrail test panel: added Setup column as expandable rows — click any test to reveal its full guardrail configuration instructions, expected behavior, and hub response (once complete) |
| v0.1.259 | June 19, 2026 | Added AI Hub Guardrail Test Suite: 28-prompt automated sequence (Blocked Keywords, PII, Prompt Injection, Regex, Sensitive Data) with live progress bar, category badges, auto-reset between tests, and Stop button |
| v0.1.258 | May 22, 2026 | AI Hub Chat: ⋯ menu with Reset Connection and Disconnect, plus correct typing indicator (no more 'Agent Activity / orchestrating') |
| v0.1.257 | May 21, 2026 | AI Hub: self-signed HTTPS checkbox for direct-to-IP hubs + clearer TLS error messages |
| v0.1.256 | May 12, 2026 | Portable-app pivot (no startup setup check) + multi-profile AI Hub support |
| v0.1.256 | May 12, 2026 | Setup wizard no longer auto-opens on launch; use the Setup button in the header |
| v0.1.255 | May 8, 2026 | Fix manual AWS credentials login (cache-related 'AWS credentials not found' error), accept ASIA temporary keys |
| v0.1.254 | May 8, 2026 | Default AI Hub setup port changed from 4000 to 443 |
| v0.1.253 | May 6, 2026 | Fix BedrockAgentRole trust policy refresh on existing roles (fixes 'Bedrock can't access role' in partner accounts) and add named profile support for manual AWS credentials |
| v0.1.252 | May 1, 2026 | Move AWS/Azure cloud toggle from header into Agents and Models pages where it is contextually relevant |
| v0.1.251 | May 1, 2026 | Fix hub model picker: claude-* models now correctly grouped under Anthropic instead of OpenAI — name-pattern matching added for bare IDs that gateways stamp with owned_by=openai |
| v0.1.250 | May 1, 2026 | Fix hub model picker: slash-prefix ID now checked before owned_by so LiteLLM's generic owned_by=openai no longer groups Anthropic and Azure Foundry models under OpenAI |
| v0.1.249 | May 1, 2026 | Hub model picker now correctly groups models by provider (OpenAI, Azure/Microsoft Foundry, Anthropic Direct, etc.) using owned_by — previously all non-Bedrock models were mislabeled as Anthropic Direct |
| v0.1.248 | April 28, 2026 | Q Business scenario confirm screen now shows full preview before building — AWS resources grid, Chat Controls guardrail settings (scope, blocked phrases, system message override), Response Persona details (identity, tone, audience, instructions), and Plugin info |
| v0.1.247 | April 28, 2026 | Added admin controls and response persona to Q Business scenarios — each build applies Chat Controls (ENTERPRISE_CONTENT_ONLY scope, blocked phrases, hallucination reduction, creator mode disabled) and a Chat Response Configuration with scenario-specific tone, identity, and instructions; surfaced via a 🛡 Controls badge in the chat panel |
| v0.1.246 | April 28, 2026 | Enhanced Q Business scenarios with Q Web Experience and Q Plugin — all 3 scenarios now provision a hosted web chat UI and a CUSTOM-type Q Plugin with inline OpenAPI 3.0 schema; added Build dropdown to consolidate scenario launcher buttons; Amazon Quick Flows now uses Bedrock ConverseCommand for card generation instead of Q Apps |
| v0.1.245 | April 28, 2026 | Collapsed the 4 scenario toolbar buttons (Scenarios, Q Apps, QuickSight, Quick) into a single ▾ Build dropdown to free up space in the Agents sidebar toolbar |
| v0.1.244 | April 28, 2026 | Fixed Amazon Quick Flows: replaced PredictQAppCommand (requires IAM Identity Center) with Bedrock/Claude to generate workflow cards — Q Business app is still provisioned as a real AWS resource, Q App and session steps are now simulated |
| v0.1.243 | April 27, 2026 | Fixed Unauthorized on PredictQAppCommand: use actual IAM caller ARN as Q Apps userId, move user-context header to finalizeRequest step so it persists after SigV4 signing, improve error logging with error name and HTTP status |
| v0.1.242 | April 27, 2026 | Fixed Unauthorized error on PredictQAppCommand — Q Apps API requires Amazon-QApps-UserContext header on every request; added middleware to QAppsClient to inject it automatically |
| v0.1.241 | April 27, 2026 | Added Amazon Quick Flows integration — uses PredictQAppCommand to AI-generate Q App workflows from natural language descriptions, deploys them as interactive Q Apps on a minimal Q Business application, and adds an ⚡ Amazon Quick tab in the ScenarioModal with 3 scenarios (Customer Intake, Market Research, Incident Report) |
| v0.1.240 | April 27, 2026 | Fixed QuickSight subscription check timing out on accounts that already have QuickSight — the status check was requiring the exact string ACCOUNT_SUBSCRIBED but AWS returns other strings (e.g. EXISTING_SUBSCRIPTION_ACCOUNT) for active accounts; now any non-failed status is treated as ready |
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
