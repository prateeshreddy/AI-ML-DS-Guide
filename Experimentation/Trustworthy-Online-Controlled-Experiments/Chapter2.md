# Chapter 2: Running & Analyzing Experiments
## Example Setup — “Coupon code at checkout for a Widget website”
- **Initial Hypothesis**: Users might abandon carts to search for codes leading to lesser conversions
- **Define metrics/OEC**: We could use revenue, but other factors typically affect revenue even if properly randomized. `revenue/user` is a more robust metric.
<p align="center">
<img width="370" height="457" alt="image" src="https://github.com/user-attachments/assets/eb5a8999-8508-4733-8259-066d7f94507c" />
</p>

- **Exposure**: Which users to consider in our OEC calculation? Not all users see checkout/our change -> analyze on the appropriate population. Thus, Only users who start checkout.
<p align="center">
<img width="459" height="428" alt="image" src="https://github.com/user-attachments/assets/a414dbfd-f4e8-4aba-bf6e-dc64185074fe" />
</p>

- **Variants**:
  - **Control**: Existing checkout page (no new coupon prompt).
  - **Treatment 1**: Checkout with coupon or gift code option below credit card information
  - **Treatment 2**: Checkout with coupon or gift code as a pop‑up.

## Establishing Statistical Significance
- To figure out if the difference between the control and treatment groups is statistically significant. If not, we **reject the initial hypothesis**
- Compute the **difference in means** +  **standard error (SE)** between Treatment and Control on the OEC.
- standard error (SE) can typically be **reduced** by **increasing the sample size**.
- Compute **p‑value = P(observing a difference between variants | H₀ is true)**
- Or you can also compute **95% confidence interval (CI)** for the lift.
  - For large samples, a two‑sided 95% CI is approximately `estimate ± 1.96 × SE`.

### Statistical Power & Practical significance
- **Power: P(reject H₀ when a true effect exists)** — typically **80–90%**.
- **Minimum Detectable Effect (MDE)**: Also called practical significance, which is the **smallest business‑meaningful lift worth shipping/maintaining**.
- Increasing **sample size** or **run time** increases power and allows a smaller MDE.

### Experiment Design Checklist
- **Randomization unit**: Usually **user**; consider session/page/geo only if interference is limited.
- **Sample size**: Plan for the MDE you care about (e.g., detect 1% lift with 80% power).
- **Run length**: Cover at least 4 days and **one full week** to control day‑of‑week effects; extend if novelty/learning effects are suspected.
- **Variants data split**: Control (34%) + Treatment1 (33%) + Treatment1 2 (33%)

### Interpreting the Results
- **Instrumentation**: The data collected on user interaction via logs.
- **Infrastructure**: This includes everything from experiment config to variant assignment.
- Results on OEC for our Example :

<p align="center">
<img width="579" height="240" alt="image" src="https://github.com/user-attachments/assets/4441b4d2-4e8a-4092-8e22-5acf0f9fa2c7" />
</p>

- **Guardrail checks**: These are our **sanity checks** which shouldn't change in any of the variant.
  - **Trust/quality checks** (e.g., crash rate)
  - **Organizational checks** (e.g., latency).
- **Interpretation for Statistical significance**:
  - Both treatment p-values are `< 0.05`, that means mean for control and any treatment are not same.
  - Exposing that both coupon box/pop‑up likely **decreased revenue**, so do **not launch**.

## Decision (Confidence Interval and Practical Significance)
Use the **estimated difference** (black box point) with **Confidence Interval** of the treatment effect against our predefined **Practical significance** (two dashed lines) and costs to decide:

<p align="center">
<img width="676" height="614" alt="image" src="https://github.com/user-attachments/assets/4e0177af-99f3-4047-bfc1-6bb88e5cf31c" />
</p>

1. **Not statistically significant**: CI contained within ± MDE → Implementing this treatment feature will likely yield neutral effect on OEC → iterate or abandon.
2. **Statistically and practically significant**: CI entirely beyond MDE in the desired direction → **Launch decision**.
3. **Statistically significant but not practically significant**: The effect of implementing this treatment feature is likely too small to justify costs → **Do not launch**.
4. **CI > MDE bounds**: Insufficient statistical power to draw a strong conclusion → **Iterate with more data, better precision**.
5. **Likely practical but not statistically significant**: There is a risk of no true lift in revenue if implememented → Iterate with **increase in power** and precision.
6. **Statistically significant and likely practically significant**: Because the lower CI bound is too low yet we do see lift → consider launch with caution but ideal decision is iterate with more power.

