# Eniac Webpage CTA A/B Test — Chi-Square Analysis

A statistical analysis of a 4-way A/B test conducted on Eniac's homepage to evaluate whether different call-to-action (CTA) button designs produced significantly different click-through rates (CTR).

The analysis uses a **chi-square test of independence**, followed by **pairwise post-hoc chi-square tests with a Bonferroni correction**.

---

## 📌 Project Overview

Eniac tested four different versions of its primary homepage CTA button.

The variants differed in:

- **Button copy:** `SHOP NOW` vs. `SEE DEALS`
- **Button color:** White vs. Red

The goal of this analysis is to determine whether the four variants have statistically different click-through rates and identify which variants differ from one another.

### Business Question

> **Does CTR differ significantly across the four homepage CTA variants?**

---

## 🧪 A/B Test Variants

| Version | Button Copy | Color |
|:------:|-------------|-------|
| A | SHOP NOW | White |
| B | SHOP NOW | Red |
| C | SEE DEALS | White |
| D | SEE DEALS | Red |

Each variant was shown to a separate group of visitors during a comparable approximately 14-day testing period.

---

## 📊 Dataset

The project contains four CSV files representing the four homepage variants:

```text
eniac-ab-test/
│
├── data/
│   ├── eniac_a.csv
│   ├── eniac_b.csv
│   ├── eniac_c.csv
│   └── eniac_d.csv
│
├── eniac_case_analysis.ipynb
│
└── README.md

---

## 🛠️ Tools & Libraries

This project was developed using Python and the following libraries:

| Tool / Library | Purpose |
|---|---|
| **Python 3.10+** | Programming language used for the analysis |
| **pandas** | Loading, cleaning, transforming, and analyzing CSV data |
| **NumPy** | Numerical operations |
| **SciPy** | Chi-square hypothesis testing |
| **Matplotlib** | Data visualization |
| **Jupyter Notebook** | Interactive analysis and documentation |
| **re** | Extracting visit and click information from text using regular expressions |
| **math** | Mathematical calculations used during the analysis |

### Python Imports

The main libraries used in the notebook are:

```python
import pandas as pd
import numpy as np

from scipy import stats
from scipy.stats import chi2_contingency

import math
import re
