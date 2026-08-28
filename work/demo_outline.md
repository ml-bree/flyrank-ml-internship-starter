# 5-Minute Demo Outline — User Intent Prediction

## 1. The Problem (1 minute)
"At FlyRank, content ranks well but quietly decays. The hand-rule baseline is 0.680 precision — it catches some pages, but misses patterns deeper in the ranking."

## 2. My Approach (1 minute)
"I built a Random Forest classifier on real search data. I used four features: CTR, engagement_rate, avg_position, and impressions_90d. The target: pages where users actually engage."

## 3. The Results (1 minute)
"The Random Forest achieved 0.760 Precision@50 — an 11.8% improvement over the baseline. Feature importance showed CTR was the strongest signal, followed by engagement_rate."

## 4. The Action Playbook (1 minute)
"Here's what a content team can do with this:
- Refresh: High CTR + low engagement
- Rewrite: Low CTR + high position
- Protect: High CTR + high engagement
- Monitor: Improving engagement
- Review: Low impressions"

## 5. What's Next (1 minute)
"This is directional, not causal. Next steps: add more features, validate on more months, and build a live dashboard."

## One Chart to Show
- Bar chart: Model vs Baseline Precision@50 (0.680 → 0.760)
