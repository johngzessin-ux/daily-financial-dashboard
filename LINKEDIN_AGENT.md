# LinkedIn Agent

Drafts a ready-to-post LinkedIn update from the day's `index.html` financial
digest. Output lives in `linkedin-post.md` at the repo root and is overwritten
each time the agent runs — copy/paste it into LinkedIn manually, no API
posting is wired up.

## What it does

1. Reads the current `index.html` digest (Private Investments, Equities,
   Fixed Income, Geopolitical Events).
2. Picks the 3-5 most client-relevant threads for the day.
3. Writes a LinkedIn-ready post to `linkedin-post.md`:
   - A hook line, a few insight paragraphs in plain language (no jargon
     dumps), a soft call-to-action, and 4-6 relevant hashtags.
   - Roughly 150-250 words — long enough to be useful, short enough to read
     on a phone.
4. Commits and pushes the updated `linkedin-post.md` directly to `main`,
   mirroring how the dashboard's own daily update lands on `main`.

## Running it manually

Ask Claude to "regenerate the LinkedIn post from today's dashboard" and it
will redo the steps above.

## Automation

A daily Routine triggers this in a fresh session. Adjust or disable it via
the Claude Code Remote trigger tools (`list_triggers` / `update_trigger` /
`delete_trigger`).
