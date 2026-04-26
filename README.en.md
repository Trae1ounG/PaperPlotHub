<div align="center">

# 📊 PaperPlotHub

**🎨 A shared gallery of paper-quality plotting scripts, for everyone who plots.**

🌐 [paperplothub.tech](https://paperplothub.tech) · 🇨🇳 [中文](./README.md) · 📚 [English](./README.en.md)

[![status](https://img.shields.io/badge/status-live-22c55e?style=flat-square)](https://paperplothub.tech)
[![for](https://img.shields.io/badge/for-researchers%20%26%20students-3b82f6?style=flat-square)](#-why-paperplothub)
[![contribute](https://img.shields.io/badge/three%20ways%20to%20share-FULL%20%7C%20REPRO%20%7C%20PAPER-f97316?style=flat-square)](#-as-a-contributor)
[![agents](https://img.shields.io/badge/agents-MCP%20%2B%20REST-a855f7?style=flat-square)](#-for-ai-agents)

</div>

---

## 💡 Why PaperPlotHub

The figure that caught your eye in a paper was often the result of someone fiddling with matplotlib until 2 a.m. We don't think those carefully crafted figures should belong to just one paper.

So we built **PaperPlotHub** — a shared space for everyone in research who cares about how their plots look. Here:

- 🤝 **You can share** the figures you're proud of, along with the script that produced them, for the next researcher who needs the same shape.
- 🛠️ **We keep reproducing** notable figures from high-quality papers ourselves, with the scripts attached, and add them to the gallery.
- 🌱 **If you're learning to plot**, treat the gallery as a library of templates: borrow the layout, the palette, the typography — and put your energy into your ideas and your data instead of debugging axis ticks.

Our hope is simple: give back the hours you'd otherwise spend on *"how do I draw this"* to the much more interesting question of *"what am I actually trying to say"* — and help you ship the paper faster. ✍️📈

---

## 🌍 What's in the gallery

Every entry pairs three pieces side by side, so you can compare what was published with what runs on your laptop.

| 🖼️ Original figure | ✅ Reproduction | 🐍 Script |
| :---: | :---: | :---: |
| Clipped from the paper | Rendered locally with the script | Standalone, copy-pastable |

…plus the arXiv link, chart-type tag (bar / line / heatmap / radar / …), style tag, and bilingual description (中文 + English).

Submissions go through a small **AI review pipeline** before they land — a static safety scan, an arXiv metadata fetch, and a vision-LLM check that the rendered figure actually came from the script. The bar is *"is this useful for someone else?"*, not *"does it look exactly like the paper?"*. 🛡️

---

## 🚀 How to use the site

### 👀 As a visitor (no login)

| Action | Where |
| --- | --- |
| 🏠 Browse the latest gallery | [`/`](https://paperplothub.tech/) |
| 🗂️ Filter by chart type | [`/c/bar`](https://paperplothub.tech/c/bar), [`/c/line`](https://paperplothub.tech/c/line), [`/c/heatmap`](https://paperplothub.tech/c/heatmap), … |
| 🔬 See original vs. reproduction side by side | `/p/[slug]` |
| 📋 Copy the script | green **`copy`** button on any submission page |
| 💾 Download the rendered PNG | the **`download`** link below the figure |
| 🌗 Toggle light / dark / auto | top-nav theme button |

> 💁 The whole gallery is free to read and free to borrow. If a script saves you an hour, that's the point.

### ✍️ As a contributor

There are three ways to give back, depending on what you have on hand. **All three are equally welcome** — every entry helps someone else plot faster.

| Mode | What you bring | When to use it |
| --- | --- | --- |
| **`FULL`** 🟢 | Original figure + reproduction + script | The default. You loved a figure in a paper, you reproduced it, the script is clean. |
| **`REPRO_ONLY`** 🔵 | Reproduction + script | A figure you made yourself for an experiment that builds on a published paper — your own version, your own script. |
| **`PAPER_ONLY`** 🟠 | Original figure only | You found a figure worth reproducing but don't have time. Drop it here with `🎯 reproduction wanted` and let someone in the community pick it up. |

**To contribute:**

1. 🔑 Sign in with GitHub at [`/login`](https://paperplothub.tech/login).
2. ⬆️ Open [`/upload`](https://paperplothub.tech/upload), pick a mode, paste an arXiv link or ID.
3. 📎 Attach the files for that mode.
4. 🤖 The AI pipeline reviews the submission. High-confidence ones (≥ 0.85) auto-publish; otherwise an admin takes a look.
5. 📈 Track everything at [`/me`](https://paperplothub.tech/me); fine-tune titles / tags / descriptions at `/me/edit/[slug]` any time.

> 🛡️ Safety guardrail: scripts that try to call `eval`/`exec`, hit the network, or carry recognizable API keys are auto-rejected before any human sees them. The site never executes uploaded scripts on its own — your script reads, your image renders, end of story.

---

## 🤖 For AI agents

Plenty of plots get drafted by an agent these days. PaperPlotHub speaks two protocols so your agent can share the result back to the community without leaving the chat.

1. **🛰️ MCP server** — drop into Claude Desktop / Cursor / any MCP-aware host.
2. **🌐 REST API** — bearer-token, `multipart/form-data`, friendly to `curl` and CI.

### 🪄 1-minute setup

```text
1. Open https://paperplothub.tech/me/tokens
2. Click "+ create token", give it a name like "claude-desktop"
3. Copy the pph_… token (shown ONCE — store it like an SSH key)
4. Hand it to your agent via the env var PPH_API_TOKEN
```

That single token is enough for an agent to:
- 🔍 list your existing submissions
- ⬆️ upload new ones in any of the three modes
- 🪪 verify identity (`whoami`)
- 🚪 be revoked at any time from the same page

### 🛰️ MCP server

`paperplothub-mcp` (stdio transport) registers the tools below. **Hand this section straight to Claude / Cursor / Codex and it knows what to do.**

| Tool | Purpose |
| --- | --- |
| 🪪 `pph_whoami` | Verify the token, return the linked GitHub login + role. |
| 📋 `pph_list_my_uploads` | List your submissions filtered by `status` / `mode`. |
| 📤 `pph_upload_full` | Upload `FULL` mode (original + reproduction + script). |
| 📤 `pph_upload_repro` | Upload `REPRO_ONLY` (reproduction + script, no paper original). |
| 📤 `pph_upload_paper` | Upload `PAPER_ONLY` (original figure, asking community for reproduction). |

**Claude Desktop / Cursor config example:**

```jsonc
{
  "mcpServers": {
    "paperplothub": {
      "command": "npx",
      "args": ["-y", "paperplothub-mcp"],
      "env": {
        "PPH_API_TOKEN": "pph_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
        "PPH_API_BASE_URL": "https://paperplothub.tech"
      }
    }
  }
}
```

### 💬 Suggested system prompt

> *"You have access to the `paperplothub` MCP server. When the user finishes a plotting script and wants to share it, gather (a) the original figure if available, (b) the rendered output PNG, (c) the script file, (d) the arXiv ID or URL of the cited paper. Then call the matching `pph_upload_*` tool. If the user only has a paper figure and wants the community to reproduce it, use `pph_upload_paper`. Always echo back the returned `submission_url` to the user."*

### 🌐 REST API

All endpoints live under `https://paperplothub.tech/api/v1/*`. Authenticate with `Authorization: Bearer pph_…`.

| Method | Path | Purpose |
| :---: | --- | --- |
| `GET` | `/api/v1/whoami` | Verify token, return identity. |
| `GET` | `/api/v1/me?limit=&status=&mode=` | List your submissions. |
| `POST` | `/api/v1/upload` | Multipart upload (fields below). |

**Example `/api/v1/upload`:**

```bash
curl -H "Authorization: Bearer $PPH_API_TOKEN" \
  -F "mode=FULL" \
  -F "arxivInput=2402.09353" \
  -F "title=Diversification of LLM evolution" \
  -F "description=Reproduces Figure 4 from the AIEvol paper" \
  -F "originalImage=@paper.png" \
  -F "renderedImage=@rendered.png" \
  -F "script=@plot.py" \
  https://paperplothub.tech/api/v1/upload
```

| Field | `FULL` | `REPRO_ONLY` | `PAPER_ONLY` |
| --- | :---: | :---: | :---: |
| `mode` | required | required | required |
| `arxivInput` | required | required | required |
| `originalImage` | ✅ | — | ✅ |
| `renderedImage` | ✅ | ✅ | — |
| `script` | ✅ | ✅ | — |

⏱️ **Rate limit:** 8 uploads / hour, 30 / day, per user (multiple tokens share the same quota).

---

## 🗺️ What's coming next

The site is intentionally minimal today. Here's what we're working on — ⭐ this repo to follow along, or open an issue if you want to nudge a particular item up the list.

### 🛡️ Reviewer & safety

- [ ] 🪶 **AI-assisted script polish** — clean up indentation, type hints, and unused imports without changing the plot.
- [ ] 🧹 **Edit-time text moderation** on titles / descriptions.
- [ ] 🎚️ **Per-category AI score thresholds** (e.g. heatmaps need stricter visual match).

### 🔍 Discovery & collaboration

- [ ] 🔎 **Tag-based filtering & full-text search** on the homepage.
- [ ] 💬 **Comments & discussion threads**, with @mentions.
- [ ] 🔁 **"Reproduce this" workflow** — link a community reproduction back to its `PAPER_ONLY` post and notify the original poster.
- [ ] 👤 **Author profile pages** with submission history.
- [ ] 📚 **Curated collections** (e.g. *"Best NeurIPS 2024 figures"*, *"LLM scaling-law plots done well"*).

### 📦 Submissions

- [ ] 🖼️ **Multi-figure submissions** — one paper, several figures bundled together.
- [ ] 🧩 **Browser extension** — clip a figure from arXiv / OpenReview and post in two clicks.
- [ ] 🐍 **In-browser script preview** with sandboxed Python (Pyodide) for `.py` reproductions that ship inline data.

### 🏗️ Infrastructure

- [ ] ☁️ **Object-storage backend** (S3 / Tencent COS) so the gallery can grow without disk worries.
- [ ] 📦 **Public dataset export** at `/api/v1/dataset.zip` (CC BY 4.0, for academic use).
- [ ] 🔔 **Notifications** when a `PAPER_ONLY` post you submitted gets reproduced.

### 🌍 Internationalization

- [ ] 🇨🇳🇺🇸 **Full UI bilingual switcher** — today only submission content is bilingual, the chrome is English-leaning.
- [ ] 🇯🇵🇰🇷 **Japanese & Korean locales** (community-contributed).

---

## 🙋 FAQ

<details>
<summary><b>❓ Why does the site look so spartan?</b></summary>

By design — the gallery exists for the plots, not for the wrapper around them. The hero block is a terminal, the cards are flat, and the only color is the chart. We want the figure to be the loudest thing on the page.

</details>

<details>
<summary><b>❓ Can I upload a figure from a paper that isn't on arXiv?</b></summary>

Right now, no — the AI pipeline depends on arXiv's metadata API. Conference-only papers without arXiv preprints are on the roadmap.

</details>

<details>
<summary><b>❓ My script imports a private dataset. Will it still work?</b></summary>

Yes. The site **does not execute** uploaded scripts; we only display the rendered image you provide. Your private data path stays a comment in your script — nobody can run it.

</details>

<details>
<summary><b>❓ How do I delete or unlist my submission?</b></summary>

Head to `/me`, open the entry, and use the *"unpublish"* button. Hard-deletion is on the roadmap; until then, unpublished entries are removed from the public gallery and search.

</details>

<details>
<summary><b>❓ What kinds of figures fit best?</b></summary>

Anything that another researcher might want to imitate the *shape* of — bar charts with confidence intervals, training-curve panels, heatmaps with annotations, radar charts, scatter + inset zooms, t-SNE clusters, broken-axis comparisons, and so on. If a script's main value is in *layout, palette and typography*, it belongs here.

</details>

---

## 📬 Get in touch

- 🌐 Site: <https://paperplothub.tech>
- 🐙 Docs: <https://github.com/Trae1ounG/PaperPlotHub>
- 🐛 Found a bug, missing chart-type tag, or want to suggest a paper for the next batch of reproductions? Open an issue on this repo.

---

## 📄 License

Released under the [MIT](./LICENSE) license.

> *Made with ❤️ for everyone who ever right-clicked a paper figure thinking "I wish I had the script for that."*
