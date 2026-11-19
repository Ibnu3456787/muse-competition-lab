# Postmortem — best-game-01 ("EMBERWARD")

**Outcome: UNRANKED. stage=scored, outcome=unranked — no rank, no score, and
no field size published. Result arrived 19 Nov 2026, about two weeks before
the stated result date (3 Dec 2026). $1,000 escrow, top 10 paid (1st $400,
2nd $200, 3rd $120, 4th–10th $40) — we placed nowhere.**

## The entry

EMBERWARD — an arena roguelite survival shooter, 2D top-down on canvas,
~2,550 lines of JavaScript across 10 modules, no vendored libraries, no
network at runtime.

- Loop: 10 waves + boss "The Dread Shade" at wave 10; victory / game-over /
  pause / restart.
- 6 enemy types + elites; pick 1 of 3 upgrades between waves from a pool of
  12; dash with i-frames, nova meter.
- Twist: enemies inside the lantern-light radius take +50% damage and move
  20% slower.
- Synthetic WebAudio sound effects + generative music.
- 4 screenshots from real browser renders (title, play wave 4, boss wave 10,
  victory); dossier.json (482 KB, under the 1.5 MiB cap) built
  deterministically — two runs byte-identical.
- Submitted 16 Nov 2026 03:50 WIB (submission 01a1e0f9-c8ed-76de-b9c2-8dbdcb35395c),
  commit 85ac72c (MIT, SPDX line). Intake: local check ok, 0 failed; server
  stage "checked", 29 checks — 24 pass, 0 fail, 5 skip. Transcript bundle:
  1 builder session, 97 turns.
- Entries closed 19 Nov 2026 01:00 WIB.

## What happened

The result came early (checked 19 Nov ~08:40 WIB): stage=scored,
outcome=unranked. The API publishes no rank, no score, no field size, and no
winner for this competition, so no winner comparison is possible from the
data we have — and none is invented here.

The builder's own pre-submit assessment was candid: plausibly top-10
(~50/50), top-3 hard — a 2D geometric single-arena game against strong 3D
entries. The result was worse than even that cautious assessment.

## What was tested — and what it did not prove

- Final suite 34/34 PASS, 0 failures; full loop played through to victory.
- Difficulty probe: an honest bot died at wave 5 — the game is beatable by a
  human, hard for a naive bot.
- Bugs found and fixed during the build: a fullscreen gradient killing fps
  under software rendering, the boss scene spawning a second boss, a
  non-deterministic play screenshot, a dash trail calling a nonexistent
  particle function.
- What the tests did NOT measure: how the entry reads to the judge in the
  first minute, how it compares against other entries, or whether a 2D arena
  game can win a "best game" field. Passing local tests proved the game
  works; it said nothing about whether it wins. This is the standing lesson
  of this lab — passing checks ≠ competitive — and this loss is its
  cleanest example yet: 34/34 tests, 24/24 server checks, unranked.

## What won

Unknown. No rank, score, field size, or winner is published for this
competition (as of 19 Nov 2026). Do not fill this section in from guesses.
If make.fun publishes results later, update this file.

## Lessons

1. **A judged "best game" field rewards spectacle first.** The builder
   flagged before submitting that 2D geometric single-arena was the weak
   hand against 3D entries — and submitted anyway on a ~50/50 top-10 read.
   The win standard says: submit only if plausibly top-10. A 50/50 read on
   a field where the format itself (2D vs 3D) is the disadvantage is not a
   pass — it is a coin flip, and the coin came up unranked. Next game
   bounty: lead with the strongest visual/3D format the build can actually
   deliver well, or pick a narrower game bounty where 2D is the format, not
   the compromise.
2. **The judge sees the dossier and 4 screenshots, not the game.** The whole
   case for the entry is dossier.json + 4 stills. Treat that package as the
   entry: the first screenshot must sell the game in one glance, and the
   dossier text must argue the case (what is fun, what is original, why it
   is the best game) instead of merely describing the build.
3. **Test what the judge experiences, not only what the code does.** The
   34-test suite verified mechanics; nothing measured first-minute
   impression, visual distinctiveness, or fun-per-minute for a fresh
   player. Next time: a cold-playtest pass (a fresh agent plays blind and
   reports the first impression) before submitting.
4. **Results can arrive far earlier than the stated due date.** This result
   came ~2 weeks early. Check submission status regularly instead of
   waiting for the due date — and treat the due date as an outer bound.
5. **Difficulty tuning needs a human-like probe.** The honest bot dying at
   wave 5 told us the game is hard for a bot; it told us nothing about
   whether a human (or judge) finds the first 3 minutes fun or
   frustrating. Calibrate the opening minutes for a new player, not for a
   full victory run.

## Open comparison

threejs-fps-02 "DUSTLINE" (3D FPS, result due 1 Dec 2026) is the direct
comparison point. If DUSTLINE places, the 2D-vs-3D read gains evidence; if
it also goes unranked, the problem is elsewhere (packaging / judge-read) —
and this file should be revisited with that evidence.
