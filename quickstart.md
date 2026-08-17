# Quickstart

The 15-minute path from zero to a working setup. The two full manuals in this repo explain everything in depth — this file just gets you running.

## The whole idea (30 seconds)

You keep one small "map" file (`CLAUDE.md`) that an AI reads first. It points the AI to detailed files only when a task needs them, so the map stays cheap and always-loaded while everything else loads on demand. That single trick is what keeps the AI focused and stops it hallucinating from irrelevant data.

Both systems in this repo are that same idea, aimed at two jobs:
- **Organizing information** → the Self-Improving Knowledge Base (`raw` / `wiki` / `outputs`)
- **Running a workflow** → the Three-Layer Folder System (Map / Rooms / Workspace)

Start with the knowledge base. Once it clicks, the other is the same skill pointed at a draft → edit → publish pipeline.

## What you need

An AI that can see your local files — **Claude Code** or **Claude Cowork** is smoothest. Plain ChatGPT or Claude web works too; you just upload files and paste answers back by hand.

## Build a knowledge base in 15 minutes

1. **Make the folders.** Create one folder (e.g. `knowledge-base/`) containing `raw/`, `wiki/`, `outputs/`, and an empty `CLAUDE.md`.

2. **Add the rules.** Open [self-improving-knowledge-base-setup.md](self-improving-knowledge-base-setup.md), copy the map/schema template from **Step 3**, and paste it into your `CLAUDE.md`. Save.

3. **Dump your stuff.** Drop 3–5 things you already have into `raw/` — clipped articles, notes, transcripts, screenshots. Do **not** organize them. That's the AI's job.

4. **Build the wiki.** Point your AI at the folder and send:
   > "Read everything in `raw` and compile a wiki in the `wiki` folder following the rules in your `CLAUDE.md`. Build `wiki/index.md` too, and list anything that was ambiguous."

5. **Use it.** Ask a question:
   > "Using only my wiki, answer: [your question]. Cite the pages you used. If the wiki doesn't cover it, tell me what's missing."

   When an answer is worth keeping, save it:
   > "Save that to `outputs/` as a dated briefing, and update the relevant wiki page and index if it introduced anything new."

That's a live, self-improving knowledge base. Every good answer you file back makes the next question easier.

## Next steps

- **Keep it honest:** once a month, ask the AI to run the health check in Step 5 of the knowledge-base manual.
- **Add a workflow:** when you want the AI to *run a process* rather than organize notes, follow [three-layer-folder-system-setup.md](three-layer-folder-system-setup.md) — same map-file idea, pointed at a pipeline.
