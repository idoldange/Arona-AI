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
| **Reverse Image Search** | Identifies image sources via Google Lens with Yandex as fallback. |
| **GitHub Integration** | Browse repositories, read files, search code, and inspect directory trees directly in chat. |
| **Code Execution** | Runs Python scripts and shell commands in isolated Docker containers with file output support. |
| **Artifact Preview** | Output files (`.html`, `.jsx`, `.md`, `.mermaid`) are automatically accompanied by a live preview link. Clicking it opens the file in a browser-based viewer — no download required. |
| **Kivotos Database** | Query *Blue Archive* student stats, skills, gear, banners, events, and raids via SchaleDB. |
| **Song Recognition** | Identifies songs from audio or video URLs using Shazam. |
| **Weather** | Retrieves real-time weather data for any location worldwide. |
| **Chess** | Play a full game of chess with board image rendering. |
| **Voice Chat** | Joins voice channels for live AI conversation with real-time audio support. |
| **Text-to-Speech** | Synthesizes Arona's voice using a custom-trained model. Responses can be delivered as standalone audio messages. |
| **Singing Synth** | Arona sings UTAU (`.ust`), OpenUtau (`.ustx`) projects and plays MIDI (`.mid`) with soundfonts, mixing vocals, instruments and extra audio. Attach images/videos to get an `.mp4`. |
| **Raid Recovery** | One-command cleanup after a server raid: purges spam messages, removes junk channels, restores renamed channels and recreates deleted ones. |
| **Slash Command** | `/arona` lets you chat with Arona (with up to 10 attachments) anywhere via user install, no server invite needed. |
| **Account Migration** | Link or unlink Discord accounts so they share the same chat history and saved information. |
| **Scheduling** | Schedule messages or AI-triggered tasks for a future time, with support for recurring intervals (daily, weekly, monthly). |
| **Gacha Tracker** | Tracks *Blue Archive* pull history, pity counter, and spark progress per user. |
| **Todo** | Per-channel task list with full CRUD support, displayed as formatted Discord embeds. |
| **Channel Memory** | Persistent per-channel notes and context automatically injected into Arona's prompt — useful for pinned instructions or shared channel lore. |
| **Mood System** | Arona's tone shifts naturally over time based on how she's treated, how long she's been idle, and even hardware temperature. Leave her alone long enough and she'll be in a better mood when you come back. |
| **Bond System** | Arona remembers how much each user has talked with her and adjusts how she treats them accordingly — from a professional stranger to something noticeably warmer. |

---

## Commands

Prefix: `!arona`

### General

| Command | Description |
|---|---|
| `!arona help` | Show available commands |
| `!arona affection` | Show your bond rank with Arona and her current mood (aliases: `!arona bond`, `!arona mood`) |

### Utilities

| Command | Description |
|---|---|
| `!arona base64 encode <text>` | Encode text to Base64 |
| `!arona base64 decode <base64>` | Decode a Base64 string |

### Channel Management

By default, Arona only responds when mentioned. Use these commands to set channels where she responds to **every message** automatically, or channels she should ignore entirely. These commands require "Manage Channels" permission.

| Command | Description |
|---|---|
| `!arona channel add` | Add the current channel to the auto-respond list |
| `!arona channel remove` | Remove the current channel from the auto-respond list |
| `!arona ignoredchannel add [id]` | Make Arona ignore a channel entirely (no responses, no processing). Defaults to the current channel if no ID is given |
| `!arona ignoredchannel remove [id]` | Stop ignoring a channel. Defaults to the current channel if no ID is given |

### Context Management

This command manage Arona's memory of previous messages in the channel. By default, she reads the last 15 messages for context. Use this to clear that history. This command requires "Manage Messages" permission, or the current channel is a DM.

| Command | Description |
|---|---|
| `!arona clear` | Prevent Arona from reading any previous messages in the channel. |

### Chess

Play against a local engine or another member. Moves accept UCI or SAN (e.g. `e2e4`, `Nf3`). Each channel can host one game.

| Command | Description |
|---|---|
| `!arona chess start [elo] [white\|black]` | Start a game against the engine (default: White) |
| `!arona chess restart [elo] [white\|black]` | Reset the board, keeping or replacing the elo/color |
| `!arona chess challenge @user [white\|black]` | Challenge another member to a PvP game |
| `!arona chess move <move>` | Play a move |
| `!arona chess board` | Show an interactive click-to-move board |
| `!arona chess resign` | Resign the current game |
| `!arona chess stop` | End the current game (engine or PvP) |

