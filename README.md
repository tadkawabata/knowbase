# AI Workspace Manuals

Two setup guides for using folder structure as the interface to an AI assistant. Each manual doubles as a paste-in guide: drop the whole file into Claude or ChatGPT and it walks you through the build one step at a time.

## The core idea

Both systems use one small "map" file (`CLAUDE.md`) that an AI reads first, which points it to the detailed files only when a task needs them. The map stays in context; everything else loads on demand. That's what keeps the AI focused, cheap to run, and less prone to hallucinating from irrelevant data.

## What's inside

- **[three-layer-folder-system-setup.md](three-layer-folder-system-setup.md)** — the **Three-Layer Folder System**. A Map / Rooms / Workspace structure for running a *workflow* (e.g. draft → edit → publish). You move and name files; the AI reads only the room the task belongs to.
- **[self-improving-knowledge-base-setup.md](self-improving-knowledge-base-setup.md)** — the **Self-Improving Knowledge Base**. A `raw` / `wiki` / `outputs` structure where you dump messy notes and an AI "librarian" organizes them into a maintained wiki that gets smarter the more you use it.

## Start here

1. Pick the manual that matches what you want: a workflow pipeline, or an organized knowledge base.
2. Open the file and paste its full contents into Claude or ChatGPT.
3. Send: *"Be my setup guide for this. Walk me through it one step at a time, and wait for me to confirm each step before moving on."*
4. Follow along — you'll have a working setup in well under an hour.

## What you need

- An AI assistant (Claude or ChatGPT). Smoothest with a tool that can see your local files — **Claude Code** or **Claude Cowork** — so the AI reads and writes your folders directly. Plain web chat works too; you just paste and upload by hand.
- A folder on your computer and any plain-text or markdown editor.
