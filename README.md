# Federated Behavioural Drift Detection for Zero Trust Policy Staleness in Multi-Tenant Cloud

Yeah, the title's a mouthful. Here's what it actually means.

## The idea, starring a security guard

Picture a guard who got one instruction years ago: blue badges get in, everyone else gets stopped. Worked great on day one. Then the company switched to green badges, moved floors, changed the shifts... and nobody told the guard. He's still running the old rule, quietly turning away the right people and occasionally waving through the wrong ones. Nothing *looks* broken. The rule just silently went out of date.

Now swap the building for a cloud, the guard's instruction for a Zero Trust access policy, and the badges for how users actually behave. Same story: the policy was correct when it was written, behaviour slowly shifted, and now it's making bad calls nobody notices.

This project builds the thing that taps the guard on the shoulder and goes "hey, your rule's outdated, go check it."

The catch: tons of companies share one cloud (the "multi-tenant" bit), and none of them will hand over their users' private data. So instead of dumping everything in one place, each company learns locally and only shares what it *figured out*, never the raw data. That's the "federated" bit. Nice side effect: if one company runs into a new behaviour pattern early, everyone else gets a warning before it bites them too.

## What's actually new here

Loads of people already do "federated learning + drift detection." But they all use it for the same goal: spot the drift, retrain the model, keep it accurate.

I'm flipping that. I use the same drift signal to figure out when the *security policy* has gone stale and needs a human to look at it. Think smoke alarm for outdated rules, not a retrain trigger.

One-liner: everyone else detects drift to fix the model. I detect drift to flag a stale policy.

## How it works (6 moving parts)

1. **Fake the shared cloud** — chop one public security dataset into 5-10 pretend companies.
2. **Hand each a rulebook and freeze it** — train a small model on day one, never update it again.
3. **Let behaviour drift** — feed in slowly-changing data so the frozen rulebook starts messing up in a way I can measure.
4. **Catch the drift** — drift detectors (ADWIN, DDM) that trip the "your policy's stale" alarm.
5. **Make them team up** — companies swap model updates, not data, so early drift in one warns the rest.
6. **Prove it's better** — show the federated version flags staleness earlier than any company going solo, and nearly as well as just illegally pooling everyone's data.

That last graph is basically the whole paper.

## Where I'm at

Phase 0 of 6. Foundation's down, nailing the exact contribution.

- [x] **Phase 0** — repo set up, dug through the literature, pinned the core idea
- [ ] **Phase 1** — read everything, write the related work
- [ ] **Phase 2** — design the experiment (the make-or-break part)
- [ ] **Phase 3** — actually build it (Flower for federation, River for drift)
- [ ] **Phase 4** — run it, make the money figure
- [ ] **Phase 5** — write the paper
- [ ] **Phase 6** — find a venue that isn't sketchy, submit

Whole thing runs on a laptop. No GPUs, it's small tabular data and tiny models.

## Poking around

```
research/   my notes, the contribution statement, the lit review
docs/       why I made each call + a running log of what I did and when
data/       datasets live here on my machine, NOT in the repo (way too big)
src/        the actual code (shows up in Phase 3)
notebooks/  messing around
results/    figures and small result files
```

## Running it

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Datasets aren't in here (GitHub rejects anything over 100MB and these run a few GB). Grab them yourself, instructions in `data/README.md`.

## Standing on shoulders

The heavy hitters: NIST SP 800-207 (the Zero Trust bible), McMahan et al. 2017 (where federated learning started), Gama et al. 2014 (the concept-drift survey everyone cites). Everything else is in `research/01_literature.md`.

## Who

Mohammed Fawaz, [@Fawaz3469](https://github.com/Fawaz3469). MIT licensed, go wild (see LICENSE).
