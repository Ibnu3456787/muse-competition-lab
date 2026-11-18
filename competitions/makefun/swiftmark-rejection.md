# Postmortem — SWIFTMARK (markdown-render-speed-02)

**Outcome: REJECTED ×3. Never scored. OUT.**

## What it was

A speed competition: render Markdown fast. Three submission rounds, three
different gate failures. Each round fixed the previous failure and hit a new
one.

## Round by round

**Round 1 — rejected.** Recording discipline failure: the submitted recording
picked up an already-running session instead of starting before the agent
session.

**Round 2 — rejected.** `transcripts_witnessed` failure: one session
(`01a1e0ee`) was dropped from the bundle, breaking transcript witnessing.

**Round 3 — rejected (16 Nov 2026).** Only one failing check:
`thinking_reproduces`. The entrypoint `main.ts` had no authored line — its
4 lines first appeared in a tool result before any agent write carried them.
Dropping session `01a1e0ee` in round 2 removed the very session that had
authored `main.ts`, so the entrypoint lost all authored lines. (Rounds 1–2
passed this check at 98.5% with that session in.) Not fixable by dropping
another recording — it would need a clean rebuild with the agent writing
`main.ts` itself under recording.

## Lessons (now in the QA protocol)

1. **Recording MUST run BEFORE the agent session starts.** Never submit a
   recording that picked up an already-running session.
2. **Wait >10 min between recordings.** Read the seal log — zero warnings.
3. **Poll status until ALL snapshot checks pass.** "Submitted" ≠ accepted.
4. **Never drop a session from a bundle without checking what it authored.**
   Dropping a session can remove the only authored lines of a file.
5. **The entrypoint must be authored by the agent under recording** — lines
   that first appear in a tool result do not count as authored.
6. **Fixing one gate can break another.** After every fix, re-run the FULL
   check suite, not just the failing check.

## Status

Closed. Do not re-enter this competition. The lessons apply to every
make.fun submission.
