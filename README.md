<h1 align="center">BlueDrip</h1>

<p align="center">
  <strong>AI-powered iMessage drip sequences from your real phone number.</strong>
</p>

<p align="center">
  Schedule personalized iMessage and SMS sequences, detect replies in real time, and get notified the moment someone responds — all from your Mac. No cloud, no CRM, no subscriptions.
</p>

<p align="center">
  <a href="https://github.com/amengol/bluedrip-releases/releases/latest">
    <img src="https://img.shields.io/badge/Download%20for%20macOS-1d9bf0?style=for-the-badge&logo=apple&logoColor=white" alt="Download for macOS">
  </a>
  &nbsp;
  <a href="https://github.com/amengol/bluedrip-releases/releases">
    <img src="https://img.shields.io/github/v/release/amengol/bluedrip-releases?style=for-the-badge&label=latest&color=1d9bf0&cacheSeconds=3600" alt="Latest release">
  </a>
</p>

---

## Why BlueDrip

- **Your real number.** Messages go out through your own iMessage/SMS account, from your own phone, the way you'd send them yourself — not through a spoofed gateway or a shared shortcode.
- **Local-first.** Leads, templates, and conversation history all live in a local SQLite database on your Mac. Your data never leaves your machine.
- **Smart replies.** Optional AI intent classification tags incoming responses as *interested*, *opt-out*, *question*, and more — then routes them to DNC, a webhook, or a human inbox for you to review.
- **No subscriptions.** Buy a license key and run BlueDrip on your own hardware. There are no per-message fees, no monthly caps, and no servers to babysit.

## Features

- Multi-step drip sequences defined in plain Markdown templates with YAML frontmatter
- Variable substitution (`{{first_name}}`, `{{company}}`, ...) with per-contact data
- Media attachments: images, video clips, voice messages
- Unified inbox that watches the Messages database in real time — replies appear within seconds
- Automatic sequence pause-on-reply
- Do-Not-Contact list enforcement, rate limiting, delivery idempotency
- AI intent classification via Anthropic, OpenAI, or any OpenAI-compatible provider (your API key, stored locally)
- Webhook dispatch for CRM integration, with retry logic and delivery logging
- Full dashboard UI: contacts, sequences, templates, analytics, inbox, settings
- macOS menubar app with background service — runs quietly without getting in your way

## How it works

BlueDrip installs as a standalone macOS app with a menubar icon. A background service (the "bridge") sends scheduled iMessages via Apple's Messages app on your Mac and watches the Messages database for incoming replies using `fswatch`. When someone responds, BlueDrip pauses the sequence automatically and sends you a native macOS notification — no polling, no webhooks, no middlemen handling your conversations.

The dashboard window gives you a full UI for managing contacts, building sequences, reviewing the inbox, and checking analytics. You can close the dashboard anytime — the bridge keeps running silently in the background.

## Requirements

- **macOS 11** (Big Sur) or newer
- **A phone number registered with iMessage** on your Mac
- **A BlueDrip license key** — free tier available for personal use

## Installation

1. Download the latest **BlueDrip.dmg** from the [Releases](https://github.com/amengol/bluedrip-releases/releases/latest) page
2. Open the DMG and drag **BlueDrip** to your Applications folder
3. Launch BlueDrip — the setup wizard walks you through license activation, macOS permissions, and your first sequence in under two minutes

The setup wizard handles everything automatically: it installs the background service, asks for the Messages/Automation permissions macOS needs, and initializes your local database at `~/Library/Application Support/BlueDrip/`.

## Privacy

Everything lives on your Mac. Leads, templates, sequences, message logs, and conversation history all stay in a local SQLite database at `~/Library/Application Support/BlueDrip/`. The only network calls BlueDrip makes are:

- **License validation** — a lightweight check-in with the BlueDrip license server to verify your key is active
- **Update notifications** — a version check that tells you when a new release is available
- **AI intent classification** *(optional)* — only if you enable it and configure an API key; BlueDrip sends the reply text to the provider you choose

Messages, contacts, and sequences are never transmitted anywhere. You can inspect the database yourself — it's just SQLite.

## Getting a license

BlueDrip is commercial software with a free tier. To request a key or ask about pricing, get in touch: **contact@bluedrip.io**

## Release history

Every version, its changelog, and its download are on the [Releases](https://github.com/amengol/bluedrip-releases/releases) page. Each release page includes full release notes.

---

<p align="center">
  <sub>© Jorge Amengol. BlueDrip is proprietary software distributed under a commercial license.</sub>
</p>
