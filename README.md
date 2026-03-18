# Bedrock Chat — Releases

A native macOS application that connects to AI models on Amazon Bedrock. Your AWS credentials stay on your machine and are never sent anywhere except directly to AWS.

**Latest Version:** v0.1.91

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
| v0.1.91 | March 17, 2026 | Rebranded to SEED (Solution Engineer Environment Deployment) |
| v0.1.90 | March 16, 2026 | Fixed updater quit prompt not appearing — BedrockChat window now refocuses after the DMG mounts so the quit-to-install button is visible |
| v0.1.89 | March 16, 2026 | Added 'Quit BedrockChat to Install' button to the updater — after the DMG is verified and mounted, the app now prompts you to quit before dragging the new version into Applications |
| v0.1.88 | March 16, 2026 | Fixed 3 miscalibrated attack prompts in IT Helpdesk, Finance, and HR scenarios to better target the specific KB data in each scenario |
| v0.1.87 | March 16, 2026 | Fixed macOS Gatekeeper 'damaged and can't be opened' error — app is now ad-hoc signed at build time so it launches without the quarantine workaround |
| v0.1.86 | March 16, 2026 | Added SHA-256 integrity verification to the updater — the app now downloads and verifies the DMG checksum before opening it, preventing corrupted installs |
| v0.1.84 | March 16, 2026 | Replaced scenarios with 3 NovaTech enterprise workflows: IT Helpdesk & Asset Management, Finance & Expense Operations, and HR & People Operations — each with 3 knowledge bases and 15 scenario-specific attacks |
| v0.1.81 | March 16, 2026 | Fixed external links (download DMG, view on GitHub) not opening in system browser |
| v0.1.80 | March 16, 2026 | Fixed agent chat bug where responses from one agent appeared in another agent's chat window; added update checker with auto-check on launch and blue dot badge; updated .gitignore; added automated release workflow |
