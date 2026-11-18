# QA Protocol

**Origin:** MUSE Competitive Intelligence v1.0, Phases 4–5 (operator doctrine,
18 Nov 2026), plus Roles 4–5 of the Master Skill. This file covers testing,
benchmarking, and optimization — everything between "it runs" and "submit".

## Phase 4 — Competitive Benchmarking

Do not stop when the program runs. Do:

- Unit testing.
- Integration testing.
- Edge-case testing.
- Performance testing.
- Stress testing where relevant.
- Benchmark against the baseline.
- Regression testing after fixes.

Use the official local grader when available. Never claim to have passed
hidden tests that cannot be accessed.

## Adversarial QA (Role 4)

Think like a strict competition grader. Test:

- Normal inputs.
- Empty inputs.
- Invalid inputs.
- Boundary values.
- Large inputs.
- Unexpected combinations.
- Runtime and memory consumption.
- Repeated execution.
- Deterministic behavior where required.

Never claim hidden tests passed unless their results are actually available.

## Phase 5 — Iterative Optimization

After obtaining a score:

1. Identify the worst-performing part.
2. Find the likely cause.
3. Form an improvement hypothesis.
4. Implement one measurable change.
5. Re-run the benchmark.
6. Compare before and after.
7. Keep only changes that genuinely improve the result.

Do not optimize based on untested assumptions.

## Competitive Optimizer loop (Role 5)

1. Record the current score.
2. Identify the weakest metric.
3. Form a specific improvement hypothesis.
4. Change one important variable at a time.
5. Run the same benchmark again.
6. Compare the results.
7. Keep improvements supported by evidence.

Do not optimize based on intuition alone.

## Submission gates (learned the hard way)

These failures cost real entries — verify every one before submitting:

- **Run the official check tool** and confirm `ok:true` with zero failed
  checks. A rejected entry scores 0 no matter how good the artifact is.
  (Lost: cutest-cat-01 ×2, werewolf-agent-01 v2, SWIFTMARK ×3.)
- **Verify the grading environment has what the submission needs.** A
  submission that cannot reach its model/API at grade time scores ~0.
  (Lost: photo-geolocator-01 — 300 model calls answered 401, no provider key.)
- **Verify the session/transcript records are complete and genuine.**
  Recordings must start BEFORE the agent session; never submit a recording
  that picked up an already-running session.
- **Verify determinism** where the competition requires it — run the grader
  multiple times and confirm identical results.
- **Test dozens to hundreds of times; submit only the best.** (Operator rule.)
