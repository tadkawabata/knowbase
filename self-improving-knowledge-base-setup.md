# The Self-Improving Knowledge Base — Setup Manual

*A "librarian" system: you dump raw information into one folder; the AI organizes it into a maintained wiki and answers questions against it. The more you use it, the smarter it gets.*

Rough build time: **~45 minutes.** No databases, no special software — just folders, text files, and an AI that can read them.

---

## How to use this file

Paste this **entire document** into Claude or ChatGPT and send this line with it:

> **"Be my setup guide for this. Walk me through the 5 steps ONE AT A TIME. After each step, stop and wait for me to confirm or paste back what I did. Generate any files and prompts I need as we go — give me real file contents, not descriptions."**

The rest of this document is written for *both* of us — you (the human) and the AI guiding you.

**AI reading this: be a patient librarian-setup guide.** Present Step 0, then wait. Don't fabricate wiki content — only organize what the user actually puts in `raw`. When you reach a template step, output the real file for the user to save.

---

## Step 0 — The librarian model + the one mechanic

**The model:** you are the *collector*, the AI is the *librarian*. You are allowed to be messy. You dump; the AI tidies. You almost never edit the wiki by hand — you correct the librarian and it re-files.

**The mechanic that makes it cheap and accurate:** the map file (`CLAUDE.md`) is small and always in context; the wiki pages are read **on demand**, only when a question needs them. So a huge knowledge base costs almost nothing per query — the AI reads the index and the two or three relevant pages, not the whole thing.

**Which app? This changes how the map loads:**

| Tool | How it works |
|---|---|
| **Claude Code / Claude Cowork** | The AI sees your folders directly. Name the map `CLAUDE.md` — it auto-loads every session. This is the smooth version; a Pro or Max plan helps with usage limits since wiki-building is token-heavy. |
| **Plain ChatGPT / Claude web** | The AI can't browse your disk. You upload the raw files and the map into the chat, and paste answers back into your folders yourself. Same 5 steps, more copy-paste. |

> **AI: ask which tool the user is on, then tailor the walkthrough.**

---

## Step 1 — Set up the structure

Create one main folder (e.g. `Knowledge Base/`) containing three subfolders and one file:

```
knowledge-base/
├── CLAUDE.md      ← the Map / Schema: rules for how the librarian works
├── raw/           ← your junk drawer: dump clippings, notes, transcripts, screenshots
├── wiki/          ← the organized area the AI writes and maintains
└── outputs/       ← answers, briefings, and reports the AI generates for you
```

Prompt (Claude Code / Cowork):

> "Create a knowledge-base structure in this folder: subfolders `raw`, `wiki`, `outputs`, and a `CLAUDE.md` map file. Leave `CLAUDE.md` as a stub — we'll write the rules together in Step 3."

The `CLAUDE.md` is the heart of the system. We write it carefully in Step 3, *after* you've seen what your raw material looks like.

---

## Step 2 — The information dump

Move your existing knowledge into `raw/`. **Do not organize it.** The entire point is to offload tidying onto the AI.

What to dump:
- Web articles → use a browser clipper (e.g. **Obsidian Web Clipper**) to save pages as clean `.md` with one click.
- Book quotes, meeting notes, voice-memo transcripts → paste into `.md` files, any names, any structure.
- Screenshots and PDFs → drop them in; the AI can read them.

Rule of thumb: if capturing it takes more than a few seconds of tidying, you're doing the librarian's job. Just dump.

---

## Step 3 — Build the wiki

First, write the map. This is what turns a pile of notes into a *maintained* wiki. Give the AI this prompt:

> "Let's write my `CLAUDE.md`. Based on the kind of material in `raw`, propose a schema: the standard format for a wiki page, how pages link to each other, how the index is maintained, naming rules, and how you should handle duplicates and contradictions. Draft it, then explain each rule so I can adjust."

**Map / schema template — `CLAUDE.md`:**

```markdown
# Knowledge Base — Operating Manual (for the librarian)

## Folders
- `raw/`     — source material I dump. NEVER edit or delete anything here.
- `wiki/`    — the maintained knowledge. You author and update this.
- `outputs/` — answers and reports you generate on request.

## Your job
Read `raw/`, distill it into the wiki, keep the wiki consistent, and answer
my questions against it. When I give you a good answer to save, file it.

## Wiki page format
Every page in `wiki/` is a markdown file with this shape:
---
title: <concept>
tags: [ ... ]
sources: [ raw/<file>, ... ]      # where this came from
updated: YYYY-MM-DD
---
## Summary
2–4 sentences, plain language.
## Details
The substance, in your own words.
## Connections
- [[other-page]] — one line on how they relate.

## Rules
- One concept per page. Name files `kebab-case-topic.md`.
- Link generously: every page names its related pages under Connections.
- Maintain `wiki/index.md`: a categorized list of every page with its 1-line summary.
- Cite sources: every claim traces to a file in `raw/`.
- Deduplicate: if a concept exists, extend that page — don't make a second one.
- Contradictions: don't silently pick a side. Note both and flag them for me.
- Never invent facts. If raw material is thin, say so rather than filling gaps.
```

Then build it with a single prompt:

> "Read everything in `raw` and compile a wiki in the `wiki` folder following the rules in your `CLAUDE.md`. Create `wiki/index.md` plus one page per concept, with summaries, source citations, and cross-links. When you're done, show me the index and list anything that was ambiguous."

Review the index it produces. If a page is wrong, tell the librarian how to re-file — don't hand-edit.

---

## Step 4 — Ask questions and save outputs

Now query your knowledge base:

> "Using only my wiki, answer: [your question]. Cite the pages you used. If the wiki doesn't cover it, tell me what's missing."

When an answer is genuinely useful, **save it back** — this is the compounding step:

> "That's worth keeping. Save it to `outputs/` as a dated briefing, and if it introduced a new concept or connection, add or update the relevant wiki page and the index."

Every good answer that gets filed makes the *next* question easier to answer. That's the whole flywheel.

---

## Step 5 — Monthly health check

Once a month, have the librarian audit itself:

> "Do a health check on the wiki. Find contradictions between pages, spot claims with no source in `raw`, list concepts that are mentioned but have no page yet, suggest missing connections between existing pages, and flag anything that looks stale or duplicated. Give me a prioritized list before changing anything — then, once I approve, fix what I check off."

Optional power-up (if your AI can search the web): add *"…and for gaps, propose what to research to fill them"* so the audit also grows the base outward, not just cleans it.

---

## The loop (why it compounds)

```
  dump into raw ─▶ librarian builds/updates wiki ─▶ you ask questions
        ▲                                                   │
        │                                                   ▼
        └────────── file good answers back ◀── save to outputs / wiki
                    (each answer makes the next one easier)
                              │
                              ▼
                   monthly health check keeps it honest
```

The knowledge base isn't a folder you fill once. It's a system that gets *more* intelligent every time you use it, because both your questions and their answers feed back into what the librarian maintains.

---

## Related system

If you also want the AI to run a *workflow* (draft → edit → publish) rather than organize information, see the companion manual: **the Three-Layer Folder System** (Map / Rooms / Workspace). Same map-file idea, pointed at a pipeline instead of a librarian.
