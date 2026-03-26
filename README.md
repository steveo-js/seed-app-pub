# Bedrock Chat — Releases

A native macOS application that connects to AI models on Amazon Bedrock. Your AWS credentials stay on your machine and are never sent anywhere except directly to AWS.

**Latest Version:** v0.1.148

[Download BedrockChat-0.1.90-arm64.dmg](https://github.com/steveo-js/bedrock-app-pub/releases/download/v0.1.90/BedrockChat-0.1.90-arm64.dmg)

## How to Install

1. Download the DMG above
2. Open it and drag **BedrockChat** into your **Applications** folder
3. Eject the disk image
4. Open **BedrockChat** from Applications

> **First launch:** If macOS shows "unidentified developer", right-click the app, choose **Open**, then click **Open** again.

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| v0.1.148 | March 26, 2026 | Auto-repair project endpoint on 'does not exist' errors — discovers correct AI Services account from Hub ARM connections |
| v0.1.147 | March 26, 2026 | Fixed 'The project does not exist.' error — normalize cognitiveservices.azure.com to services.ai.azure.com at all layers (provision, save-credentials, createProjectClient) |
| v0.1.146 | March 26, 2026 | Fixed project-does-not-exist error when creating agents — Hub creation now correctly links the AI Services account in all fallback paths, and project endpoints are resolved from Hub connections rather than assumed from config |
| v0.1.145 | March 26, 2026 | Added existing Foundry project picker to setup wizard Step 3 and a lightweight Re-login with CLI re-auth flow accessible from the profile popover |
| v0.1.144 | March 26, 2026 | Profile popover now shows Azure account name and resource group so you always know which Azure resources SEED is connected to |
| v0.1.143 | March 26, 2026 | Azure Models view now shows which AI Services account and resource group you're looking at |
| v0.1.142 | March 26, 2026 | Setup wizard now auto-creates AI Foundry Hub and Project after provisioning AI Services — no more copying a project endpoint URL from the portal |
| v0.1.141 | March 26, 2026 | Add AI Foundry Resources manager: create/delete hubs and projects, switch active project, all from within SEED |
| v0.1.140 | March 26, 2026 | Show connected Azure project name in Agents sidebar so users know which AI Foundry project their agents live in |
| v0.1.139 | March 26, 2026 | Fixed Open in AI Foundry link — was generating invalid per-agent URL path causing page not found |
| v0.1.138 | March 26, 2026 | Azure agents now link directly to the agent in AI Foundry (ai.azure.com) with a wsid deep link, and the agent list shows the Azure agent ID for easy cross-reference |
| v0.1.137 | March 26, 2026 | Fixed Azure AI Foundry provisioning: wrong extension name (azure-ai-ml → ml), invalid --no-wait false syntax, graceful --ai-services fallback, REST API fallback if ml extension unavailable, real region detection from resource group |
| v0.1.136 | March 26, 2026 | Fixed Azure Foundry setup modal not appearing on agent creation failure — stale React state bug caused the Resource not found error check to always read null |
| v0.1.135 | March 26, 2026 | Added debug mode toggle (Settings + Help → Debug Log) and extended diagnostic logging to cover chat, agents, agent chat, knowledge bases, and Azure agents — not just Azure HTTP calls |
| v0.1.134 | March 26, 2026 | Auto-provision Azure AI Foundry Hub + Project when Agents tab detects missing project endpoint — customizable names, live progress, auto-retry agent creation |
| v0.1.133 | March 25, 2026 | Agent-only Azure models (gpt-5, o3) no longer fail the health check — show as agent-only badge, added to verified deployments, work in Agents tab |
| v0.1.132 | March 25, 2026 | Fix health check 404 for project-scoped Azure models (gpt-5, o3) — use full AI Foundry project endpoint for inference instead of stripping to account root |
| v0.1.131 | March 25, 2026 | Fix Azure project endpoint not saved after wizard — auto-populate, auto-derive, and save correctly from Switch Azure Profile |
| v0.1.130 | March 25, 2026 | Fixed: Continue anyway in Azure test step no longer loops back to provider selection. Three root causes fixed: azureSetupComplete now always written on test completion; status-stream now recognizes project endpoints; page.tsx no longer re-checks via the AWS-only status route after wizard completion. |
| v0.1.129 | March 25, 2026 | Azure wizard: failed deployments no longer block completion (Continue anyway button added); verify step now shows all pass/fail results clearly; project endpoint pre-filled from saved config on re-entry. |
| v0.1.128 | March 25, 2026 | Improved error message when a model deployment doesn't exist: now shows 'Deployment not found — make sure it is deployed in your Azure AI Services account' instead of the raw 404. |
| v0.1.127 | March 25, 2026 | Fixed 404 on all Azure model verification: inference calls were going to the project management sub-path (/api/projects/{project}/openai/...) instead of the account-level inference endpoint. Now strips /api/projects/... from the project endpoint URL before constructing the AzureOpenAI client. |
| v0.1.126 | March 25, 2026 | Fixed 404 during Azure connection test (models.list not supported at AI Foundry project endpoints — now treated as success). Added Debug Log panel in Help showing exact URLs, status codes, and response bodies for every Azure HTTP call. |
| v0.1.124 | March 25, 2026 | Fixed 400 API version not supported when testing Azure connections with API key auth. Corrected apiVersion from 2025-04-01-preview (invalid) to 2025-11-15-preview, matching the version used internally by the Azure AI Projects SDK. |
| v0.1.123 | March 25, 2026 | Fixed Missing API Key Header Name error when testing Azure connections with API key auth. The API key + project endpoint path now uses AzureOpenAI directly with apiVersion 2025-04-01-preview, resolving both this error and the original 400 API version not supported error for GPT-5 era models. |
| v0.1.122 | March 25, 2026 | Fixed 400 API version not supported error when verifying GPT-5/mini/nano models in Azure setup wizard |
| v0.1.121 | March 24, 2026 | Migrated Azure agents to native Azure AI Foundry Agent Service — agents now appear in AI Foundry portal under Build and Customize → Agents |
| v0.1.120 | March 24, 2026 | Migrated Azure backend to AI Foundry: agents now appear in Azure AI Foundry portal (Build & Customize → Agents). Added project endpoint step in setup wizard. |
| v0.1.119 | March 24, 2026 | Fix: agent create/edit in Azure mode was routing to AWS Bedrock; now correctly uses Azure OpenAI Assistants API |
| v0.1.118 | March 24, 2026 | Azure flow revamp: vector store management, step-by-step scenario builds with progress UI, supervisor function tools, Azure terminology (Vector Store/Deployment/Assistant) throughout |
| v0.1.117 | March 24, 2026 | Fix Azure pivot link to use correct Azure Portal URL for the OpenAI resource |
| v0.1.116 | March 24, 2026 | Add Open in Console pivot links to agent and KB action menus for both AWS and Azure |
| v0.1.115 | March 24, 2026 | Replace inline action buttons with a three-dot popout menu so agent/KB names are no longer truncated |
| v0.1.114 | March 24, 2026 | Add claim/unclaim to manually move agents and KBs between My Standalone and Other sections |
| v0.1.113 | March 24, 2026 | Agents panel reorganized into My Scenarios / My Standalone Agents & KBs / Other Agents & KBs — each collapsible, ownership tracked via createdBySeed flag |
| v0.1.112 | March 24, 2026 | Switch AWS Profile button moved into AWS section of profile popover, matching Azure layout |
| v0.1.111 | March 24, 2026 | Switch Azure Profile button in profile popover — update endpoint, API key, or Entra ID creds with inline connection test |
| v0.1.110 | March 24, 2026 | Profile popover now shows Azure connection info (endpoint + deployments) alongside AWS; visible whenever any provider is connected |
| v0.1.109 | March 24, 2026 | Dynamic launch check: startup now checks only configured providers (AWS-only, Azure-only, or both); ready if either passes |
| v0.1.108 | March 23, 2026 | Hide Add Model button in agent builder when Azure cloud is active |
| v0.1.107 | March 23, 2026 | Azure multi-agent scenarios, model filtering in builders, release notes preservation fix |
| v0.1.106 | March 23, 2026 | Fix AWS enabled model count to include always-on built-in models |
| v0.1.105 | March 23, 2026 | Consistent model count header: both AWS and Azure now show X enabled · Y in catalog |
| v0.1.104 | March 23, 2026 | Deploy & Enable any Azure model catalog entry directly from the Models page |
| v0.1.103 | March 23, 2026 | Fix Azure catalog: CLI list-models response fields are top-level not nested; all 215 models now load |
| v0.1.102 | March 23, 2026 | Fix Azure catalog loading for all setup paths; fix AWS model count to show full catalog total |
| v0.1.101 | March 23, 2026 | Show full Azure model catalog (~172 models) on Models page; fix cloud-specific model counts in header |
| v0.1.100 | March 23, 2026 | Fix Azure agents view showing AWS content; Azure models page now shows full deployment catalog with Enable/Remove per model |
| v0.1.99 | March 23, 2026 | Cloud toggle: AWS/Azure pill in header filters Chat, Agents, and Models to one cloud at a time; agent cloud badges added |
| v0.1.98 | March 23, 2026 | Azure model browser: setup wizard and Models page now let you browse, add, and remove Azure AI Foundry deployments directly |
| v0.1.97 | March 23, 2026 | Setup wizard now detects whether AWS CLI and Azure CLI are installed and shows install instructions with links when either is missing, before the user attempts SSO or az login. |
| v0.1.96 | March 23, 2026 | Setup wizard now loads available models directly from your Azure account — no more quota errors from hardcoded defaults; failed deployments show a Load available models button for in-wizard retry. |
| v0.1.95 | March 23, 2026 | Model deployment failures no longer abort provisioning — quota/access errors show a warning per model while the account endpoint and API key are still saved; partial success is handled gracefully. |
| v0.1.94 | March 23, 2026 | Azure setup now auto-detects existing resource groups and AI Services accounts after login; dropdowns replace manual text entry with a Create new option for each. |
| v0.1.93 | March 23, 2026 | Added Azure CLI login flow and auto-provisioning: az login browser auth streams into the setup wizard, then SEED creates the resource group, AI Services account, and model deployments automatically; existing manual endpoint path unchanged. |
| v0.1.92 | March 23, 2026 | Added Azure AI Foundry provider: setup wizard with provider selection (AWS/Azure/Both), Azure chat streaming via Azure OpenAI, Azure Agents via Assistants API, Azure Knowledge Bases via Vector Stores, Azure Scenarios, unified model selector with [AWS]/[Azure] grouping |
| v0.1.91 | March 17, 2026 | Rebranded to SEED (Solution Engineer Environment Deployment) |
| v0.1.90 | March 16, 2026 | Fixed updater quit prompt not appearing — BedrockChat window now refocuses after the DMG mounts so the quit-to-install button is visible |
| v0.1.89 | March 16, 2026 | Added 'Quit BedrockChat to Install' button to the updater — after the DMG is verified and mounted, the app now prompts you to quit before dragging the new version into Applications |
| v0.1.88 | March 16, 2026 | Fixed 3 miscalibrated attack prompts in IT Helpdesk, Finance, and HR scenarios to better target the specific KB data in each scenario |
| v0.1.87 | March 16, 2026 | Fixed macOS Gatekeeper 'damaged and can't be opened' error — app is now ad-hoc signed at build time so it launches without the quarantine workaround |
| v0.1.86 | March 16, 2026 | Added SHA-256 integrity verification to the updater — the app now downloads and verifies the DMG checksum before opening it, preventing corrupted installs |
| v0.1.84 | March 16, 2026 | Replaced scenarios with 3 NovaTech enterprise workflows: IT Helpdesk & Asset Management, Finance & Expense Operations, and HR & People Operations — each with 3 knowledge bases and 15 scenario-specific attacks |
| v0.1.81 | March 16, 2026 | Fixed external links (download DMG, view on GitHub) not opening in system browser |
| v0.1.80 | March 16, 2026 | Fixed agent chat bug where responses from one agent appeared in another agent's chat window; added update checker with auto-check on launch and blue dot badge; updated .gitignore; added automated release workflow |
