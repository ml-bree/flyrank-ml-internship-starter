# Social Post — Methodology

## Short Version (Twitter/LinkedIn)

I built a Random Forest classifier on FlyRank search data (79M rows) to predict which pages need content refresh.

The hand-rule baseline was 0.680 precision. The model hit 0.760 — an 11.8% improvement.

Key insight: CTR is the strongest signal, but engagement_rate adds power. Position matters less than actual user behavior.

The output: a ranked action playbook — Refresh, Rewrite, Monitor, Protect, Review.

GitHub: https://github.com/ml-bree/flyrank-ml-internship-starter
Paper: https://ml-bree.github.io/flyrank-ml-internship-starter/

#MachineLearning #DataScience #FlyRank #AI #SearchRanking

## Employer Summary (3 Sentences)

**What I built:** A Random Forest classifier that predicts which pages need content refresh before they decline.

**On what data:** The FlyRank ML Internship dataset — 79M rows of real search performance data.

**What it showed:** The model achieved 0.760 Precision@50, an 11.8% improvement over the hand-rule baseline. The output is a ranked action playbook for content teams.
