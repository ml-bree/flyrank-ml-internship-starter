# User Intent Prediction for Search Ranking

## Abstract

This paper presents a machine learning approach to predicting user intent from search engagement signals. Using the FlyRank ML Internship dataset, I built a Random Forest classifier that predicts whether a page matches user intent based on CTR, engagement_rate, and position metrics. The model achieves 0.760 Precision@50, outperforming both the hand-rule baseline (0.680) and a single decision tree (0.740). The results are directional — they suggest that feature interactions capture user intent better than any single signal alone. This work provides a ranked action playbook for content teams to prioritize pages for refresh, rewrite, or protect.

---

## 1. Introduction

Search ranking systems need to understand what users actually want. A page that ranks high but doesn't match user intent leads to poor engagement and user frustration. The challenge is that user intent isn't directly observable — we can only see engagement signals.

This work addresses the question: **Can we predict whether a page matches user intent using search engagement signals?**

The decision this work supports is: **Which pages should be prioritized for content refresh based on predicted user intent?**

---

## 2. Data

**Dataset:** FlyRank ML Internship warehouse release (Hugging Face)

**Tables used:**
- `fact_content_daily_performance_sample` — daily search performance metrics
- `dim_content` — content metadata (creation date, type)

**Time window:** June 2026 (sample table)

**Exclusions:**
- Pages with less than 10 impressions (not enough signal)
- Pages with missing engagement data

**Public-safe note:** All data is pseudonymized. No client names, domains, URLs, or private queries are included.

---

## 3. Methodology

### 3.1 Task Type
Binary Classification — predict whether a page matches user intent (1) or not (0).

### 3.2 Features
| Feature | Description | Available At Decision Moment? |
|---------|-------------|------------------------------|
| `avg_position` | Average search position | Yes — historical GSC data |
| `ctr` | Click-through rate | Yes — historical clicks/impressions |
| `engagement_rate` | GA4 engaged sessions | Yes — historical GA4 data |
| `impressions_90d` | 90-day impressions | Yes — historical GSC data |

### 3.3 Label Definition (Proxy)
`high_intent = 1` if:
- `ctr > 0.05` AND `engagement_rate > 0.3`

This proxy assumes that high engagement (clicks + scrolls) indicates matched user intent.

### 3.4 Baseline
A hand-rule from Week 4:
- If `ctr < 0.02` AND `avg_position > 10` → flag for refresh
- Precision@50 = 0.680

### 3.5 Validation Design
- **Split:** 80/20 client-holdout
- **Stratification:** Balanced by target
- **Leakage prevention:** Features and label are from the same time window; no future data is used

### 3.6 Models
1. **Decision Tree** (max_depth=5) — interpretable baseline
2. **Random Forest** (n_estimators=100, max_depth=5) — ensemble improvement

---

## 4. Results

### 4.1 Model vs Baseline Comparison

| Model | Precision@50 | Improvement vs Baseline |
|-------|--------------|------------------------|
| Hand-Rule Baseline | 0.680 | — |
| Decision Tree | 0.740 | +8.8% |
| **Random Forest** | **0.760** | **+11.8%** |

### 4.2 Feature Importance (Random Forest)

1. **CTR** — most important predictor
2. **engagement_rate** — second most important
3. **avg_position** — third
4. **impressions_90d** — least important

**Interpretation:** CTR is the strongest signal, followed by engagement_rate. Position matters, but less than actual user engagement.

### 4.3 Error Analysis

**False Positives:** Pages flagged as high intent but not actually. This happens when engagement_rate is high but CTR is low.

**False Negatives:** Pages missed as high intent. This happens when CTR is high but engagement_rate is low.

**Key Insight:** No single feature is perfect — the combination matters.

---

## 5. Limitations & Honest Framing

**This is an observed, directional analysis, not a causal claim.**

1. **Proxy target:** I used engagement as a proxy for intent. A user can be engaged without the page matching their original intent.

2. **Sample bias:** The sample table is June 2026 only. Results may not generalize to other months.

3. **Feature limitations:** I only used four features. More features could improve the model.

4. **Client-holdout:** While this reduces leakage, it also reduces sample size.

**Caveat:** This work does not prove that improving user intent prediction causes better search ranking. It only shows that ML can identify patterns that correlate with engagement.

---

## 6. Ranked Recommendations

| Rank | Action | Reason Code | Signal |
|------|--------|-------------|--------|
| 1 | **Refresh** | `LOW_ENGAGEMENT` | High CTR + low engagement_rate |
| 2 | **Rewrite** | `LOW_CTR_HIGH_POSITION` | Low CTR + high avg_position |
| 3 | **Monitor** | `IMPROVING_ENGAGEMENT` | Engagement_rate is increasing |
| 4 | **Protect** | `HIGH_ENGAGEMENT` | High CTR + high engagement_rate |
| 5 | **Review** | `LOW_IMPRESSIONS` | Low impressions — not enough data |

---

## 7. Reproducibility

All code and notebooks are available in the GitHub repository:

**Repository:** https://github.com/ml-bree/flyrank-ml-internship-starter

**Key Notebooks:**
- **Data Contract:** `work/notebooks/w03_data_contract.ipynb`
- **Baseline:** `work/notebooks/w04_baseline_score.ipynb`
- **Model:** `work/notebooks/w05_model.ipynb`
- **Validation Audit:** `work/notebooks/w06_validation_audit.ipynb`
- **Action Playbook:** `work/notebooks/w07_action_playbook.ipynb`

### Running the Code
1. Clone the repo
2. Install requirements: `pip install -r requirements.txt`
3. Open the notebooks in Colab
4. Connect to Hugging Face with your READ token
5. Run the cells

---

## 8. Acknowledgments & Data Credit

This work was built on the FlyRank ML Internship dataset.

**Data credit:** Built on the FlyRank ML Internship dataset. Data provided by [FlyRank](https://flyrank.ai).

---

**Author:** Breattah Okeyo  
**Date:** August 2026  
**Track:** Machine Learning Internship  
**Lane:** User Intent / Refresh Opportunity Scoring
