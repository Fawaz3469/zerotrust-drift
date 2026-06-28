# Federated Behavioural Drift Detection for Zero Trust Policy Staleness in Multi-Tenant Cloud

A research project + paper. Status: **Phase 0 — locking the contribution.**

## What this is, in one paragraph

On a shared cloud used by many separate companies ("tenants"), each company has a
Zero Trust access policy — a rulebook deciding "can this user access this, right now?".
Over time, user **behaviour drifts**, and those rulebooks silently go **stale**: they keep
making allow/deny calls that are quietly wrong, and nobody notices because the rule still
*looks* fine. This project builds a system that watches behaviour, detects when it has
drifted far enough that a policy is probably out of date, and **flags it for review** — and
it learns this **across all tenants together** (federated learning), so drift one tenant
sees early can warn the others, *without anyone sharing raw private data*.

## The contribution (what makes it a paper)

Existing federated drift work detects drift in order to **retrain a model and keep it
accurate**. We instead treat federated behavioural drift as a signal that a tenant's
**Zero Trust policy has gone stale**, and show that cross-silo federation flags policy
staleness **earlier and more reliably** than single-tenant or centralised detection —
without tenants sharing raw behavioural data.

> This sentence is the north star. It will be sharpened after the Phase 0 reading.
> See `research/00_contribution.md`.

## The plan (6 phases)

| Phase | What | GPU? |
|------|------|------|
| 0 | Lock the contribution (read 3 papers, finalise the one-sentence claim) | none |
| 1 | Literature review (snowball to ~30 papers, draft Related Work) | none |
| 2 | Experiment design — define tenant / drift / policy / staleness metric / baselines | none |
| 3 | Build the harness (Flower for federation, River for drift detectors) | light |
| 4 | Run experiments + ablations + the key figure | light |
| 5 | Write the paper (IEEEtran LaTeX template) | none |
| 6 | Vet the venue carefully, then submit | none |

This whole project runs **locally** on a laptop — it is small tabular data and tiny models.
No CUDA / cloud GPU required.

## Setup

```bash
# from the repo root
python3 -m venv .venv
source .venv/bin/activate        # macOS / Linux
pip install -r requirements.txt
```

## Repo structure

```
research/      notes, contribution statement, literature review, paper PDFs (papers/ is gitignored)
data/          datasets live here LOCALLY — NOT committed (see data/README.md)
src/           project code (added in Phase 3)
notebooks/     exploration / scratch
results/       figures + small result files (committed)
```

## Important: what goes to git and what does not

- **Committed:** code, docs, configs, figures, small `.csv` result summaries.
- **NOT committed:** the raw dataset (multiple GB), the virtual environment, model
  checkpoints, caches. These are excluded by `.gitignore`. The dataset is documented in
  `data/README.md` so the repo stays reproducible without storing huge files.
