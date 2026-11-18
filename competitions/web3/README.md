# Web3 bug bounty research

Status: in progress. Nothing submitted yet without the operator's explicit
confirmation. All targets are explicitly authorized programs; work stays
within published scope. No exploitation, no user data taken.

Finding details are recorded at category level only — full proof-of-concept
and report drafts stay private until submitted through the program's channel.

## Metric (Immunefi)

- Program: Metric DEX, oracle-anchored (Pyth + Chainlink). Max reward
  $500,000. No KYC. PoC required. No deadline.
- Finding: **Low** — surplus underflow in a fee-collection path, confirmed
  with Foundry (13/13 tests passing).
- Report draft written; submission approved by the operator in principle but
  **not confirmed sent**.
- Next: confirm submission, record outcome here.

## Hyperliquid

- Program: mainnet bugs causing outage or logical error. Rewards in USDC
  (Critical <$1,000,000, High <$50,000, Medium <$10,000). Submission via
  email. KYC/KYB required.
- Finding F-1: **Low** — replay-check gap in a validator-set update path.
  Liveness/griefing impact, no fund loss. PoC 3/3 passing.
- SDK bugs reported separately to GitHub (Rust #199, Python #339 — both open).
- Decisions pending with the operator: (a) fund the testnet faucet (≥5 USDC)
  or not; (b) ask about F-1 scope before submitting.

## Gleam wallet security scan (separate program)

- Community scan of the Gleam Arweave/AO wallet (Chrome extension).
- Round 1 (release v1.48.0, Approval preview area): **1 verified Medium
  finding** — an already-resolved approval could be resolved again after a
  service-worker restart, posting a transfer twice from one approval.
  Demonstrated by test; 5,066 existing tests passing.
- The finding was already fixed on the project's master branch, so the
  advisory may close as a duplicate; the draft's new contribution is a wider
  no-outcome window the fix does not close.
- Advisory form fully filled (CVSS 4.7) but GitHub refused creation
  ("reached the limit for creating advisories") — retry pending. Round 1
  attestation signed; 0 points (no paid places left for v1.48.0).
