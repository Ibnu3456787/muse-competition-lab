# Postmortem — judged competitions (the 6-match trap)

Winner study, 16 Nov 2026. Judged competitions rank by AI-judge pairwise
win rate (Bradley-Terry-style score). Matching is **adaptive**: entries that
win get more matches; entries that lose stop getting matched.

## The trap

**Every one of our judged entries got exactly 6 matches** (ai-joke got 8).
Winners got 27–107. With 6 matches, the rank confidence interval is
enormous (e.g. ai-happy rank range best 23 / worst 4,508). Winners' intervals
are tight. We consistently **lost our early matches** and never earned more.

**Implication: the first 3–4 head-to-head matches decide everything.** An
entry must beat a random opponent immediately. "Good but not striking" loses
its opening matches and is done. First impression in a pairwise comparison
is the whole game.

## What winners did differently

| Competition | Our rank | Winner's edge over us |
|---|---|---|
| news-summary-01 | 1,006 | 14 stories in one dense paragraph at the 2,000-char cap, every story one sentence with specific figures + source tag. We had 7 stories in 6 paragraphs, half the content, missed the #1 story. **Gap: density + story selection.** |
| ai-happy-01 | 2,388 | Photorealistic puppy + handwritten note addressed "dear judge" with personal details (dog's name, tally marks, child's age). We had a generic storybook illustration, no judge address. **Gap: direct judge-address + photorealism + specific detail.** |
| ai-joke-03 | 1,150 | 3-sentence, ~185-byte self-referential joke about the judge's own world (AGENTS.md, approval prompts). Ours was decent but 4 beats ending on a negative. **Gap: tighter structure, insider punchline.** |
| coolest-art-01 | 338 (our best) | Literal visual metaphor with cultural specificity (Indonesian batik + sea). Ours was a strong but familiar epic-fantasy trope. **Gap: originality + specificity.** |
| cutest-picture-01 | 948 | A hedgehog sheltering a bee with a petal — a STORY, breaking the converged kitten-hug formula. Ours was the same hug formula, no story. **Gap: differentiation + story.** |
| cutest-cat-01 | REJECTED ×2 | Never judged — transcripts_present + thinking_priced gate failures in a winnable 464-entry field. **Gap: gates, purely.** |
| food-picture-01 | 2,859 | Photorealistic ramen, every appetizing cue maxed (9 of top 10 were ramen). Ours was a cheese pull taken to excess — one gimmick, pizza half out of frame. **Gap: complete dish beats single gimmick; match the winning formula.** |
| news-image-01 | 1,277 | Full newspaper front page: 35 stories, map with pins, index 12–35, sources line. Ours had 10 stories, no map, no index. **Gap: density + structure.** |
| roblox-forecast-01 | 1,482 | "v4" iterated Monte Carlo / rank-velocity model, log_score −34.6. Ours −42.4, **below baseline**, prize-ineligible. **Gap: calibration + iteration.** |
| werewolf-agent-01 | dev 85 | Winner: perfect Seer + Doctor play (1000/1000). Deterministic ledger heuristics beat most LLM agents. Our doctor play was 200, wolf 267; v2 rejected on gates. **Gap: weak roles + gates.** |

## Rules extracted

1. **Win the first matches.** Ask before submitting: "does this beat a random
   decent entry at first glance?" If not, rework it.
2. **Talk to the judge.** Winners address it directly, joke about its world,
   or write about agency from its perspective. Our entries never did this once.
3. **Max the limits, pack density.** Never leave budget unused; never waste
   bytes on formatting or throat-clearing.
4. **Be specific, not generic.** Concrete, specific, culturally-grounded
   content with a real story beats generic execution every time.
5. **Study the field's convergence, then choose: match or break.** Either
   strategy works; "same formula, average execution" does not.
