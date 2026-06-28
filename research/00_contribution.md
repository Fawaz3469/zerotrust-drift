# Phase 0 — Lock the contribution

## The project in plain terms

Think of a security guard given one rule years ago: "blue badges in, everyone else stop."
Perfect on day one. But the company switched to green badges, changed shift times, moved
offices — and nobody re-briefed the guard. He's now quietly making wrong calls, and no one
notices because the rule still *looks* fine. It's just out of date.

Swap the building for a **cloud**, the guard's rule for a **Zero Trust access policy**, and
badges for **user behaviour**, and that's the problem this project attacks. The twist: many
companies share the cloud (**multi-tenant**), they won't share private data, so the detector
is trained **federated** — each keeps its data at home, shares only what it learned.

## The draft contribution sentence (the north star)

> Existing federated drift work detects drift in order to **retrain a model and keep it
> accurate**. We instead treat federated behavioural drift as a signal that a tenant's
> **Zero Trust policy has gone stale**, and show that cross-silo federation flags policy
> staleness **earlier and more reliably** than single-tenant or centralised detection —
> without tenants sharing raw behavioural data.

**Your one job in Phase 0:** read the 3 papers below (intros + related-work only), then
rewrite that sentence in your own words once you can clearly finish: *"everyone detects
drift to fix the model — I detect drift to flag a stale policy."*

## The 3 papers to read first (closest prior work)

1. **Ganguly & Aggarwal (2022)** — "Online Federated Learning via Non-Stationary Detection
   and Adaptation amidst Concept Drift." arXiv:2211.12578.
   → Shows FL + drift, but to *keep the global model accurate*. Note how that differs from you.

2. **FL-MalDrift (2025)** — "FL-MalDrift: a federated learning framework for malware
   detection under local concept drift." Scientific Reports.
   → Each client detects drift locally before aggregation. Closest *mechanism* to yours.

3. **Shen — "A Survey of Access Control Misconfiguration Detection Techniques."**
   arXiv:2304.07704.
   → The academic anchor for "policies go wrong / stale." Helps you formalise *staleness*.

## Prior art to explicitly distinguish (do NOT skip)

- **US Patent — "Enforcing security policies in a zero trust framework using a behavioral
  score."** Feeds a behavioural score into the ZT policy engine for *real-time allow/deny*.
  You must cite this and explain the difference: that's per-request decisioning; you detect
  that the *policy baseline itself* has gone stale over time. Different problem.

## After reading — write here:

- My sharpened contribution sentence:
  _(fill in)_
- The single clearest gap I'm filling:
  _(fill in)_