### Text-to-Speech

| Command | Description |
|---|---|
| `!arona tts <text>` | Arona speaks the text as an audio file (max 1500 characters). Japanese only. Raise or lower pitch with `↑` / `↓` (e.g. `そ↑う`), and switch voice emotion with tags such as `[happy]` or `[shy]`. |

### Singing Synth

Attach one or more `.ust`, `.ustx`, or `.mid`/`.midi` files to `!arona synth`. Multiple files are synthesized as separate tracks and mixed together. Can take several minutes.

| Command / Option | Description |
|---|---|
| `!arona synth` | Sing the attached UTAU/OpenUtau project and/or play the attached MIDI |
| `!arona synth list <word>` | Browse available instruments and soundfonts (e.g. `list violin`) |
| `transpose=<semitones>` | Shift pitch (default: automatic octave) |
| `lang=ja\|en` | Lyrics language (default: `ja`) |
| `temperature`, `top_k`, `voice_center`, `auto_octave` | Fine-tune the vocal synthesis |
| `sf=<soundfont>[:<instrument>]` | Choose the soundfont/instrument for instrument tracks |
| `inst_vol=<percent>`, `inst_db=<dB>` | Instrument loudness relative to the vocal |
| `inst=0` / `vocals=0` | Skip instrument or vocal tracks |
| `vid_vol=<percent>`, `fade=<sec>`, `img=<sec>` | Controls for images/videos attached to produce an `.mp4` |

### Server Security

| Command | Description |
|---|---|
| `!arona raided` | Open the raid recovery panel: choose the time window and optional raider bot ID, then purge spam, remove junk channels and restore channels. Requires the **Administrator** permission; the bot needs `Manage Messages`, `Manage Channels` and `View Audit Log`. |

### Slash Command

| Command | Description |
|---|---|
| `/arona <prompt> [attachment1..10]` | Chat with Arona from anywhere (user install) |

### API Key Management

Arona includes a free daily message limit. To skip it, bring your own Gemini API key — free to get, no cost to you.

| Command | Description |
|---|---|
| `!arona addkey` | Add your own Gemini API key(s) via a form. Multiple keys can be added, and new keys stack with existing ones. |
| `!arona listkeys` | View your saved keys (only visible to you). |
| `!arona removekey <index>` | Remove a key by its index from `!arona listkeys`. |
| `!arona quota` | Check your remaining free daily messages. |

### Data Management
This command **deletes ALL** data related to you in Arona's database (e.g., saved info, message history, API keys, etc.). This action **cannot** be undone.

| Command | Description |
|---|---|
| `!arona forgetme` | Delete all data related to your account. |
| `!arona forgetme confirm` | Confirm data deletion. This action cannot be interrupted or reversed. |

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

**Bring Your Own Key**
If you use `!arona addkey`, your key is stored encrypted and used only for your own requests. Requests routed through Arona's servers are still subject to Google's standard Gemini API terms. You are responsible for how your key is used.

**Official Policies**

[Google Privacy Policy](https://policies.google.com/privacy) · [Gemini Terms of Service](https://support.google.com/gemini/answer/13594961)

---

## References

| Project | Description | Link |
|---|---|---|
| **Google Gemini API** | Core AI engine powering Arona's language understanding, multimodal input, and function calling | [ai.google.dev](https://ai.google.dev/gemini-api/docs) |
| **GPT-SoVITS** | TTS framework used for Arona's voice synthesis | [GitHub](https://github.com/RVC-Boss/GPT-SoVITS) |
| **Applio** | RVC-based voice conversion platform used for voice chat | [GitHub](https://github.com/IAHispano/Applio) |

---

## Project Info

| | |
|---|---|
| **Version** | Beta(idk) |
| **License** | MIT License |
|**Source Code**| [Github Repo](https://github.com/idoldange/arona) |
| **Developer** | [Dante](https://github.com/idoldange) — Solo Project |
| **Bug Reports** | [GitHub Issues](https://github.com/idoldange/Arona-AI/issues) |

---

*© 2026 Arona Bot. All rights reserved.*
