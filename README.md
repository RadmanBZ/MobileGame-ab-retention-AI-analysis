# 📊 Cookie Cats A/B Test: Gate Placement Optimization Analysis

## 🎯 Executive Summary

This project analyzes the results of an A/B test conducted by King (the makers of Candy Crush) on the popular mobile game **Cookie Cats**. The objective was to determine the optimal placement of the first "gate" (a friction point requiring player wait time or in-app purchase) by comparing its impact on player retention and engagement when placed at **Level 30 (Control)** vs. **Level 40 (Treatment)**.

The analysis employed advanced statistical techniques, including **Chi-Square Testing** and **Bootstrapping**, to draw robust conclusions.

| Metric | Gate 30 (Control) | Gate 40 (Treatment) | Statistical Finding | Business Recommendation |
| :--- | :--- | :--- | :--- | :--- |
| **7-Day Retention** | **Higher** | Lower | **Statistically Significant Decrease** (at $\alpha=0.05$) | **KEEP GATE @ LEVEL 30** |
| **Median Game Rounds** | $\approx$ Same | $\approx$ Same | **No Significant Difference** (CI includes 0) | The change did not drive more engagement. |

---

## 💡 Key Business Questions Addressed

This project directly addresses the core hypothesis related to the gate placement strategy:

1.  **Retention:** Does moving the gate to Level 40 significantly increase 7-day retention?
    * **Finding:** **No.** Moving the gate resulted in a **statistically significant drop** in 7-day retention.
2.  **Engagement:** Does moving the gate increase overall player activity (median game rounds)?
    * **Finding:** **No.** The change had **no measurable impact** on the median number of game rounds played, which remained close to zero difference.

---

## 🛠️ Project Methodology

The analysis was performed using Python and focused on rigorous statistical validation, moving beyond simple mean comparisons to address data skewness.

### 1. Data Preparation & EDA

* **Outlier Handling:** An extreme outlier (user with $\sim49,854$ game rounds) was identified and removed to ensure robust statistical results.
* **A/B Balance Check:** Verified near-perfect 50/50 user allocation, validating the test design.
* **Distribution Analysis:** Confirmed that the `sum_gamerounds` variable exhibits **extreme right-skewness**, justifying the use of median and bootstrapping.

### 2. Statistical Testing

| Metric | Test Used | Rationale |
| :--- | :--- | :--- |
| **Retention Rates** | **Chi-Square Test for Proportions** | Standard method for comparing two proportions (retained vs. not retained) across independent groups. |
| **Game Rounds** | **Bootstrapping** (for Median Difference) | Used to create a 95% **Empirical Confidence Interval** for the difference in medians, a non-parametric method robust to the data's highly skewed distribution. |

---

## 📈 Advanced Analytical Insights

### 1. Critical Churn Point Analysis

By isolating non-retained users, we identified where players drop off the most:

* **Primary Finding:** The highest churn consistently occurs at **Round 0 (Initial Install)**.
* **Business Impact:** The most significant bottleneck is the **initial user experience (Onboarding)**. Optimizing the first few minutes of the game will yield a higher retention return than optimizing the gate's location.

### 2. Comparative Engagement Distribution (KDE Plot)

* **Finding:** The **Kernel Density Estimate (KDE) plot** showed the engagement distributions for both Gate 30 and Gate 40 **completely overlap** across the first 100 rounds.
* **Business Impact:** This visual proof strongly confirms that the gate placement does not fundamentally alter the player's motivation to continue playing.

---

## ✅ Conclusion and Action Plan

### Final Decision:

The A/B test results are clear: Moving the gate to Level 40 introduced significant friction without providing any measurable increase in player activity.

> **Action:** **REVERT** to the Gate @ Level 30 version immediately to protect long-term retention and Customer Lifetime Value (LTV).

### Next Steps for Product Development:

1.  **Prioritize Onboarding:** Reroute development resources to improve the first 5 game rounds to address the Round 0 churn bottleneck.
2.  **Test Deeper Gates:** If the goal is monetization, future A/B tests should explore placing the gate much further into the game (e.g., Level 50 or 60) to avoid interrupting the initial habit-forming stage.

---

## ⚙️ Repository Structure and Setup

### Technologies Used

* Python (3.9+)
* **Pandas** for Data Manipulation
* **NumPy** for Numerical Operations (Bootstrapping)
* **Seaborn** & **Matplotlib** for Professional Visualization
* **SciPy** for Statistical Testing

### File Structure