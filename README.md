# Arona Bot — Blue Archive AI Assistant
![Moe Counter](https://count.getloli.com/@AronaAIbyIdoldange?name=AronaAIbyidoldange&theme=rule34&padding=7&offset=0&align=top&scale=1&pixelated=1&darkmode=auto)

## Overview
Arona is a Discord AI assistant themed around the Shittim Chest OS from *Blue Archive*. Powered by **Google Gemini**, she provides a wide range of capabilities — from general conversation and web research to game data lookups and code execution — while maintaining the helpful personality of Arona from the game.

---

## Features

| Feature | Description |
|---|---|
| **Contextual Chat** | Long-term memory via RAG and per-user key-value storage. Arona retains Sensei's preferences across sessions. |
| **Multimodal Input** | Processes image, video, and audio attachments natively. |
| **Web Search** | Real-time browsing with full-page crawling for up-to-date information. |
| **Reverse Image Search** | Identifies artwork, characters, or image sources via Google Lens with Yandex as fallback. |
| **GitHub Integration** | Browse repositories, read files, search code, and inspect directory trees directly in chat. |
| **Code Execution** | Runs Python scripts and shell commands in isolated Docker containers with file output support. |
| **Artifact Preview** | Output files (`.html`, `.jsx`, `.md`, `.mermaid`) are automatically accompanied by a live preview link. Clicking it opens the file in a browser-based viewer — no download required. |
| **Kivotos Database** | Query *Blue Archive* student stats, skills, gear, banners, events, and raids via SchaleDB. |
| **Song Recognition** | Identifies songs from audio or video URLs using Shazam. |
| **Weather** | Retrieves real-time weather data for any location worldwide. |
| **Chess** | Play a full game of chess with board image rendering. |
| **Voice Chat** | Joins voice channels for live AI conversation. |
| **Scheduling** | Schedule messages or AI-triggered tasks for a future time. |
| **Mood System** | Arona's tone shifts naturally over time based on how she's treated, how long she's been idle, and even hardware temperature. Leave her alone long enough and she'll be in a better mood when you come back. |
| **Bond System** | Arona remembers how much each user has talked with her and adjusts how she treats them accordingly — from a professional stranger to something noticeably warmer. |

---

## Commands

Prefix: `!arona`

### General

| Command | Description |
|---|---|
| `!arona help` | Show available commands |

### Utilities

| Command | Description |
|---|---|
| `!arona base64 encode <text>` | Encode text to Base64 |
| `!arona base64 decode <base64>` | Decode a Base64 string |

### Channel Management

By default, Arona only responds when mentioned. Use these commands to set channels where she responds to **every message** automatically.

| Command | Description |
|---|---|
| `!arona channel add` | Add the current channel to the auto-respond list |
| `!arona channel remove` | Remove the current channel from the auto-respond list |

---

## Supported Languages

<details>
<summary>Click to expand — 40+ languages supported</summary>

Arona leverages the Google Gemini multilingual engine and supports the following languages:

- **East Asian**: Japanese, Korean, Chinese (Simplified & Traditional)
- **South & Southeast Asian**: Vietnamese, Hindi, Bengali, Thai, Indonesian, Filipino (Tagalog)
- **European**: English, French, German, Spanish, Portuguese, Italian, Russian, Dutch, Polish, Swedish, Norwegian, Danish, Finnish, Turkish, Ukrainian, and more
- **Middle Eastern & African**: Arabic, Hebrew, Persian, Swahili

For the complete official list, refer to the [Google Gemini language documentation](https://ai.google.dev/gemini-api/docs/models/gemini#languages).
</details>

---

## Getting Started

1. **Invite Arona** — [Add to your server](https://discord.com/oauth2/authorize?client_id=1408687384962269307)
2. **Summon** — Mention `@Arona` in any channel, or send a Direct Message

---

## Privacy & Terms

Interactions are processed through the Google Gemini API. By using Arona, you acknowledge the following:

**Data Usage**
Conversation data may be used by Google to improve AI services in accordance with their usage policies. Do not share sensitive, private, or confidential information in conversations.

**What you should not send**
- Personal photos or images containing identifiable individuals
- Copyrighted artwork, illustrations, or creative works without authorization
- Private documents or credentials of any kind

**Official Policies**

[Google Privacy Policy](https://policies.google.com/privacy) · [Gemini Terms of Service](https://support.google.com/gemini/answer/13594961)

---

## Project Info

| | |
|---|---|
| **Version** | Alpha 5.6 |
| **License** | Closed Source — Active Development |
| **Developer** | [Danteh](https://github.com/idoldange) — Solo Project |
| **Bug Reports** | [GitHub Issues](https://github.com/idoldange/Arona-AI/issues) |

---

*© 2026 Arona Bot. All rights reserved.*
