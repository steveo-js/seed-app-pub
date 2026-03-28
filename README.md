# SEED — Releases

A native macOS application that connects to AI models on Amazon Bedrock. Your AWS credentials stay on your machine and are never sent anywhere except directly to AWS.

**Latest Version:** v0.1.168

[Download SEED-0.1.168-arm64.dmg](https://github.com/steveo-js/bedrock-app-pub/releases/download/v0.1.168/SEED-0.1.168-arm64.dmg)

## How to Install

1. Download the DMG above
2. Open it and drag **SEED** into your **Applications** folder
3. Eject the disk image
4. Open **SEED** from Applications

> **If macOS shows "damaged and can't be opened":** Open Terminal and run `xattr -cr /Applications/SEED.app`, then launch the app normally.

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| v0.1.168 | March 28, 2026 | Claude direct API chat tab with proxy profiles, proxy auth detection (bearer/basic), and AWS/Azure toggle hidden on Chat tab |
| v0.1.167 | March 28, 2026 | Added Claude Chat tab with direct Anthropic API integration, named proxy profiles for routing, and Claude section in Settings |
