# Compositor

**AI session memory, composed and carried forward.**

A single-file HTML tool that solves a specific problem: AI conversation memory does not carry between sessions or across platforms. A user working with Claude, ChatGPT, Grok, and Gemini in browser tabs — plus Claude Code and Codex in CLI — re-explains the same constraints, re-derives the same decisions, and loses useful insights every time they start a new session.

Compositor is the connective tissue. Ingest a session summary, extract structured records, and assemble a briefing pack to carry context into the next session — anywhere, with any AI.

**[Open Compositor →](https://pressandprocess.github.io/compositor/)**

---

## How it works

**Ingest.** Paste or upload an AI session summary. Compositor parses it and extracts structured records — decisions, threads, constraints, insights, brainstorming, knowledge, actions, and questions — grouped by category with a confidence score. Review the extraction, add flags and tags, then commit the session to your local ledger.

**Repository.** Filter across all ingested sessions by category, flag, source, tag, or time window. Select the sessions that are relevant to your next task and assemble a briefing pack — a Markdown context block in three sizes (tiny, standard, deep) — ready to paste into any AI session.

**Ledger.** The central data view. Every session you've committed, sortable and searchable. Export individual sessions or in bulk. The ledger lives entirely in your browser's localStorage — no server, no sync, no account.

---

## Architecture

**Edge-computed.** Everything runs in the browser. No external API calls, no cloud backend, no accounts required. Your data stays on your machine.

**Single file.** The deliverable is one HTML file. No build step, no bundler, no framework, no NPM. Vanilla JavaScript and inline styles. Download it, open it, use it.

**Vendor neutral.** Compositor does not care which AI produced the input. It treats all sources as text with patterns. Claude, ChatGPT, Grok, Gemini, Claude Code, Codex — all work.

---

## Usage

**Option 1 — Use it directly:**
Open [pressandprocess.github.io/compositor](https://pressandprocess.github.io/compositor/) in any modern browser. No installation required.

**Option 2 — Self-host:**
Download `index.html` from this repo and host it anywhere over HTTPS. The tool requires HTTPS — local `file://` URLs trigger browser security restrictions on the FileReader and clipboard APIs.

**Option 3 — Run locally with a simple server:**
```bash
npx serve .
# or
python -m http.server 8080
```
Then open `http://localhost:8080` in your browser.

---

## Parser

Compositor handles three input modes:

- **Structured Markdown** — summaries with `## Decisions`-style section headers. Highest confidence extraction.
- **AI summaries in code fences** — summaries wrapped in triple backticks with optional YAML frontmatter. High confidence.
- **Unstructured prose** — plain text classified by keyword patterns. Lower confidence, still useful.

The confidence ring on the review card tells you how much structure the parser found before you commit.

---

## Data

All data is stored in `localStorage` under the key `compositor_v2`. Nothing leaves your browser.

The ledger has a soft ceiling around 300–400 sessions before localStorage becomes uncomfortable. A Google Sheets sync layer is planned for v2 — the ledger schema is already shaped for it.

To back up or move your data: Settings → Export Records (JSON). To restore: Settings → Import Records.

---

## Roadmap

- **v2.1** — Google Apps Script ledger sync. Append-only writes to a Google Sheet, read-back for cross-device access, removes the localStorage ceiling.
- **v2.2** — User-defined category keyword aliases. Let users add keyword patterns when defining a custom category so the parser's fallback classification recognizes it.
- **v2.3** — Multi-file ingest queue.
- **v3.0** — Once the ledger lives in Sheets, any AI with MCP can query it directly.

These are directions, not commitments.

---

## License

MIT License — see [LICENSE](./LICENSE).

Copyright (c) 2026 Chad Corwin / Press & Process Guild.

---

## Press & Process Guild

Compositor is the flagship tool of [Press & Process Guild](https://pressandprocess.ai) — a practice building practical, open-source AI tools. Single file. Edge computed. No backend required.

[pressandprocess.ai](https://pressandprocess.ai) · [GitHub](https://github.com/pressandprocess)
