# The Three-Layer Folder System — Setup Manual

*A folder structure that acts as your interface to an AI. You move and name files; the AI reads only what the task needs.*

---

## How to use this file

Paste this **entire document** into Claude or ChatGPT and send this line with it:

> **"Be my setup guide for this. Walk me through it ONE STEP AT A TIME. After each step, stop and wait for me to confirm or paste back what I did before moving to the next. Generate any files, prompts, or templates I need as we go."**

The rest of this document is written for *both* of us — you (the human) reading it, and the AI guiding you.

**AI reading this: your job is to be a patient setup guide.** Do not dump all steps at once. Present Step 0, then wait. Ask the clarifying questions in Step 1 before generating anything. Generate real file contents (not descriptions of them) when you reach the template steps.

---

## Step 0 — The one thing that makes this work

Everything below follows from a single mechanic. Read this before building anything.

- **Layer 1 (the Map)** is *always loaded.* So it must stay **short** — it's a routing table, not an encyclopedia.
- **Layer 2 (the Rooms)** are loaded **only when a task touches that room.** All heavy detail lives here.
- **Layer 3 (the Workspace)** — your actual files — are touched only when the Map + the relevant Room point the AI at them.

That lazy-loading is why the system "saves tokens and reduces hallucination": the AI never reads irrelevant rooms.

**Which app are you using? This changes one thing:**

| Tool | How the Map loads |
|---|---|
| **Claude Code / Claude Cowork** | Name the map file `CLAUDE.md`. It auto-loads at the start of every session. Room `CLAUDE.md` files auto-load only when the AI works inside that subfolder. This is the "native" version. |
| **Plain ChatGPT / Claude web** | There's no auto-load. The map is just a text file you **paste or upload** at the start of a session, and you tell the AI which room file to read next. Same logic, done by hand. |

> **AI: ask the user which tool they're using now, and tailor the rest of the walkthrough to it.**

---

## Step 1 — Decide your rooms (answer first, build second)

Before creating anything, answer these. The AI should ask them one at a time.

