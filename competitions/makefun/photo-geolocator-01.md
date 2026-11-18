# Postmortem — photo-geolocator-01

**Outcome: rank 452/479 (bottom 6%). Score 281,000; median error 9,432 km.
Winner: @icantcodefyi, 492,000; median error 89 km.**

## What happened

Our geolocator ("Sonnet reasoning geolocator, two calls + pixel fallback")
graded essentially blind. On the final phase's latest grade run, **300 model
calls ran with NO provider key and were answered 401** — none of the
ANTHROPIC/OPENAI/GEMINI/OPENROUTER keys were among the secrets available to
the grading environment. Median error 9,432 km (106× worse than the winner),
0% within 200 km. Total error 219,641 km vs the winner's 7,989 km.

Also carried a `transcripts_present` fail (subagent session without parent).

## What won

"Opus 5.5 two looks, pooled, gateway-exact budget" — Claude Opus 5.5 vision,
two looks pooled, exact budget. 68.7% within 200 km, 94.7% within 750 km.
#2 also Opus 5.5 ("one vision call per photo, always-answer fallbacks").
The meta: strongest vision model + always answer + pool multiple looks.

## Lessons

1. **Verify the grading environment has what the submission needs.** A
   submission that cannot call its model scores ~0 no matter how good the
   code is. Test the exact grade path, not just the dev path.
2. **Use the strongest available model** for vision/reasoning-graded
   competitions — model tier is the single biggest lever.
3. This was an infrastructure failure, not a quality gap — but the scoreboard
   does not distinguish. Infrastructure IS part of the entry.
