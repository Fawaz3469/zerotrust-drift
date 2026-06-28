# Phase 1 — Literature review

Method: don't collect 50 papers blindly. For each of the 5 building blocks, read the
**survey** + a couple of **anchors**, then snowball from each survey's reference list.
Target ~30 papers. Use Zotero (free) to manage them. Drop PDFs in `research/papers/`
(gitignored — keep them local).

All references below were verified as real. Pull exact bibliographic details from the
publisher / IEEE Xplore / arXiv before citing.

---

## 1. Zero Trust Architecture (the policy foundation)

- **NIST SP 800-207** (Rose et al., 2020) — the definitive ZTA reference. Defines the
  Policy Engine / Policy Administrator / Policy Enforcement Point model. *Always cite.*
- **NIST SP 800-207A** (2023) — multi-cloud / cloud-native ZTA. Your **multi-tenant** anchor.
- Useful motivation: recent work notes NIST 800-207 implicitly assumes the Policy Engine
  has continuous visibility and a *stable* environment — exactly the assumption you attack.

## 2. Policy staleness / drift (the core problem)

- **Shen — Survey of Access Control Misconfiguration Detection Techniques** (arXiv:2304.07704).
  Academic anchor; access-control errors are a top cause of real-world incidents.
- Practitioner framing (use sparingly, for motivation): "configuration drift", "security
  drift", "policy drift" — the same idea under industry names.

## 3. Federated learning for security (the method backbone)

- **McMahan et al. (2017)** — FedAvg, "Communication-Efficient Learning of Deep Networks
  from Decentralized Data." The foundational FL paper.
- **Kairouz et al. (2021)** — "Advances and Open Problems in Federated Learning." Canonical
  FL survey.
- **Hernandez-Ramos et al. (2025)** — "Intrusion Detection based on Federated Learning: a
  systematic review." ACM Computing Surveys. *Mine this for related work.*
- **Lavaur et al. (2022)** — "The evolution of FL-based intrusion detection and mitigation:
  a survey." IEEE TNSM.
- **DÏoT** (Nguyen et al., IEEE ICDCS 2019) and **Mothukuri et al.** (IEEE IoT Journal 2022)
  — the two most-cited FL anomaly-detection systems.
- **Entente** (arXiv:2503.14284) — *cross-silo* intrusion detection with FL. Build your
  terminology on "cross-silo" — each tenant is a silo. Most relevant framing to you.

## 4. Behavioural / concept drift detection (the detection mechanism)

- **Gama et al. (2014)** — "A Survey on Concept Drift Adaptation," ACM Computing Surveys.
  Start here.
- Classic detectors to baseline against: **ADWIN** (Bifet & Gavaldà, 2007), **DDM**
  (Gama et al., 2004), **EDDM**, **Page-Hinkley**. (River implements these.)
- **PWPAE** (arXiv:2109.05013) — concept drift adaptation for IoT anomaly detection;
  bridges drift + security.

## 5. Federated + drift TOGETHER (closest prior work — must engage)

- **Ganguly & Aggarwal (2022)** — arXiv:2211.12578. FL + drift, to keep model accurate.
- **CDA-FedAvg** (Casado et al.) — "Concept drift detection and adaptation for federated
  and continual learning."
- **FL-MalDrift (2025)** — Scientific Reports. Local drift detection before aggregation.

> The pattern in group 5: they all detect drift to **fix the model**. Your move is to use
> drift as a **staleness signal for the policy**. That gap is the paper.

---

## Related Work skeleton (draft as you read)

1. Zero Trust & policy enforcement — what policies are, why they're assumed stable. [§1]
2. Policy staleness / misconfiguration — evidence policies decay; gap: not framed as a
   *detectable, measurable* drift problem. [§2]
3. Federated learning for security — cross-silo IDS exists; gap: aimed at detection
   accuracy, not policy lifecycle. [§3]
4. Concept drift detection — mature toolbox (ADWIN/DDM); gap: applied to model upkeep,
   not policy staleness. [§4]
5. Federated + drift — closest prior work; gap: **drift → retrain model**, never
   **drift → flag stale policy**. ← our contribution. [§5]

## Snowball checklist

- [ ] Zotero installed, collection created
- [ ] Read the 3 Phase-0 papers
- [ ] Read the Gama drift survey + one FL-IDS survey
- [ ] Snowball each survey's references → ~30 papers tagged by building block
- [ ] Draft the 5 Related Work paragraphs above
