# Product Decision: Why We Chose Budget Guard

**🥈 2nd Place | PMC × PostHog Product Case Competition | UC Santa Cruz, November 2026**

**Decision:** Recommend **Budget Guard** for the case's hypothetical 2027 product investment, ahead of **Preflight** and **Crew**.

> **Scope:** This document records the reasoning behind our competition submission. The three proposals, customer interviews, business figures, and $3M investment decision are part of a simulated case. Our revised estimates are scenarios, not actual PostHog revenue, product results, or company plans.

## 1. The investment choice

The case asked us to select one feature within a hypothetical $3M investment budget.

| Proposal | Customer problem | Build + conditional launch cost | Proposed time to launch |
|---|---|---:|---:|
| **Preflight** | Engineers need confidence in AI-generated changes before merging them | $3.0M | 9 months |
| **Crew** | Non-engineering teams need more independence with product data and experiments | $2.8M | 6 months |
| **Budget Guard** | Teams at usage limits need predictable costs without abruptly losing useful analytics data | $1.2M | 3 months |

*Case sources: Table B1 and Table C1. Launch costs are incurred only if a pilot passes.*

We evaluated **customer evidence, business value, feasibility, and risk**, rather than choosing only the feature with the highest headline payoff.

## 2. What changed our minds

Our initial preference was **Preflight**. It aligned with the case's direction toward AI-assisted software improvement, and a system that helps engineers assess AI-written code could strengthen trust in that workflow.

After examining the adoption assumptions and customer data, we shifted to **Budget Guard**. The problem was already visible: teams were reaching free usage limits but not converting to paid usage. The proposed solution also required less investment and carried a higher estimated pilot pass probability.

Our product thesis was:

> **Make PostHog valuable enough to pay for, and predictable enough to trust.**

This was a **prioritization choice under uncertainty**, not a claim that Budget Guard would produce guaranteed revenue.

## 3. Customer evidence

### A measurable conversion gap

The case's new-team funnel showed:

| Teams reaching a free limit | Added a card | Did not add a card |
|---:|---:|---:|
| 2,480 | 992 (40%) | 1,488 (60%) |

Another **6,000 teams from earlier quarters** remained at a free limit (*Table D1*).

Of the **310 non-converters surveyed**, **41%** said they feared an unpredictable bill and **14%** needed another person's approval (*Table D2*). Only **21%** of the 1,488 non-converters responded, so those percentages cannot safely be generalized to the entire population. Approval concerns are also not necessarily solved by a better billing forecast.

### The practical cost of uncertainty

In the fictional interview E3, **Leo**, a solo founder, had previously experienced an unexpected charge from another service. After reaching PostHog's free recording limit, he chose not to add a card. He knew a billing limit setting existed, but did not know what amount to enter or how much more recording would cost. When a customer reported a checkout issue while recordings were off, he spent two days reproducing the problem without a replay (*E3.1–E3.5*).

**Interpretation:** The problem was not simply price. The uncertainty surrounding price could cause customers to stop collecting data they valued.

## 4. Product concept and prototype

We proposed a billing experience with four connected elements:

1. **A forecast before payment:** Show a likely monthly charge and range, with clear limitations for traffic spikes, launches, or tracking changes.
2. **A hard dollar cap:** Let customers select the maximum monthly usage charge they are prepared to pay.
3. **Priority-aware sampling:** As usage approaches the cap, sample routine sessions more heavily while prioritizing errors, checkout, and other important workflows.
4. **Transparent tradeoffs:** Explain what is retained, what may be missed, and when recording must stop to respect the cap.

The case already described a billing-limit setting (*E3.3*). Our proposed differentiation was **cost guidance plus managed data collection**, rather than a spending cap alone.

We demonstrated the concept in [`index.html`](index.html), a browser-based prototype with five screens: Leo's problem, forecast, cap settings, traffic-spike simulation, and internal growth review.

**Simulated demo result:** A modeled bot-traffic incident produces an uncapped bill of **$1,521**, compared with **$40** under a **$50 Budget Guard cap**, while retaining the featured checkout recording. All pricing and behavior are illustrative. A real sampling system can misclassify traffic, lose useful sessions, or reach a hard limit that stops recording. The demo does not establish real-world accuracy.

## 5. Financial evaluation

### Original expected values

The competition defines a simplified expected-value calculation:

```text
EV = P(pilot passes) × [P(hit | launched) × added ARR if hit
                        + P(miss | launched) × added ARR if miss
                        − launch cost]
     − build cost
```

The ARR figures represent **additional annual recurring revenue measured two years after launch**. This case-specific measure combines a future revenue run rate with one-time costs. It is **not a net present value or accounting profit calculation**.

| Feature | Finance's EV | Pilot pass probability | Probability of both passing pilot and hitting target |
|---|---:|---:|---:|
| Preflight | $3.690M | 35% | 21% |
| Crew | $2.320M | 60% | 30% |
| Budget Guard | $3.015M | 90% | 63% |

*Case source: Table C1. The final column multiplies pilot success probability by the conditional chance of hitting the revenue target.*

### Preflight: adoption sensitivity

Finance's **$30M added-ARR** target requires **3,000 teams** to spend **$10,000 more per year**. The case reported **2,250 paying teams** with Self-Driving enabled, including **900 small teams** averaging approximately **$1,430 in total annual PostHog spending** (*Tables C1, D3, D5*).

