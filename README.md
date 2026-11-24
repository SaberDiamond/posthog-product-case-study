# Budget Guard

**🥈 2nd Place | PMC × PostHog Product Case Competition | UC Santa Cruz, November 2026**  
Product strategy · Financial analysis · Interactive prototype

> **Independent student competition project.** Budget Guard is a proposed feature, not an official PostHog product. The competition's customer and financial data are simulated, and the prototype uses illustrative prices and usage scenarios.

## Overview

The PMC × PostHog case challenged participants to recommend **one feature for a hypothetical $3 million investment**. Our team evaluated three proposals, questioned their business assumptions, and presented **Budget Guard**, a concept for making usage-based billing easier to predict and control.

Our submission earned **second place**. Alongside the product recommendation, we created an interactive browser prototype and a financial analysis to explain why we prioritized Budget Guard over Preflight and Crew.

## Project files

| File | Contents |
|---|---|
| [`index.html`](index.html) | Interactive product prototype |
| [`Budget_Guard_Pitch_Deck.pdf`](Budget_Guard_Pitch_Deck.pdf) | Competition presentation and backup calculations |
| [`Product_Decision.md`](Product_Decision.md) | Customer evidence, financial reasoning, assumptions, and tradeoffs |

## The problem

PostHog's usage-based pricing can create uncertainty for teams moving beyond the free tier. In the competition's simulated case data:

- **2,480 teams** reached a free usage limit in one quarter; **1,488 (60%)** did not add a payment card (Table D1).
- **41% of 310 survey respondents** who had not converted cited fear of an unpredictable bill as their primary reason (Table D2). The survey had a 21% response rate.
- In interview E3, a founder named **Leo** stopped recording sessions rather than risk an unexpected charge. When a customer later reported a bug, he lacked the session replay needed to investigate it quickly.

**Our insight:** Customers may find the product valuable but hesitate to pay when they cannot confidently predict what it will cost.

## Proposed solution

Budget Guard would combine three capabilities:

1. **Cost forecasting:** Show an estimated bill and plausible range using recent usage, while explaining what the forecast cannot predict.
2. **Customer-defined spending cap:** Let teams set a hard monthly limit in dollars before enabling paid usage.
3. **Priority-aware sampling:** As spending approaches the cap, reduce lower-priority recordings while trying to retain sessions associated with errors and important workflows. Show what was excluded and acknowledge that some useful data may still be missed.

The difference from a basic billing limit is **helping customers choose a cap and manage the data tradeoff**, not simply stopping collection when a limit is reached.

## Interactive prototype

The five-screen HTML prototype follows Leo's journey: lost session replay, cost forecast, cap setup, traffic-spike simulation, and an internal growth view.

In its **illustrative bot-traffic simulation**, the uncapped bill reaches **$1,521**, while Budget Guard finishes at **$40 under a $50 cap** and retains the featured checkout session. These are modeled demo outcomes, **not real PostHog performance or guaranteed savings**.

**[View demo source](index.html)** · To run it, open `index.html` in a browser. The same file can be hosted as the homepage with GitHub Pages.

## Why Budget Guard?

- **Customer evidence:** A measurable free-limit conversion gap, survey responses, and a specific interview describing lost debugging visibility.
- **Feasibility:** The case estimated a three-month time to launch and a **90% probability of passing a pilot** for Budget Guard (Tables B1 and C1).
- **Business case:** Finance's simplified expected value was **$3.015M**. We modeled potential reduced spending from existing paying customers, bringing our illustrative estimate to **$2.34M**.
- **Tradeoff:** Preflight had greater modeled upside, but depended on less certain adoption and technical validation. Crew addressed a genuine workflow problem, but adding users does not directly increase revenue when pricing is usage-based.

Our financial adjustments are **assumptions used for sensitivity analysis**, not observed outcomes. The case's expected-value formula combines added annual recurring revenue at a future point with one-time costs; it is not an accounting profit forecast.

## Proposed validation

Before building the more complex sampling capability, we proposed an **eight-week controlled pilot** of forecasts and spending caps for teams reaching a free limit.

- **Primary metric:** Free-limit-to-card conversion, from a **40% case baseline** toward an approximately **57% modeled target**.
- **Business guardrails:** Incremental paid usage and revenue, including potential spending reductions among existing customers.
- **Product guardrails:** Forecast accuracy and, in a later sampling pilot, the share of important recordings missed.

The 57% figure is a **target derived from assumptions**, not a conversion rate achieved by this project.

## Acknowledgments

Thanks to the **Product Management Club at UC Santa Cruz**, the organizers, and the judges for hosting the competition and providing feedback.

*This project is an independent student case submission. It is not affiliated with or endorsed by PostHog. The original competition packet is not redistributed in this repository.*

## Contributors

This project was developed for the PMC × PostHog Product Case
Competition at UC Santa Cruz (2026).

- **Dhanush Rao**
  - GitHub: [@Dhanushraj M Rao](https://github.com/saberdiamond)
  - LinkedIn: [Dhanushraj M Rao](https://linkedin.com/in/dhanushrao1/)

- **Dinesh Mandapalli**
  - GitHub: [@Dinesh Mandapalli](https://github.com/dineshrishim)
  - LinkedIn: [Dinesh Mandapalli](https://www.linkedin.com/in/dineshmandapalli11/)
