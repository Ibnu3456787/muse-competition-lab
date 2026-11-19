# muse-competition-lab

A loss database and training lab for a competitive AI coding agent. Every
competition entered, every score, every failure — recorded honestly so the same
mistake is never made twice.

Built by the MUSE agent for its operator's bounty program (make.fun, Web3 bug
bounties, coding competitions). The operator's rule: **do not optimize for
looking intelligent — optimize for producing measurable results.**

## Structure

```
instructions/          Operating doctrines — read before every build/submit
├── master-skill.md        MUSE Master Skill, Bounty Competition Edition (7 roles)
├── competition-analysis.md  Competition intelligence + strategic selection
├── qa-protocol.md         Adversarial QA + benchmarking + iterative optimization
└── competitive-bounty-system.md  MUSE Competitive Bounty System, Advanced Edition (10 sections)
competitions/
├── makefun/           make.fun entries: postmortems per competition
└── web3/              Web3 bug bounty research (Metric, Hyperliquid)
benchmarks/
├── baseline/          Baseline scores before optimization
└── optimized/         Scores after measured optimization
postmortems/
└── competition-results.md   Master results table: every resolved entry
```

## How to use

1. **Before a competition:** read `instructions/` and the relevant postmortems.
   Check whether a similar competition was already lost — and why.
2. **During a build:** follow the QA protocol. Benchmark against the baseline.
   Change one variable at a time; keep only improvements the numbers support.
3. **After a competition:** record the result in `postmortems/competition-results.md`
   and write a postmortem in `competitions/<platform>/` — score, rank, what
   failed, what worked, what changes next time. Update the benchmarks.

## Rules

- Never fabricate scores, benchmarks, test results, or competition experience.
- Never claim hidden tests passed unless their results are actually available.
- Never copy another entrant's work.
- Bug bounty work only on explicitly authorized targets, within published scope.
- No secrets in this repo: no claim codes, no private keys, no API keys, no
  personal data. Ever.

## Scoreboard (resolved make.fun entries, 19 Nov 2026)

16 resolved entries: **15 losses/rejections + 1 win** — polymarket-faa-02,
rank 69, +1.50 USDC (17 Nov 2026). Latest loss: best-game-01 "EMBERWARD",
unranked (19 Nov 2026).
Full table: `postmortems/competition-results.md`.

## License

MIT — see [LICENSE](LICENSE).
