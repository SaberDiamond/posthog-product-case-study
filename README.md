# Budget Guard

**🥈 2nd Place | PMC × PostHog Product Case Competition, UC Santa Cruz (November 2026)**  
**Product management case study · Financial analysis · Interactive prototype**

> **Student competition concept.** Budget Guard is a proposed feature, not an official PostHog product. The competition case, customer stories, and financial data are simulated. The demo uses illustrative prices and synthetic usage data.

## Overview

In the PMC × PostHog Product Case Competition, our team was asked to recommend **one product feature** for a fictional **$3 million investment budget**. We evaluated three proposals, questioned the financial assumptions behind them, built an interactive demo, and defended our recommendation in a five-minute pitch.

Our team placed **second** with **Budget Guard**, a feature concept designed to make usage-based billing more predictable while helping customers preserve useful analytics data.

## The problem

In the case's simulated customer data, **2,480 teams** reached a free usage limit during one quarter, but **1,488 (60%)** did not add a payment card. In a separate survey, **41% of respondents** who had not converted identified unpredictable bills as their primary obstacle.

One interview described **Leo**, a founder who paused session recordings to avoid unexpected charges. When a customer later reported a bug, the missing recording made troubleshooting harder.

**Product insight:** Customers can see the value of analytics and still hesitate to pay if they cannot predict the cost.

*Source: Competition packet, Tables D1–D2 and interview E3. These are simulated case figures, not PostHog operating results.*

## Our solution: Budget Guard

Budget Guard combines four ideas into one customer experience:

1. **Usage forecast:** Estimate next month's spend as a range, not a promise.
2. **Monthly spending cap:** Let a customer choose a hard limit they feel comfortable with.
3. **Priority-aware sampling:** As usage approaches the cap, reduce lower-priority recordings before critical workflows, while acknowledging that sampling can still miss data.
4. **Transparent activity:** Show what was sampled or omitted and why.

The prototype follows Leo's journey from a paused recording account to a forecast, a **$50 cap**, and a simulated bot-traffic spike. Under the demo's assumptions, an uncapped bill reaches **$1,521**, while Budget Guard ends at **$40** and retains the highlighted checkout recording. **These outcomes are simulated, not real product performance.**

## Why we chose it

We compared Budget Guard with **Preflight** (predictive checks for AI-generated code changes) and **Crew** (a workspace for non-engineering teams).

- **Customer need:** Billing uncertainty was supported by both funnel behavior and a specific customer interview in the case.
- **Feasibility:** Finance estimated a **90% chance of passing the pilot** and a **three-month build** for Budget Guard.
- **Economics:** Finance's original simplified expected value was approximately **$3.02M**. We modeled a potential reduction in spending among existing paying customers and revised this to approximately **$2.34M**.
- **Tradeoff:** Preflight has a larger modeled upside, but its adoption and technical validation assumptions are more uncertain.

Our adjustment assumes **20% of small paying teams spend 25% less** after setting caps. That is a **scenario we created**, not an observed result. The expected-value figures use the competition's simplified ARR-based calculation and should not be interpreted as accounting profit.

## How we would validate it

Our proposed first step was an **eight-week controlled pilot** showing a forecast and cap to teams that reach a free limit, before investing in more complex sampling.

- **Baseline:** 40% of teams at a free limit add a payment card (case data).
- **Proposed target:** Approximately 57%, derived from Finance's modeled two-year conversion goal.
- **Guardrails:** Measure net incremental revenue, spending reductions among existing customers, forecast accuracy, and loss of critical session data.

**The 57% figure is a target, not a measured outcome.**

## Interactive prototype

The demo is a **single-page HTML, CSS, and JavaScript prototype**, featuring an adjustable spending cap, a billing forecast, and an interactive traffic-spike simulation. No real payments are collected, and it is not connected to a PostHog account.

**Run locally:** Open `index.html` in a web browser.

**Live demo:** Add the GitHub Pages URL here after publishing.

## Presentation and materials

- **Final pitch deck:** `presentation/Budget_Guard_Final_Pitch.pdf` (add after exporting)
- **Decision analysis:** `analysis/Product_Decision.md` (optional deeper write-up)
- **Product screenshots:** `assets/` (add a forecast, cap, and simulation screenshot)

## Team and acknowledgment

This was a collaborative **two-person team** project. I helped bring the team together and guide our customer research, financial evaluation, product direction, and final pitch.

Thank you to **Tarun, the Product Management Club at UC Santa Cruz, and the competition judges** for organizing the opportunity and providing feedback.

---

*This repository documents an independent student competition submission. It is not affiliated with, endorsed by, or a release from PostHog. Original competition materials are not redistributed here.*