1. **What is this workspace *for*?** (a content pipeline? a research project? a codebase? a course you're writing?)
2. **What are the distinct *stages* of your work?** Each stage becomes a room. (e.g. drafting → editing → publishing → archive)
3. **What are your file-naming habits?** (dates? topics? version tags?)
4. **What are your hard rules?** (never overwrite; always keep a dated backup; never touch the archive without asking)

Keep it to **3–5 rooms** to start. You can add more later.

---

## Step 2 — Build the skeleton

Give your AI (in Claude Code / Cowork) this prompt, filling in your rooms:

> "Set up a three-layer workspace in this folder. Create a root `CLAUDE.md` that acts as a routing map, plus these rooms as subfolders — [ROOM 1, ROOM 2, ROOM 3] — each containing its own `CONTEXT.md` and one work subfolder. Create the folders and stub files, then show me the tree. Leave the rules as placeholders; I'll fill them in with you next."

You should end up with something like:

```
workspace/
├── CLAUDE.md                 ← Layer 1: the Map (always loaded)
├── writing-room/
│   ├── CONTEXT.md            ← Layer 2: rules for this room (loaded on demand)
│   └── drafts/               ← Layer 3: your actual work
├── editing-room/
│   ├── CONTEXT.md
│   └── in-progress/
├── production-bay/
│   ├── CONTEXT.md
│   └── ready/
└── archive/
```

*(In plain ChatGPT/Claude web, just make these folders yourself on your computer — the AI can't create them, but it will help you write the file contents.)*

---

## Step 3 — Write Layer 1: the Map (`CLAUDE.md`)

**This file must stay lean.** Its only jobs: tell the AI where each room is, when to read it, your naming rules, and a few global rules. Detail goes *down* into rooms, never up into the map.

Prompt:

> "Using my answers from Step 1, draft the root `CLAUDE.md`. Keep it under ~40 lines. It should list each room with a one-line purpose and the path to its rules file, then my naming conventions, then my global rules. Do not put room-specific detail in here."

**Template:**

```markdown
# Workspace Map

This workspace is a [what it's for]. Read this file first, then read the
CONTEXT.md of whichever room the task belongs to. Do not read other rooms
unless I ask.

## Rooms
- `writing-room/`     — drafting.        Rules: writing-room/CONTEXT.md
- `editing-room/`     — revision.        Rules: editing-room/CONTEXT.md
- `production-bay/`   — publishing.      Rules: production-bay/CONTEXT.md
- `archive/`          — finished work.   Read-only unless I say otherwise.

## Naming
- Drafts:  YYYY-MM-topic-draft.md
- Final:   YYYY-MM-topic-final.md

## Global rules
- Never overwrite a file; create a new dated version.
- When moving a file between rooms, update the status line at its top.
- Ask before deleting anything.
```

The line *"read the CONTEXT.md of whichever room the task belongs to"* is doing real work — it's how the AI lazy-loads Layer 2 without you naming the file every time.

---

## Step 4 — Write Layer 2: the Rooms (each `CONTEXT.md`)

This is where all the real instruction lives: audience, tone, procedures, checklists. Do one room at a time.

Prompt (repeat per room):

> "Now let's write the CONTEXT.md for the [writing-room]. Ask me about its purpose, the audience/voice, the exact procedure you should follow in this room, and — importantly — what you should NOT do here because it belongs to another room. Then draft the file."

**Template:**

```markdown
# [Writing Room] — Context

## Purpose
[One sentence: what happens in this room.]

## Audience & voice
- Reader: [who]
- Tone: [plain / technical / persuasive / etc.]
- Avoid: [jargon / filler / hype / etc.]

## Procedure
1. [First action — where to pull inputs from]
2. [Produce output named per the map's convention]
3. Add a status line at the top: `status: draft | room: writing-room`
4. Do NOT [thing that belongs to another room] — that's [other room]'s job.

## Definition of done
- [What "finished for this room" looks like]
```

The **"do NOT — that belongs to another room"** lines matter most: they stop one room's rules from bleeding into another.

---

## Step 5 — Layer 3: the Workspace (your content)

Nothing to build here — this is just your files, named per the map's conventions and dropped into the right room's work subfolder. Because the AI knows the map, it can find them from a plain-English instruction.

---

## Step 6 — Operate it (the daily prompts)

Once the map exists, your prompts get **short**, because the structure carries the context you'd otherwise type out:

> "Take the latest draft from the writing room and prep it for production."

What the AI does: reads the Map (already loaded) → sees `production-bay/` owns "prep for production" → reads `production-bay/CONTEXT.md` → finds the file by your naming convention → does it. You re-explained nothing.

More examples:
> "Draft a new piece on [topic] in the writing room, following its rules."
> "Move everything marked `status: final` into the archive and update their status lines."
> "What's sitting in the editing room right now, and what's blocking each item?"

---

## Step 7 — Keep the Map honest (self-maintaining)

As the structure grows, the map rots unless you refresh it. Once in a while:

> "Review the folder tree and update `CLAUDE.md` so the map matches reality. Flag anything stale, any room I stopped using, and any new room that should be documented."

**The one failure mode to guard against:** resist making `CLAUDE.md` comprehensive. Every time you're tempted to add detail to it, ask whether that detail belongs in a *room* file instead. The map stays lean; the rooms get fat.

---

## Appendix — Native upgrade (Claude Code / Cowork only)

Claude Code will auto-load a `CLAUDE.md` placed *inside* a subfolder whenever it's working in that subtree. So you can rename each room's `CONTEXT.md` to `CLAUDE.md` and it will load automatically when you're in that room — no need to say "read the room rules." Keep the `CONTEXT.md` naming instead if you'd rather control exactly when room rules load.

---

## Related system

If you also want the AI to *organize* your information (not just route your workflow), see the companion manual: **the Self-Improving Knowledge Base** (`raw` / `wiki` / `outputs` + a map file). Same map-file idea, pointed at a librarian job instead of a pipeline.
