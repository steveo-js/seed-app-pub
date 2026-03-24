# Bedrock Chat — Releases

A native macOS application that connects to AI models on Amazon Bedrock. Your AWS credentials stay on your machine and are never sent anywhere except directly to AWS.

**Latest Version:** v0.1.107

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
