---
layout: post
title: The Integrated Vision, GRC as the North Star for Enterprise Architecture
subtitle: A personal take on weaving Governance, Risk and Compliance into the daily life of the architecture practice.
gh-repo: serfies/serfies.github.io
gh-badge: [star, fork, follow]
tags: [EA]
comments: true
mathjax: true
author: Andre Serfontein
---

![The Integrated Vision, GRC as the North Star for Enterprise Architecture](/assets/img/2025-05-28-grc-as-north-star.png)

### Why revisit EA + GRC now?

At the end of my previous blog post I've promised to share how I think Governance, Risk and Compliance (GRC) can be practically integrated with Enterprise Architecture (EA). The information below is the result of a study I have done on the topic of incorporating GRC in lean/agile EA. I should note that I must still implement the "theory" below in practice, so please see the output of my labour below for what it is.

So, the answer **to** the question why I am so interested in GRC and EA is twofold. First, I am of the opinion that architecture is frequently fixated on the R and C of GRC with the G taking a backseat. Secondly, even if architecture is focused on risk and compliance, I think in many cases it is only partially doing so. The point I am making is that GRC extends far beyond just cybersecurity and legal compliance. From an EA perspective, when GRC is fully integrated, it becomes an integrated and proactive capability that underpins an organisation's ability to achieve its objectives reliably, address uncertainty and act with integrity across all operations.

### GRC with agility
 
