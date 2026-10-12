# Conventions for this repo

## Identity — non-negotiable
This repo is personal work. Commits must be authored as
`Toshali Mohapatra <53348090+wildchaser1703@users.noreply.github.com>`
and `origin` must point at `github.com-wildchaser1703`.
**Never run `gh` in this repo** — the gh CLI is authenticated to a work account
and `gh repo create` / `gh repo fork` would create under the wrong owner.
A pre-commit hook enforces both rules.

## Measurement standard (SOP-04) — applies to every number
Before: record model repo + revision hash, runtime version/commit, quant flags,
OS version, machine and thermal state in `VERSIONS.md`. Fix the seed. Fix the
prompt set. Decide the repeat count *before* running.
During: discard the first run as warmup, always. Minimum 5 repeats for anything
published. Enforce a cooldown gap between configs — a warm laptop benchmarks
the laptop, not the model. Sample power and memory concurrently.
After: report mean **and** spread. CV above 5% means add repeats or find the
confound, never publish and hope. Raw output goes to `results/` as JSON and is
committed. Charts are generated from committed data, never hand-entered.
Record what would falsify the finding; if nothing would, it is not a finding.

## Repo rules
- `data/` is gitignored except fetch scripts and small probe files. Corpus
  licences often bar redistribution — commit the fetch script, not the corpus.
- `results/` is **always committed**.
- Models live in `~/models/`, never in the repo.
- Python is 3.12 via uv. Never the system 3.14 — ML wheel coverage lags.
- Conventional commits: `feat:` `fix:` `bench:` `docs:` `chore:`.
- Tag the commit behind every published number: `bench-YYYY-MM-DD-<topic>`.
- The README must let a stranger reproduce the headline number. That is its
  acceptance test.

## Scope
One ticket at a time. No unrelated refactors, no speculative improvements.
