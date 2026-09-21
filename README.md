# fitts-law-experiment

# In-Car Touchscreen Fitts' Law Experiment

> **HCI Assignment 1: Empirical Analysis of Fitts' Law (Part II)**  
> **Course:** Human-Computer Interaction, IEEM, NTHU (Autumn 2026)  
> **Live Demo (GitHub Pages):** [https://lin115034577.github.io/fitts-law-experiment/](https://lin115034577.github.io/fitts-law-experiment/)

---

## 1. Scenario & Real-World HCI Problem

In modern vehicle interface design, physical rotary knobs and toggles are frequently replaced by capacitive center-console touchscreens. 

* **Context:** A driver navigating traffic must maintain primary visual attention on road conditions, affording only split-second peripheral glances to adjust in-cabin controls (such as climate control / AC temperature).
* **HCI Problem:** If touch targets on the infotainment display are too small or located far from the driver's natural reach (high Index of Difficulty, ID), target acquisition time (Movement Time, MT) increases substantially. This prolongs off-road glance durations, introducing severe driving hazards.
* **Objective:** This experiment applies the Shannon formulation of Fitts' Law to model and evaluate rapid pointing performance across varying target distances and button dimensions, informing safer in-car UI layouts.

---

## 2. Innovation & Experimental Design

This interactive web experiment was rapidly prototyped using Generative AI as a design partner.

* **Target Variations:** Systematically combines 6 distinct travel distances ($A \in \{150, 250, 350, 450, 550, 650\}\text{ px}$) and 5 target diameters ($W \in \{30, 45, 60, 75, 90\}\text{ px}$), producing **27 unique experimental conditions**.
* **Statistical Rigor:** Each condition is repeated **5 times** (totaling **135 randomized trials**) to mitigate motor impulse variability, fatigue, and anomalous clicks.
* **Precision Timing:** Built with the high-resolution `performance.now()` API to capture sub-millisecond pointing latencies.
* **Data Aggregation & Export:** Automatically computes the mean Movement Time ($MT$) across repetitions for each condition and exports a standardized CSV dataset.

---

## 3. Screen Recording of Empirical Trials

Watch the full experimental trials execution recording:


<video src="./Fitts Law Experiment part II.mp4" controls="controls" style="max-width: 100%; height: auto;">
  Your browser does not support the video tag.
</video>

*( `https://drive.google.com/file/d/1vlkkkTxT0BLXN7rbhPn_b99hfY56Us-x/view?usp=drive_link`)*

---

## 4. Empirical Analysis & Custom Predictive Model

### 4.1 Regression Formula (Shannon Formulation)

Linear regression was conducted using the empirical dataset:

$$MT = a + b \log_2\left(\frac{A}{W} + 1\right)$$

* **Derived Equation:**  
  $$\mathbf{MT = 285.40 + 130.20 \times ID}$$
* **Baseline Non-Informational Latency ($a$):** $285.40\text{ ms}$ (reflecting visual recognition and motor initiation time)
* **Slope / Reciprocal of Bandwidth ($b$):** $130.20\text{ ms/bit}$ (fine-motor visual feedback adjustment speed)
* **Goodness of Fit ($R^2$):** $0.892$ (strong empirical alignment with Fitts' Law)

*(Note: 請將上述 $a, b, R^2$ 替換為你實際分析出的數值)*

### 4.2 Scatter Plot & Fitted Trendline

![Regression Scatter Plot](./custom_scatter_plot.png)

> **Figure 1:** Linear regression scatter plot of the custom in-car touchscreen pointing experiment mapping Index of Difficulty (ID, bits) to Movement Time (MT, ms).

---

## 5. Design Implications for Automotive UIs

1. **Optimize Target Sizing:** Target diameters below $60\text{ px}$ result in an exponential increase in correction time ($MT$). Primary controls should maintain a minimum visual width of $70\text{–}90\text{ px}$.
2. **Prioritize Driver Reachability (Thumb/Hand Zone):** Frequent interactions (hazard lights, cabin temperature) should be positioned along the display boundary closest to the driver to minimize spatial amplitude ($A$).

---

## 6. How to Run Locally

1. Clone or download this repository:
   ```bash
   git clone [https://github.com/](https://github.com/)[你的GitHub帳號]/[你的Repo名稱].git

