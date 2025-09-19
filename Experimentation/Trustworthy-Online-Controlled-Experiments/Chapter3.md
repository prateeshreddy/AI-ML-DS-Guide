# Chapter 3: Twyman’s Law & experimentation trustworthiness

> " **Any figure or graph that looks interesting/ different is usually wrong** "

> Twyman’s Law, By A.S.C Ehrenberg (1975)

- Experience tells us that many extreme results either positive or negative to KPIs are likely an error in instrumentation. Example: logging data, computation error, loss of data (duplication)

- To increate trust in software world we add tests using `assert()`. Similarly in experimentation, we can run **tests** like
    - Having same user in both variants is a red flag
    - If experimentation split is 50% between vairants. Then large deviations from 50% are red flags

## Common errors and how to improve trustworthiness of controlled experiments

### **Lack of Statistical Power**: 
- Typically, $H_0$ = No difference in a metric for Control and Treatment groups. We reject $H_0$ if data presents strong evidence against it. 
- But what if **experiment is underpowered to detect the effect size** in treatment group? Thus, setting practical significance is important and gather enough data to detect that change

### **Misinterpreting p-values**: 
>p-value = Probability (Difference in a metric is $0$ $±$ MDE $/$ $H_0$ is true)

- Debunk popular p-value misconceptions:
    1. If p-value = 0.05 doesn't mean 5% chance of $H_0$ being true. P-value is already calculated assuming $H_0$ is true
    2. No statistical significance (p-value > 0.05) always doesn't me

(to be continued..)
