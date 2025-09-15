
# Chapter 1: Introduction and Terminology
### Overall Evaluation Criterion (OEC)
- **What**: The single primary metric (dependent variable) we optimize for an experiment.
- **Short‑term measurable** within experiment duration but predictive of **long‑term value**.
- **Examples**: active days per user, revenue/user

### Parameters: 
- **What**: Controllable factors we change
- **Examples**: font color, button shape, placement

### Variants: 
- **What**: Groups to test user experience, typically created by assigning values to parameters
- In AB testing -> A & B are two variants
- Commonly **Control** (existing) vs **Treatment**(s); can be multivariate.

### Randomization Unit
- **Unit**: The entity that is randomized (usually **user**; sometimes session/page/users in a geography).
- **Assignment**: Hashing process maps each unit to a variant **independently** and **unbiased**.
  - Keep assignment **consistent** for the duration to avoid contamination.
  - Choose a unit that minimizes **interference** between units.
  - Experiments also reveal **unexpected side‑effects** (performance regressions, crash rate changes, cannibalization of clicks/features).

### Why correlations ≠ causality?
- Example: Office 365 users who **see more error messages/heavy crashes had a lower churn rate**.
- Does this mean we show more errors? No, the reason behind this was that these users spent **more time**

### Organizational Requirements
- Sufficient traffic & instrumentation to measure the OEC reliably.
- Clear **business strategy → OEC mapping**, OEC may evolve as the product matures. Example: Click-through rate (CTR) to Conversion rate based on the product/ product growth.
- Teams using a defined OEC make more consistent **data‑driven decisions**
- Expect that only a minority of ideas will move the primary metric.
- **Example**: Experiment team at Slack in 2019 mentioned only **30%** of their monetization experiments **showed positive results**, they threw away the rest 70%

## Two Product Scenarios (Hill‑Climbing vs. Bigger Hill)
### 1) You have a business strategy + product with enough users to experiment (local hill‑climbing)
- Can identify areas with high ROI i.e. that improve OEC  (**multi‑variant** experiments to find them quicker).
- **Strategic Integrity**: To have a strategy that actually improves OEC (choosing the right metrics), add crashes as a gaurdrail metric.

### 2) You have a business strategy + product, but results suggest a pivot (searching for a bigger hill)
- Any investments should have **portfolio of ideas**; most pivots (big jumps i.e. large redesigns) fail.
- For big redesigns:
  - Expect **higher risk** and potential **novelty/primacy** effects.
  - **Need bigger experiment duration** and probably more **number of experiments** that target specific tactic as a part of the strategy.



