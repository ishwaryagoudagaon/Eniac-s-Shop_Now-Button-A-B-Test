# Eniac A/B Testing Analysis: Optimizing Click-Through Rate

## Overview

This project presents the analysis of an A/B test conducted for **Eniac**, a tech e-commerce company aiming to improve the **Click-Through Rate (CTR)** of its homepage call-to-action button.

Four button variants were tested to determine whether changes in button colour and wording could increase user engagement:

- White “SHOP NOW”
- Red “SHOP NOW”
- White “SEE DEALS”
- Red “SEE DEALS”

The analysis uses CTR as the primary success metric and applies chi-squared statistical testing to determine whether the observed differences are statistically significant.

---

## 🎯 Objective

Determine whether any of the four homepage button designs improves user engagement, measured by CTR.

The analysis also provides a basis for considering additional business metrics such as:

- Drop-off rate on the linked page
- Homepage-return rate after clicking the button

The broader business objective is to identify a call-to-action design that encourages more visitors to explore Eniac’s products without negatively affecting the subsequent user journey.

---

## 📁 Files Included

- `eniac_Button_A_B_Testing.ipynb` – Python notebook containing:
  - Data loading
  - CTR calculation
  - Results interpretation
- `Eniac_AB_Testing_Presentation.ppt`
- Data:
  - `eniac_A.csv`
  - `eniac_B.csv`
  - `eniac_C.csv`
  - `eniac_D.csv`
- `requirements.txt` – Python environment setup
- `.gitignore` – Files excluded from version control
- `LICENSE` – Project license

---

## 🧪 Experiment Setup

### 🧱 Variants Tested

| Version | Description |
| ------- | ----------- |
| A | Original white “SHOP NOW” |
| B | Red “SHOP NOW” |
| C | White “SEE DEALS” |
| D | Red “SEE DEALS” |

### 📊 Metrics

#### Primary metric

**Click-Through Rate (CTR)**
\[
CTR = \frac{\text{Button Clicks}}{\text{Total Homepage Visits}}
\]

CTR was selected as the main success metric because the experiment was designed to increase interaction with the homepage call-to-action.

#### Additional metrics

- **Drop-off rate:** The percentage of users who start a conversion process but do not complete it.
- **Homepage-return rate:** The percentage of users who return to the homepage after clicking the button.

These additional metrics can help determine whether a higher CTR also leads to better user engagement after the initial click.

---

## 📊 Statistical Methodology

### 1. CTR Calculation

For each version, the number of clicks and non-clicks was identified. CTR was then calculated by dividing clicks by total visits.

### 2. Chi-Squared Test for Independence

A chi-squared test was used to evaluate whether CTR differed across the four button versions.

The hypotheses were:

- **Null hypothesis \(H_0\):** All four versions have the same CTR.
- **Alternative hypothesis \(H_1\):** At least one version has a different CTR.

The significance level was set to:

\[
\alpha = 0.05
\]

This corresponds to a 95% confidence level.

Example Python code:

```python
from scipy.stats import chi2_contingency

chi2, p_value, degrees_of_freedom, expected = chi2_contingency(
    contingency_table,
    correction=False
)
```

### 3. Pairwise Post-Hoc Testing

After the overall chi-squared test, pairwise comparisons were conducted to identify which versions differed from each other.

Because six pairwise comparisons were made, p-values were adjusted using the **Holm correction** to reduce the risk of false-positive results.

---

## 📈 Results

Each version received approximately **1,500 homepage visits**.

| Version | Clicks | No-clicks | CTR |
| ------- | ------: | --------: | ---: |
| A | 134 | 1,366 | **8.93%** |
| B | 102 | 1,398 | **6.80%** |
| C | 78 | 1,422 | **5.20%** |
| D | 129 | 1,371 | **8.60%** |

### CTR comparison

- **Version A:** 8.93%
- **Version D:** 8.60%
- **Version B:** 6.80%
- **Version C:** 5.20%

Version **A** had the highest observed CTR, followed closely by Version **D**.

### Overall chi-squared test

The overall test produced:

```text
Chi-squared statistic: 19.72
p-value: approximately 0.000194
```

Since:

\[
p < 0.05
\]

the null hypothesis is rejected.

This indicates that the four versions do not all have the same CTR. There is statistically significant evidence that at least one version performs differently from the others.

### Pairwise comparison results

| Comparison | Holm-adjusted p-value | Statistically significant? |
| ---------- | --------------------: | -------------------------- |
| A vs B | 0.1200 | No |
| A vs C | 0.0004 | Yes |
| A vs D | 0.7469 | No |
| B vs C | 0.1933 | No |
| B vs D | 0.1933 | No |
| C vs D | 0.0012 | Yes |

The pairwise results show that:

- Version A performs significantly better than Version C.
- Version D performs significantly better than Version C.
- Version A and Version D are not statistically significantly different.
- Version B is not statistically significantly different from the other versions after correction.

---

## ✅ Final Decision

Version **A** achieved the highest observed CTR at **8.93%**, but Version **D** was very close at **8.60%**.

The statistical analysis does **not** provide enough evidence to conclude that Version A is definitively better than Version D. Therefore, the most accurate conclusion is:

> **Version A is the observed CTR leader, while Versions A and D are statistically comparable. Version C is the weakest-performing version based on CTR and performs significantly worse than both A and D.**

The overall test confirms that the four button versions do not perform equally. However, the results do not support declaring a unique winner across all four variants.

Before making a final production decision, the following steps are recommended:

1. Compare the drop-off rate for each version.
2. Compare the homepage-return rate for each version.
3. Check whether A or D leads to better downstream engagement.
4. If necessary, run a follow-up test comparing only A and D with a smaller minimum detectable effect.

---

## 🔍 Business Interpretation

The experiment provides value by identifying which button designs generate more initial engagement with the homepage call-to-action.

The findings suggest:

- The wording and colour combination influence CTR.
- The white “SHOP NOW” version had the highest observed CTR.
- The red “SEE DEALS” version performed almost as well.
- The white “SEE DEALS” version had the lowest CTR.
- A higher CTR should be evaluated together with downstream behaviour before rollout.

The recommended business approach is therefore to treat **A and D as the leading candidates**, while using drop-off and homepage-return rates to determine which version produces the most valuable user journey.

---

## 🧾 Summary

| Area | Finding |
| ---- | ------- |
| Highest observed CTR | Version A |
| Highest CTR | 8.93% |
| Closest alternative | Version D at 8.60% |
| Overall test | Statistically significant |
| Significant pairwise differences | A vs C and D vs C |
| Clear unique winner | Not established |
| Weakest-performing version | Version C |
| Recommended next step | Compare A and D using downstream metrics |

