# Product Analyst: A/B Testing Experiment

## Project Goal
This project simulates a real-world Product Analyst scenario: evaluating the success of a new website feature using an A/B test. The goal is to generate simulated user data, perform statistical analysis (Two-Proportion Z-Test), and deliver a data-driven business recommendation.

## Key Insights & Recommendation
* **Statistical Significance:** The test yielded a P-value of `< 0.05` (actual value generated dynamically in the script), indicating that the results are statistically significant.
* **Performance:** The Treatment group (new feature) achieved a ~12% conversion rate, outperforming the Control group's ~10% conversion rate.
* **Business Decision:** **Launch the feature.** The data proves with over 95% confidence that the new feature positively impacts user conversion rates.

## Project Overview
Instead of using a pre-cleaned dataset, this project builds the entire testing pipeline from scratch. It simulates 10,000 website visitors, assigns them to Control and Treatment groups, and tracks their conversions. It then uses the `statsmodels` library to mathematically prove if the difference in conversion rates is due to the new feature or just random chance.

---

## Technical Pipeline

### 1. Data Generation (Simulation)
Using `numpy` and `pandas`, a dataset of 10,000 unique users was generated.
* **Control Group:** Received the standard website experience (simulated ~10% conversion).
* **Treatment Group:** Received the new feature (simulated ~12% conversion).
* Users were split evenly (50/50) using random binomial distribution to mimic a live production environment.

### 2. Exploratory Data Analysis (EDA)
Calculated the raw conversion rates and total conversions for both groups using optimized pandas aggregations (`.agg()`) to quickly summarize user behavior.

### 3. Statistical Testing (Z-Test)
Applied a **Two-Proportion Z-Test** using `statsmodels.api`.
* Extracted total observations and total successes (conversions) for both groups.
* Calculated the Z-Score and P-Value to test the null hypothesis (that there is no difference between the two versions).

### 4. Visualization & Automated Reporting
* Utilized `seaborn` and `matplotlib` to create a clean, executive-friendly bar chart displaying the conversion rates with data labels.
* Built a dynamic string-formatting script that automatically outputs a formal business recommendation based on whether the generated P-Value falls below the standard 0.05 alpha threshold.

---

### How to Run the Code

1. **Clone this repository** to your local machine.
2. **Install dependencies:** Ensure you have Python 3.x installed. You will need the following libraries:
   ```bash
   pip install numpy pandas statsmodels matplotlib seaborn