We presented two illustrative stress tests:

- **2,250 adopters at +$10K each:** Hit-case ARR falls to **$22.5M** and EV to approximately **$2.12M**.
- **Constrain additional spend among small teams:** At +$10K for 1,350 mid-size/large teams and approximately +$1,430 for 900 small teams, hit-case ARR becomes about **$14.8M** and EV about **$0.50M**.

These are **not ceilings or measured forecasts**. The eligible customer base could grow, and a team's current annual spend is not a hard limit on future spending. The scenarios show how heavily Preflight's financial case depends on adoption and monetization, while its simulated-user predictions also need technical validation.

### Crew: monetization sensitivity

Non-engineers account for **38% of weekly active users** but only **8% of experiments created** (*Table D4*). That supports a genuine self-service opportunity. However, PostHog charges based on **usage, not seats**. Increasing the number of users does not itself produce incremental revenue.

For our presentation, we **halved Crew's assumed $14M hit payoff to $7M** as an illustrative downside scenario. This changed its EV from **$2.32M to $0.22M**. The 50% adjustment was **our assumption**, not a conclusion proven by the case data; additional product usage or retention could still make Crew valuable.

### Budget Guard: accounting for lower spend by existing customers

Finance's base-case calculation was:

```text
EV = 0.90 × (0.70 × $6M + 0.30 × $1.5M − $0.3M) − $0.9M
   = $3.015M
```

We identified an omitted downside: **paying customers might use spending caps to lower their bills**. Using the **$15M ARR from small paying teams** in Table D3, we modeled **20% of those teams spending 25% less**:

```text
Potential annual reduction = $15M × 20% × 25% = $0.75M
Revised EV = $3.015M − (90% × $0.75M) = $2.34M
```

The **20% and 25% figures are our own sensitivity assumptions**, not observed customer behavior. We applied the revenue reduction only when the pilot passed and the product launched.

| Feature | Finance's EV | Our illustrative scenario |
|---|---:|---:|
| **Budget Guard** | $3.015M | **$2.34M** |
| Preflight | $3.690M | $0.50M to $2.12M |
| Crew | $2.320M | $0.22M |

This comparison informed our decision, but **the revised scenarios use different assumptions and do not prove Budget Guard must outperform the alternatives**.

## 6. Conversion hypothesis and pilot

Finance's Budget Guard hit case assumes **5,000 new paying teams at approximately $1,200 annual spend each** (*Table C1*). We examined a possible non-converting pool:

```text
6,000 previously stuck teams + (1,488 per quarter × 8 quarters)
= 17,904 potentially non-converting teams

5,000 / 17,904 ≈ 28% of that pool
Illustrative overall card-add target ≈ 40% + (60% × 28%) ≈ 57%
```

This projection assumes that quarterly cohorts are **distinct, remain reachable, and behave similarly over two years**. Those conditions were not established by the packet, and adding a card does not guarantee $1,200 of annual paid usage.

We proposed an **eight-week controlled pilot** for teams reaching a free limit:

- **Test first:** Forecast plus selectable hard cap, before building complex sampling.
- **Primary metric:** Share of eligible teams who add a card, compared with the case's **40% baseline**.
- **Target:** Progress toward the illustrative **57%** conversion rate.
- **Stop threshold used in the pitch:** Below approximately **44%**, corresponding to our interpretation of Finance's lower-conversion case. A real launch decision would require uncertainty and revenue analysis rather than a threshold alone.
- **Business guardrails:** Actual incremental paid usage and net revenue, plus any reduced spend among existing paying customers.
- **Product guardrails:** Forecast calibration and, when sampling is later piloted, the share of important sessions that are missed.

**Core hypothesis:** More predictable billing can convert some hesitant free users into paying customers without creating offsetting revenue losses.

## 7. Tradeoffs and next steps

Choosing Budget Guard meant postponing, not dismissing, Preflight's larger strategic opportunity. We proposed **backtesting Preflight against historical AI-generated pull requests and observed rollbacks** before committing to its costlier development. The case also identified Crew's self-service opportunity, but its monetization assumptions needed more validation.

Our investment sequence was therefore **Budget Guard first, Preflight considered later if its technical evidence improves**. Budget Guard does not resolve Preflight's simulation risk, nor does one feature technically depend on the other.

## 8. Competition outcome

Our team presented the product recommendation, financial sensitivity analysis, and interactive prototype at the **PMC × PostHog Product Case Competition at UC Santa Cruz**, earning **second place**.

The central lesson was that **a useful or popular feature still needs a credible path to business value**. We aimed to make that path testable rather than present modeled revenue as guaranteed.

---

### Sources and attribution

- **Primary case:** *PostHog's Next Feature*, PMC@UCSC Product Case Competition, Fall 2026. Referenced sections include Tables B1, C1, D1–D5 and interview E3. The original case packet is not redistributed here.
- **Competition pitch:** [`Budget_Guard_Pitch_Deck.pdf`](Budget_Guard_Pitch_Deck.pdf)
- **Interactive prototype:** [`index.html`](index.html)
- **Status:** Independent student competition concept, not an official PostHog product or endorsed implementation. AI-assisted tools supported development of the prototype and presentation materials.
