# User Intent Prediction for Search Ranking

## Abstract

This paper presents a machine learning approach to predicting user intent from search engagement signals. Using the FlyRank ML Internship dataset, I built a Random Forest classifier that predicts whether a page matches user intent based on CTR, engagement_rate, and position metrics. The model achieves 0.760 Precision@50, outperforming both the hand-rule baseline (0.680 Precision@50) and a single decision tree (0.740 Precision@50). The results are directional — they suggest that feature interactions (CTR + engagement_rate + position) capture user intent better than any single signal alone.

## Introduction / Problem Statement

Search ranking systems need to understand what users actually want. A page that ranks high but doesn't match user intent leads to poor engagement and user frustration. The challenge is that user intent isn't directly observable — we can only see engagement signals.

This work addresses the question: **Can we predict whether a page matches user intent using search engagement signals?**

The decision this work supports is: **Which pages should be prioritized for content refresh based on predicted user intent?**

## Data

**Dataset:** FlyRank ML Internship warehouse release (Hugging Face)

**Tables used:**
- `fact_content_daily_performance_sample` — daily search performance metrics
- `dim_content` — content metadata (creation date, type)

**Time window:** June 2026 (sample table)

**Exclusions:**
- Pages with less than 10 impressions (not enough signal)
- Pages with missing engagement data

**Public-safe note:** All data is pseudonymized. No client names, domains, URLs, or private queries are included.

## Methodology

### Task Type
Binary Classification — predict whether a page matches user intent (1) or not (0).

### Features
| Feature | Description | Available At Decision Moment? |
|---------|-------------|------------------------------|
| `avg_position` | Average search position | Yes — historical GSC data |
| `ctr` | Click-through rate | Yes — historical clicks/impressions |
| `engagement_rate` | GA4 engaged sessions | Yes — historical GA4 data |
| `impressions_90d` | 90-day impressions | Yes — historical GSC data |

### Label Definition (Proxy)
`high_intent = 1` if:
- `ctr > 0.05` AND `engagement_rate > 0.3`

This proxy assumes that high engagement (clicks + scrolls) indicates matched user intent.

### Baseline
A hand-rule from Week 4:
- If `ctr < 0.02` AND `avg_position > 10` → flag for refresh
- Precision@50 = 0.680

### Validation Design
- **Split:** 80/20 random split
- **Stratification:** Balanced by target
- **Leakage prevention:** Features and label are from the same time window; no future data is used

### Models
1. **Decision Tree** (max_depth=5) — interpretable baseline
2. **Random Forest** (n_estimators=100, max_depth=5) — ensemble improvement

## Results

### Model vs Baseline Comparison

| Model | Precision@50 | Improvement vs Baseline |
|-------|--------------|------------------------|
| Hand-Rule Baseline | 0.680 | — |
| Decision Tree | 0.740 | +8.8% |
| Random Forest | **0.760** | **+11.8%** |

### Feature Importance (Random Forest)

1. **CTR** — most important predictor
2. **engagement_rate** — second most important
3. **avg_position** — third
4. **impressions_90d** — least important

**Interpretation:** CTR is the strongest signal, followed by engagement_rate. Position matters, but less than actual user engagement.

### Error Analysis

**False Positives:** Pages flagged as high intent but not actually. This happens when engagement_rate is high but CTR is low.

**False Negatives:** Pages missed as high intent. This happens when CTR is high but engagement_rate is low.

**Key Insight:** No single feature is perfect — the combination matters.

## Limitations & Honest Framing

**This is an observed, directional analysis, not a causal claim.**

1. **Proxy target:** I used engagement as a proxy for intent. A user can be engaged without the page matching their original intent (e.g., they clicked something else).

2. **Sample bias:** The sample table is June 2026 only. Results may not generalize to other months.

3. **Feature limitations:** I only used four features. More features (query type, content length, time of day) could improve the model.

4. **No client-holdout validation:** The split was random, not by client. A client-holdout split (train on some clients, test on others) would be a stronger test of generalization.

**Caveat:** This work does not prove that improving user intent prediction causes better search ranking. It only shows that ML can identify patterns that correlate with engagement.

## Ranked Recommendations

Based on the model, I recommend the following actions:

| Rank | Action | Signal |
|------|--------|--------|
| 1 | **Refresh** pages with high CTR + low engagement | Users click but don't stay |
| 2 | **Rewrite** pages with low CTR + high position | Good ranking but poor click-through |
| 3 | **Monitor** pages with improving engagement | Potential to grow |
| 4 | **Protect** pages with high CTR + high engagement | Already performing well |
| 5 | **Review** pages with low impressions | Not enough data |

## Reproducibility

All code and notebooks are available in the GitHub repository:

- **Repository:** https://github.com/ml-bree/flyrank-ml-internship-starter
- **Data Contract:** `work/notebooks/w03_data_contract.ipynb`
- **Baseline:** `work/notebooks/w04_baseline_score.ipynb`
- **Model:** `work/notebooks/w05_model.ipynb`
- **Capstone Paper:** `work/capstone_paper.md`

### Running the Code
1. Clone the repo
2. Install requirements: `pip install -r requirements.txt`
3. Open the notebooks in Colab
4. Connect to Hugging Face with your READ token
5. Run the cells

## Acknowledgments

This work was built on the FlyRank ML Internship dataset.

**Data credit:** Built on the FlyRank ML Internship dataset. Data provided by FlyRank (https://flyrank.ai).

---

**Author:** Breattah Okeyo  
**Date:** August 2026  
**Track:** Machine Learning Internship  
**Lane:** User Intent / Refresh Opportunity Scoring
