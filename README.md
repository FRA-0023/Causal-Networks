# Applied Causal Inference & Structural Causal Models: Beyond Passive Correlation

[![Language](https://img.shields.io/badge/Language-Python%203.10+-3776AB?style=flat&logo=python)](https://www.python.org/)
[![Frameworks](https://img.shields.io/badge/Frameworks-DoWhy%20%7C%20pgmpy-blue)](https://github.com/py-why/dowhy)
[![Methodology](https://img.shields.io/badge/Methodology-SCM%20%7C%20Potential%20Outcomes-orange)](#)
[![Case Study](https://img.shields.io/badge/Case%20Study-Viticulture%20Agronomic%20Interventions-green)](#)

> Machine learning predicts $P(Y \mid X)$. Strategic decisions require $P(Y \mid \text{do}(X))$. An applied framework across DAGs, do-calculus, Meta-Learners, and real-world counterfactual evaluation.

---

## 📌 Executive Summary

Most data science applications fail at decision-making because they optimize for passive statistical correlation. In observational data, intervening on a variable based solely on predictive correlation introduces expensive policy errors due to **confounders, colliders, and selection bias**.

This repository is an **applied causal inference framework** bridging theoretical econometrics with production Python code:
- Implements the foundational **Neyman-Rubin Potential Outcomes** and **Pearl's Structural Causal Models (SCMs)**.
- Deconstructs **graphical separation (d-separation)** to identify and block spurious non-causal paths.
- Compares advanced **Meta-Learners (S/T/X-Learners)** to estimate Conditional Average Treatment Effects (CATE).
- Applies counterfactual structural modeling to a real-world biological system: evaluating canopy management interventions on *Vitis vinifera* L. cv. Sangiovese quality.

---

## 🔍 The Causal Inference Architecture

The repository is structured into modular, interactive research notebooks progressing from foundational theory to empirical counterfactual estimation:

```
Applied-Causal-Inference/notebooks/
├── 01_potential_outcomes_economic.ipynb   # Rubin Causal Model: ATE, ATT, SUTVA & Selection Bias
├── 02_inference_with_pgmpy.ipynb          # Bayesian Networks: Conditional Independence & Belief Propagation
├── 03_d_separation.ipynb                  # Graphical Criteria: Chains, Forks, Colliders & M-Bias
├── 04_causal_inference_with_dowhy.ipynb   # The 4-Step DoWhy Pipeline: Model, Identify, Estimate, Refute
├── 05_metalearners.ipynb                  # Heterogeneous Treatment Effects: S-Learner, T-Learner, X-Learner
├── 06_Structural_causal_models.ipynb      # Pearl's do-calculus: Abduction, Action, and Counterfactual Queries
├── 07_scm_matrix_form.ipynb              # Linear SCMs: Covariance Decomposition & Path Coefficients
└── sangiovese.ipynb                       # Empirical Case Study: Viticulture Counterfactual Intervention
```

---

## 📐 Core Methodological Modules

### 1. The Identification-Estimation Decoupling (`04_causal_inference_with_dowhy.ipynb`)
Following Judea Pearl and Microsoft Research's DoWhy protocol, causal queries are strictly separated into 4 distinct phases:
1. **Model:** Encode assumptions explicitly into a Directed Acyclic Graph (DAG).
2. **Identify:** Prove mathematical identifiability using Backdoor, Frontdoor, or Instrumental Variable criteria.
3. **Estimate:** Fit propensity score matching, regression discontinuity, or IPW estimators.
4. **Refute:** Stress-test the effect using placebo treatments, random unobserved confounders, and subset validation.

### 2. Heterogeneous Treatment Effects via Meta-Learners (`05_metalearners.ipynb`)
Moving beyond population-average ATE to person-specific CATE:
- **S-Learner (Single Model):** Models treatment as a feature; prone to regularizing away treatment effects in high dimensions.
- **T-Learner (Two Models):** Trains separate models for control and treatment groups; avoids treatment attenuation.
- **X-Learner (Cross-Learner):** Optimized for extreme treatment imbalance ($N_1 \ll N_0$), computing imputed counterfactual residuals to maximize sample efficiency.

### 3. Empirical Case Study: Viticulture Counterfactuals (`sangiovese.ipynb`)
- **Domain:** Precision viticulture and enological optimization (referencing Magrini, Di Blasi & Stefanini, *Biometrical Letters*).
- **Objective:** Quantify how agronomic canopy interventions (**bud load**, **defoliation**, **cluster thinning**) and **harvest timing** causally alter must sugar concentration, total acidity, and anthocyanin profiles.
- **Mechanism:** Disentangles seasonal climatic confounders from direct human agronomic interventions to guide optimal vineyard yield management.

---

## 🛠️ Stack & Dependencies

- **Language:** Python 3.10+
- **Causal Engines:** `dowhy` (causal graph identification & refutation), `pgmpy` (Bayesian networks), `econml` / `scikit-learn` (meta-learners)
- **Data & Visualization:** `networkx`, `matplotlib`, `seaborn`, `pandas`, `numpy`

### Quick Start
```bash
# Clone repository
git clone https://github.com/FRA-0023/Applied-Causal-Inference.git
cd Applied-Causal-Inference

# Install requirements
pip install dowhy pgmpy networkx scikit-learn pandas matplotlib
```

---

**Author:** Francesco Colombini  
[GitHub Profile](https://github.com/FRA-0023) · [LinkedIn](https://www.linkedin.com/in/francescocolombini/)