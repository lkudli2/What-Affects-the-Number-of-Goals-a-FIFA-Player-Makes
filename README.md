## Project Title

**What Affects the Number of Goals a FIFA Player Makes?**
*STAT 425 – Case Study 2*
Authors: *Anav Vora & Lavanya Kudli*
Date : 5th Dec 2024

---

## Overview

This project analyzes FIFA World Cup (2018) and FIFA Women’s World Cup (2019) data to investigate the factors influencing the number of goals scored by players. The analysis uses both categorical (position, country, WorldCup/sex) and continuous (age, caps) predictors, with the primary response variable being the number of goals.

---

## Dataset

* **Response Variable:**

  * Goals scored (adjusted to `goals+1` for Box-Cox transformation).

* **Predictors:**

  * Continuous: `age_yrs`, `caps` (international appearances).
  * Categorical: `pos` (playing position), `country`, `WorldCup` (men’s vs women’s).

* **Data Preparation:**

  * Excluded players with missing goal values.
  * Visual exploration: scatter plots, boxplots, and distributions.
  * Observed skewness in `caps` and `goals`.

---

## Methodology

### 1. **Exploratory Data Analysis (EDA)**

* Compared goal distributions across positions, age, sex, and nationality.
* Observed trends:

  * Forwards (FW) scored the most goals.
  * Goals increase with age until \~37 years, then decline.
  * Higher goals with higher international appearances.
  * Women’s World Cup players scored more goals overall.
  * Certain countries (Canada, USA, Brazil) had standout performances.

### 2. **Model Fitting**

* Linear regression with interaction terms:

  * `Age × Position`
  * `Age × WorldCup`
  * `Age × Country`
  * `Caps × Position`
  * `Caps × Country`
* No interaction between `WorldCup × Caps` (ruled out).

### 3. **Model Diagnostics**

* Issues found: non-constant variance, non-normality.
* Detected: 28 high-leverage points, 9 outliers, 1 influential point.

### 4. **Transformation**

* Applied Box-Cox transformation (optimal λ ≈ -0.1).
* Adjusted response variable: `goals + 1`.
* Post-transformation:

  * Variance and normality assumptions satisfied.
  * Reduced leverage points (notably Ronaldo, Sinclair, Lloyd).

### 5. **Model Selection**

* Used sequential ANOVA.
* Significant predictors: `pos`, `country`, `age_yrs`, `caps`.
* WorldCup retained due to significant interactions.
* All interaction terms significant.

---

## Statistical Tests Summary Table

| **Test** / **Step**                                                                   | **Purpose**                                                                          | **Key Result**                                                                                                                    |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| **Normality check** (EDA + residual plots)                                            | Test if data/residuals follow normal distribution (assumption of linear regression). | Violations detected; skewness in `caps` and `goals`.                                                                              |
| **Variance check** (constant variance assumption)                                     | Ensure homoscedasticity of residuals.                                                | Non-constant variance observed → Box-Cox applied.                                                                                 |
| **High leverage / outlier / influence diagnostics** (Cook’s distance, leverage plots) | Identify extreme points affecting model fit.                                         | 28 high leverage points, 9 outliers, 1 influential point before transformation; only 3 leverage points after transformation.      |
| **Box-Cox transformation**                                                            | Fix violations of normality/variance.                                                | Optimal λ = -0.12 (rounded to -0.1); improved residual behavior.                                                                  |
| **Sequential ANOVA**                                                                  | Determine significance of predictors and interactions.                               | All interaction terms significant; `pos`, `country`, `age_yrs`, `caps` significant; `WorldCup` retained due to hierarchical rule. |

---

## Key Findings

1. **Position** strongly influences goals (FW > MF > DF > GK).
2. **Age** generally increases goals scored, but effect depends on position, sex, and nationality.
3. **Experience (caps)** is positively correlated with goals, especially at high international appearances.
4. **Sex (WorldCup)** alone not significant, but modifies the effect of age on goals.
5. **Country** influences outcomes due to different training resources and fitness standards.

---

## Conclusion

A player’s **position, age, experience, nationality, and sex** all influence scoring ability. Stakeholders (coaches, analysts, scouts) may use these findings to evaluate and forecast player performance.

---

## File Contents

* **Executive Summary.pdf**: Contains introduction, data exploration, methodology, results, and conclusions.

---

