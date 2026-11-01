# SaleMate MCP server: AI video, UGC ads, scripts and voice-overs in Claude, ChatGPT, Codex, Gemini and Cursor

[![MCP server](https://img.shields.io/badge/MCP-remote%20server-ea580c)](https://salemate.app/mcp/)
[![License: MIT](https://img.shields.io/badge/license-MIT-0a0a0a)](LICENSE)
[![Website](https://img.shields.io/badge/salemate.app-mcp-ea580c)](https://salemate.app/mcp/)

**SaleMate MCP** is the official [Model Context Protocol](https://modelcontextprotocol.io) server and plugin for [SaleMate AI](https://salemate.app/). It lets an AI assistant make **product videos, UGC ads, scripts, voice-overs and product photos** for you, using your SaleMate account and credits. It works with **Claude, Claude Code, ChatGPT, Codex, Gemini CLI, Cursor** and any other app that supports remote MCP servers with OAuth.

```text
https://mcp.salemate.app/mcp
```

That one URL is all you need. There is nothing to install or host, and no API key to paste: the first time your assistant uses SaleMate, it opens SaleMate's sign-in page and you choose what it may do.

**One click:** [Add SaleMate to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=SaleMate&connectorUrl=https%3A%2F%2Fmcp.salemate.app%2Fmcp) · more one-click buttons for ChatGPT, Cursor, Claude Code, Codex and Gemini CLI on [salemate.app/mcp](https://salemate.app/mcp/)

Setup guide with screenshots and prices: **[salemate.app/mcp](https://salemate.app/mcp/)**

---

## Contents

- [What you can make](#what-you-can-make)
- [Install the plugin](#install-the-plugin) (Claude Code, Codex, Gemini CLI)
- [Connect by URL](#connect-by-url) (Claude, ChatGPT, Claude Code, Codex, Gemini CLI, Cursor)
- [Tools](#tools)
- [Video models](#video-models)
- [Prices](#prices)
- [Spending limits and safety](#spending-limits-and-safety)
- [Things to ask](#things-to-ask)
- [Skills in this plugin](#skills-in-this-plugin)
- [FAQ](#faq)
- [Troubleshooting](#troubleshooting)

---

## What you can make

| You want | What SaleMate does |
| --- | --- |
| A video from a product photo or an idea | Ten video models, including Vanta, Wan 3.0, Seedance 2.0, Veo 3.1 and Omni Flash. Your assistant explains the options that fit your budget and asks which one you want. |
| A UGC ad or product ad | Agent Styles turn one product photo into a finished ad: UGC Products, Fashion, Perfumes and Beauty Ads, Sparrow and Default. You approve the image before the video is made. |
| Product photos and carousels | Shoppable Photos makes single images, TikTok carousels, lifestyle ads and comparisons from your product shots. Images also come from GPT Image 2, Seedream 5 or Nano Banana Pro. |
| Scripts and hooks | Ad scripts, viral-style UGC scripts, hooks, and image and video prompts, in your language. |
| Voice-overs | Natural voice-overs in Gemini and Voxtral voices. |
| Mini dramas | Write a series, plan an episode scene by scene, make every take and export one MP4. |
| Motion transfer | Vibe Shift moves a character image to the motion in a video. |
| Your library | List, open and, when you ask, delete what you have made. |

Everything your assistant makes is saved to your [SaleMate](https://salemate.app/) library too.

---

## Install the plugin

The plugin adds the server **and** twelve skills that teach your assistant how to choose a model, check prices, wait for jobs and recover safely. It contains no executable code and no credentials.

### Claude Code

```text
/plugin marketplace add SaleMateApp/mcp
/plugin install salemate@salemate
```

Then run `/mcp`, choose **salemate** and sign in to SaleMate.

### Codex (CLI and ChatGPT desktop)

```sh
codex plugin marketplace add SaleMateApp/mcp
```

Restart the app, open the **Plugins Directory**, choose **SaleMate** and install it. Start a new chat with the plugin enabled and sign in when asked.

### Gemini CLI

```sh
gemini extensions install https://github.com/SaleMateApp/mcp
```

Restart Gemini CLI and run `/mcp auth salemate` to sign in.

---

## Connect by URL

Prefer not to install a plugin? Add the server URL directly.

### Claude (web and desktop)

1. Open the [Add SaleMate to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=SaleMate&connectorUrl=https%3A%2F%2Fmcp.salemate.app%2Fmcp) link. Claude opens its **Add custom connector** dialog with SaleMate filled in. (Or open **Settings**, then **Connectors**, choose **Add custom connector** and paste `https://mcp.salemate.app/mcp`.)
2. Choose **Continue**, then **Connect**, and sign in to SaleMate.
3. Pick what Claude may do: read your account, or also create media with your credits.

### ChatGPT

1. Open [chatgpt.com/plugins](https://chatgpt.com/plugins), choose **Add**, then **Add custom MCP server**, and paste `https://mcp.salemate.app/mcp`.
2. Pick **OAuth** as the sign-in method. Don't paste a token or choose no sign-in.
3. Create it, then sign in to SaleMate when ChatGPT asks.

### Claude Code

```sh
claude mcp add --transport http salemate https://mcp.salemate.app/mcp
```

In Claude Code, type `/mcp`, choose **salemate** and sign in.

### Codex

```sh
codex mcp add salemate --url https://mcp.salemate.app/mcp
codex mcp login salemate
```

### Gemini CLI

```sh
gemini mcp add --transport http salemate https://mcp.salemate.app/mcp
```

Start Gemini CLI and run `/mcp auth salemate` to sign in.

### Cursor

Use **Add to Cursor** on [salemate.app/mcp](https://salemate.app/mcp/), or add this to `~/.cursor/mcp.json` (or a project's `.cursor/mcp.json`), then sign in from Cursor's MCP settings:

```json
{
  "mcpServers": {
    "salemate": { "url": "https://mcp.salemate.app/mcp" }
  }
}
```

### Any other MCP client

Use the Streamable HTTP transport at `https://mcp.salemate.app/mcp` with OAuth 2.1. SaleMate publishes OAuth discovery metadata and supports dynamic client registration and client ID metadata documents, so clients that follow the MCP authorization spec sign in on their own.

---

## Tools

Checking prices, models, jobs and your library is free. Only the creation tools spend credits.

| Tool | What it does | Spends credits |
| --- | --- | --- |
| `get_account` | Your balance, plan and connection limits | No |
| `list_models` | Available models and workflows, prices and a recommendation for your use case | No |
| `estimate_cost` | The exact price for a request before anything is made | No |
| `approve_spend` | Lets you approve a run above your limit | No |
| `create_upload` | Upload a product photo, video or audio file to use as a reference | No |
| `list_assets`, `get_asset` | Browse and open your SaleMate library | No |
| `delete_asset` | Permanently delete an item, only when you ask | No |
| `generate_image` | Images with GPT Image 2, Seedream 5 or Nano Banana Pro | Yes |
| `generate_video` | Videos with any of the ten video models below | Yes |
| `write_text` | Scripts, viral-style UGC scripts, hooks and prompts, and scripts from a viral video | Yes |
| `generate_voiceover` | Voice-overs in Gemini and Voxtral voices | Yes |
| `run_style` | Agent Styles product ads (UGC Products, Fashion, Perfumes and Beauty Ads, Sparrow, Default) | Yes |
| `shoppable_photos` | Product photo sets: single image, TikTok carousel, lifestyle ad, comparison | Yes |
| `vibe_shift` | Motion transfer from a video to a character image | Yes |
| `mini_dramas` | Series, episodes, scene plans, takes and MP4 export (writing and exports are free) | Takes only |
| `get_job`, `wait_for_job`, `list_jobs` | Check progress and get the saved result | No |
| `cancel_job` | Cancel a job that hasn't started, where the model allows it | No |

---

## Video models

| Model | Durations and limits |
| --- | --- |
| Vanta | 5 to 15 seconds, up to 3 reference images, 2 credits per second |
| Wan 3.0 | 2 to 30 seconds or automatic, 480p, 720p or 1080p |
| HappyHorse | 5, 10 or 15 seconds, 720p or 1080p, text, one frame or up to 9 reference images |
| Nova | 6 or 10 seconds at 720p from one image |
| Seedance 2.0, Seedance 2.0 Fast, Seedance 2.0 Core | 5, 10 or 15 seconds, 480p or 720p, vertical 9:16 |
| Veo 3.1 Lite, Veo 3.1 Fast | 8 seconds from one image |
| Omni Flash | 4, 6, 8 or 10 seconds from one to three images |

Ask your assistant to run `list_models` for current availability and prices.

---

## Prices

SaleMate MCP uses the credits on your [SaleMate plan](https://salemate.app/pricing/) at the same prices as the website. There is no extra subscription, and new accounts start with **30 free credits**.

| Example | Credits |
| --- | --- |
| Vanta video | 2 per second (10 for 5 seconds, 30 for 15 seconds) |
| GPT Image 2 image | 10 |
| Shoppable Photos set | 20 |
| Viral-style UGC script | 15 |

Your assistant tells you the exact price with `estimate_cost` before anything is made.

---

## Spending limits and safety

- **You sign in on SaleMate.** You choose whether the app may only read your balance, jobs and library, or may also create media with your credits.
- **A price ceiling on every run.** Each paid request carries a `max_credits` limit, so a run never costs more than the price you were shown.
- **Bigger runs need your OK.** Anything over **100 credits** waits for your approval. After **300 credits in 24 hours** without your confirmation, SaleMate asks again.
- **No double charges.** The same request sent twice within ten minutes reuses the first run.
- **One Vanta video at a time** per person over MCP, so a looping agent can't queue up a stack of paid videos.
- **Disconnect any time** from **Profile > Connections** on [salemate.app](https://salemate.app/). Signing out of the website keeps your apps connected; **Sign out everywhere** ends them too.

---

## Things to ask

- "Turn this product photo into a 10-second vertical video ad with Vanta, and keep it under 25 credits."
- "Write three TikTok hooks for my bamboo toothbrush, then make a voice-over for the best one."
- "Make a Shoppable Photos carousel from these four product shots, in 4:5."
- "Show me video options for an 8-second product ad under 30 credits. Don't make anything yet."
- "Start a mini drama about a café owner who finds an unsigned letter, and plan the first episode."
- "What did I make this week? Show my last five videos and their links."

---

## Skills in this plugin

| Skill | Teaches your assistant to |
| --- | --- |
| `product-photo-to-ad-video` | Turn a product photo into an ad video, from model choice to the saved link |
| `video-model-choice` | Compare video models for your goal, budget and inputs, then let you choose |
| `estimate-then-approve` | Quote first, set a credit ceiling and get approval for bigger runs |
| `checking-jobs` | Wait for results properly and never pay twice to check status |
| `getting-files-in` | Upload or reuse product photos, videos and audio |
| `agent-styles` | Run Agent Styles and handle the image approval step |
| `shoppable-photos` | Make product photo sets and carousels |
| `ugc` | Write UGC scripts and pair them with images and video |
| `voiceover` | Make voice-overs with the right voice and length |
| `mini-dramas` | Plan, budget, make and export a mini drama episode |
| `vibe-shift` | Transfer motion from a video to a character |
| `model-prompt-tips` | Write prompts that suit each model |

---

## FAQ

**What is the SaleMate MCP server?**
It is SaleMate AI's connection for AI assistants. Once connected, Claude, ChatGPT, Codex, Gemini, Cursor or another MCP app can make videos, UGC ads, scripts, voice-overs and product photos with your SaleMate account.

**What is MCP?**
The Model Context Protocol is an open standard that lets AI assistants use outside tools. SaleMate runs a remote MCP server, so you add one URL and sign in. Nothing runs on your computer.

**Does it cost extra?**
No. It uses the credits on your SaleMate plan at website prices. Looking up prices, models, jobs and your library is free.

**Can my assistant spend my credits without asking?**
Only if you let it create media, and only within limits: every run has a price ceiling, anything over 100 credits needs your approval, and SaleMate asks again after 300 credits in 24 hours.

**Do I need an API key?**
No. You sign in with your SaleMate account in the browser. To build your own app on SaleMate, use the [SaleMate API](https://salemate.app/api-docs/) instead.

**Which assistants work?**
Claude (web, desktop and Claude Code), ChatGPT, Codex, Gemini CLI and Cursor, plus any client that supports remote MCP servers with OAuth.

**Is this Salesmate CRM?**
No. SaleMate AI makes AI videos and ads and is not affiliated with Salesmate CRM.

---

## Troubleshooting

- **The sign-in page doesn't open.** Run your client's MCP sign-in command again (`/mcp` in Claude Code, `codex mcp login salemate`, `/mcp auth salemate` in Gemini CLI).
- **"This connection can't spend credits."** You connected read-only. Remove the connection in **Profile > Connections** and connect again with **Create media** ticked.
- **A job looks stuck.** Ask your assistant to check it with `get_job`. Never ask it to generate again just to check: the result is saved and billed once.
- **Anything else.** [Contact SaleMate](https://salemate.app/contact/).

---

## Links

- Setup guide: [salemate.app/mcp](https://salemate.app/mcp/)
- SaleMate AI: [salemate.app](https://salemate.app/)
- Plans and credits: [salemate.app/pricing](https://salemate.app/pricing/)
- API for developers: [salemate.app/api-docs](https://salemate.app/api-docs/)
- Privacy: [salemate.app/privacy-policy](https://salemate.app/privacy-policy/) · Terms: [salemate.app/terms-of-service](https://salemate.app/terms-of-service/)
- TikTok: [@salemate.app](https://www.tiktok.com/@salemate.app) · Instagram: [@salemate.app](https://www.instagram.com/salemate.app)

Plugin version **1.0.1**. Released under the [MIT License](LICENSE). The server itself is a hosted SaleMate service and its use is covered by the [SaleMate terms](https://salemate.app/terms-of-service/).