Ryan Pehrson’s provocation that ([**“Enterprise Architecture is dead”**](https://www.linkedin.com/pulse/enterprise-architecture-dead-ryan-pehrson-sb6de)) really says *traditional, heavyweight* EA is dead and what lives on is a **lean, continuous, product-centred architecture practice** that works at the cadence of agile delivery and DevSecOps pipelines.
As you know I resonate with Kotusev’s three EA functions, **Strategic Planning, Initiative Delivery, Technology Optimisation**, and I believe these still stand, but the *governance fabric* that connects them must become lighter, faster and integrated with the tool-chain.([kotusev.com](https://kotusev.com/The%20Process%20View%20of%20Enterprise%20Architecture%20Practice.pdf))

Below is a consolidated, “agile-ready” view that merges the GRC scope, extra governance layers, and practical play-book from my first two replies.

---

## 1  Governance landscape on one page

(*add the fourth column – “Agile twist” – to your RACI chart*)

| Governance layer                                  | Core focus & artefacts                                                                                                                                                                                                                                                                                   | Typical owners / forums                         | **Agile twist** (lean / continuous)                                                                                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Corporate & IT Governance**(ISO 38500, COBIT)   | Board tech charter (purpose, cadence, KPIs); enterprise risk‑appetite & tolerance matrix; decision‑rights RACI for investment, architecture & operations; executive IT/ESG policies & principles catalogue; major risk indicator dashboard                                                               | Board, CIO, Strategy Office                     | Tie strategy to quarterly **OKRs (Objectives & Key Results)**; use **Lean Portfolio Management (LPM – a SAFe portfolio governance model that funds value streams and manages demand through a portfolio Kanban)** to allocate rolling-wave funding instead of annual budgets.([framework.scaledagile.com](https://framework.scaledagile.com/lean-portfolio-management/?utm_source=chatgpt.com)) |
| **Enterprise-Architecture Governance**            | Enterprise architecture principles library; technology reference models & standards catalogue; reusable pattern library (security, integration, data, ESG); Architecture Decision Record (ADR) templates; variance/exception log & waivers register; EA repository (LeanIX, Confluence) & community wiki | Architecture Review Board (ARB)                 | Replace monthly ARB with **“Architecture Coffee”** sessions inside each PI/Sprint; decisions captured as ADRs in Git repos (just-enough documentation).([apiumhub.com](https://apiumhub.com/tech-blog-barcelona/continuous-architecture-principles-and-goals/?utm_source=chatgpt.com))                                                                                                          |
| **Project / Programme (Value-Stream) Governance** | Lean stage‑gate templates (Idea canvas ➜ Feasibility ➜ Compliance); RAID & dependency log; benefits hypothesis & tracking plan; value‑stream KPIs & OKRs; risk‑adjusted backlog; epic approval workflow; lightweight business‑continuity checklist                                                       | Value-stream steering group, Product Management | Gate 0-1-2 become “**Thin Slices**”: ❶ Lean business canvas ➜ ❷ Architecture spike ➜ ❸ Go/No-go; evidence is automated in the pipeline.                                                                                                                                                                                                                                                         |
| **System / Solution Governance**                  | Authoritative security baseline configs; cost & licence dashboard; SLA/SLO definitions with error budgets; operational run‑book & on‑call playbook; product roadmap & release plan; technical‑debt register; EOL/EOS roadmap; carbon footprint & efficiency report                                       | Product Owner + Site Reliability Engineer       | **Operational metrics as DoD** (security score, cost/hour, carbon g); drift detected by policy-as-code & surfaced on squad dashboards.                                                                                                                                                                                                                                                          |
| **Service-Management (ITIL) Governance**          | Automated change‑management policy; incident & problem workflow (post‑mortem template); DR/BCP run‑books & evidence archive; capacity & performance review cadence; knowledge‑base articles & service catalogue                                                                                          | CAB, Service Mgmt Office                        | Shift CAB to **automated change-approval** for low-risk changes; chaos-engineering days count as DR tests.                                                                                                                                                                                                                                                                                      |
| **Identity & Access Governance**                  | Join‑Move‑Leave workflow; entitlement catalogue & segregation‑of‑duties matrix; privileged‑access management (PAM) vault policies; audit log & quarterly access certification packs; critical access alerting rules                                                                                      | InfoSec, HR                                     | Script quarterly access certification straight from Azure AD / Entra reports into Jira tickets.                                                                                                                                                                                                                                                                                                 |
| **Vendor / OSS / Supply-Chain Governance**        | Contract & SLA repository; third‑party security & compliance assessments; SBOM inventory & vulnerability remediation tracker; open‑source licence compliance log; geopolitical & concentration‑risk watchlist; vendor lifecycle & exit plan                                                              | Procurement, Sec-Ops                            | Embed **SBOM (Software Bill of Materials) scan** in CI; licence breaches create Dependabot issues automatically.                                                                                                                                                                                                                                                                                |
| **FinOps / Cost Governance**                      | Show‑back/charge‑back dashboards; unit‑cost KPIs & budget vs actual review; reserved‑instance & savings‑plan strategy; cost anomaly alerting; optimisation backlog & action tracker; NPV & ROI realisation report                                                                                        | FinOps Guild, CFO                               | Daily cost KPIs on team wall; sprint retros include € / feature burned.                                                                                                                                                                                                                                                                                                                         |
| **ESG / Sustainability Governance**               | Carbon budgets per workload; green architecture guidelines & reference patterns; renewable energy sourcing criteria; e‑waste & asset decommission plan; supply‑chain emissions inventory; sustainability KPIs & board report                                                                             | Sustainability Lead, Cloud CoE                  | Each epic carries a CO₂ estimate; green patterns live in the same pattern repo as security patterns.                                                                                                                                                                                                                                                                                            |
| **Data & AI Governance**                          | Data classification & handling standard; data lineage & ownership diagrams; retention & minimisation policy; data quality SLA & scorecard; AI model cards & governance checklist; bias & fairness assessments; synthetic data & anonymisation policy                                                     | Chief Data & AI Office                          | **Data contract tests** run with the unit-tests; bias metrics reported with model accuracy.                                                                                                                                                                                                                                                                                                     |

---

## 2  Mapping to Kotusev’s three EA processes

| **Kotusev process**         | **Governance touch-points**                                                                                             | **Agile execution hooks**                                                                                                                                                                                                    |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Strategic Planning**      | Corporate/IT Gov, EA principles, risk appetite, LPM budget guardrails, Environmental, Social & Governance (ESG) targets | Quarterly **Portfolio Kanban**; architects join Big-Room Planning to set guardrails & capacity.                                                                                                                              |
| **Initiative Delivery**     | Project & EA governance, identity, vendor, data/AI controls                                                             | **DevSecOps pipeline** enforces policy-as-code, SBOM, IaC guardrails; ARB coffee chat sits inside sprint review.                                                                                                             |
| **Technology Optimisation** | Solution, Service Mgmt, FinOps, ESG                                                                                     | **Continuous Architecture**: measure SLA, cost, carbon; flow findings into backlog; schedule tech-debt fixes alongside features.([continuous-architecture.org](https://continuous-architecture.org/?utm_source=chatgpt.com)) |

---

## 3  Seven agile principles to make GRC “just enough”

| #     | Lean principle                 | How to apply                                                                                                                                                                                                                                                    |
| ----- | ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1** | *Guard-rails, not gates*       | Replace big sign-offs with codified controls (Azure Policy, Terraform Sentinel, GitHub OIDC rules).                                                                                                                                                             |
| **2** | *Architectural runway*         | Keep a backlog of patterns & enablers one PI ahead; prioritise it in the same Kanban as features.                                                                                                                                                               |
| **3** | *Decisions live with the code* | Architecture Decision Records (ADRs) sit next to source; each merge marks a committed decision.                                                                                                                                                                 |
| **4** | *Value-stream budgeting*       | Fund long-lived teams; move money, not people. Lean Portfolio boards review spend vs OKRs monthly.([framework.scaledagile.com](https://framework.scaledagile.com/lean-governance?utm_source=chatgpt.com))                                                       |
| **5** | *Continuous compliance*        | Every commit runs SAST, SBOM, licence scan; every deploy is tagged with risk & KRI metadata.                                                                                                                                                                    |
| **6** | *Metrics over minutes*         | Track lead-time for changes, % builds passing GRC tests, mean time to patch critical CVEs.                                                                                                                                                                      |
| **7** | *Just-in-time architecture*    | Time-box spikes (2 days max) to prove a pattern; don’t model what you can exploit from feedback.([medium.com](https://medium.com/oolooroo/adapting-architectures-practices-for-effective-continuous-software-architecture-a16843d411a4?utm_source=chatgpt.com)) |

---

## 4  Implementation play-book for a small EA team (≤ 5 architects)

| Week              | Outcome                            | Light-weight activity                                                                        |
| ----------------- | ---------------------------------- | -------------------------------------------------------------------------------------------- |
| **1–2**           | *Decision-rights one-pager*        | Workshop with CIO, PMO, InfoSec; publish RACI on Confluence.                                 |
| **3–4**           | *Lean ARB up & running*            | Schedule 30-min weekly “architecture coffee”. Use a 10-question checklist as the agenda.     |
| **4–6**           | *Policy-as-code MVP*               | Pick one cloud control set (e.g. CIS Azure) and implement as Azure Policy + GitHub workflow. |
| **6–8**           | *Portfolio Kanban & OKRs*          | Set up a Jira Portfolio board with swim-lanes for OKR themes; attach budget buckets.         |
| **Quarter 1 end** | *All squads green on GRC pipeline* | Refine CI checks until ≥ 90 % of builds pass security, licence & cost tests.                 |
| **Quarter 2+**    | *Continuous Architecture loop*     | Run “architecture days” every PI to groom runway items, carbon budgets, tech-debt heat-map.  |

---

## 5  Agile GRC cheat-sheet (stick it on the wall)

* □ OKRs link directly to risk appetite and ESG targets
* □ Architecture checklist embedded in Pull-Request template
* □ SBOM & licence scan on every build
* □ Automated change approval for compliant infra-as-code
* □ Sprint retro includes cost, carbon, and risk hygiene metrics
* □ Quarterly access reviews exported as CSV → Jira tickets
* □ Chaos-day counts as DR test evidence
* □ ESG scorecard shared with board alongside financial KPIs

---

### 6  Why this matters

* **Speed with safety** – Lean governance gives teams the psychological safety of clear guard-rails while removing bureaucracy.
* **Single source of truth** – Policy-as-code keeps evidence where auditors – and pipelines – can read it.
* **Strategic pull, not project push** – LPM plus architecture runway ensures every sprint moves strategy forward, not sideways.
* **Sustainability & trust** – Carbon and ethics are first-class citizens, not retrofit concerns.

Stitch these pieces together and you’ll have an EA advisory function that is *very much alive* – enabling value streams, taming risk, and keeping the auditors (and the dev squads) happy. **Lekker, né?**

---

#### Key references

Kotusev process model([kotusev.com](https://kotusev.com/The%20Process%20View%20of%20Enterprise%20Architecture%20Practice.pdf?utm_source=chatgpt.com))  |  Ryan Pehrson on lean EA([linkedin.com](https://www.linkedin.com/pulse/enterprise-architecture-dead-ryan-pehrson-sb6de?utm_source=chatgpt.com))
Continuous Architecture principles([apiumhub.com](https://apiumhub.com/tech-blog-barcelona/continuous-architecture-principles-and-goals/?utm_source=chatgpt.com), [continuous-architecture.org](https://continuous-architecture.org/?utm_source=chatgpt.com))
Lean Portfolio Management & governance([framework.scaledagile.com](https://framework.scaledagile.com/lean-portfolio-management/?utm_source=chatgpt.com), [framework.scaledagile.com](https://framework.scaledagile.com/lean-governance?utm_source=chatgpt.com))
