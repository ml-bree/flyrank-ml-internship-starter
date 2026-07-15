# Voice Card: Build things, deliver results, have fun, be direct

---

## FlyRank ML Pipeline

**Problem:**
Search ranking used a hand-rule that was good at the top of the list but missed patterns deeper in the rankings. Pages that needed refreshing weren't being flagged.

**What I did:**
Built a decision tree on real search data. Tested 4 different depths (2, 3, 4, 5). Swapped features to find what actually predicted page decline. Found that engagement_rate worked better than impressions_90d.

**Key decisions:**
- Chose a decision tree over a black-box model so I could read and explain it
- Used Precision@50 as the metric because it matches how rankings actually work
- Kept client-holdout validation in mind to avoid data leakage

**Outcome:**
- Hand-rule baseline: 0.680 Precision@50
- My best model: 0.800 Precision@50
- **That's a 17% improvement over the hand-rule**

**Tech:** Python, pandas, scikit-learn, decision trees

**Link:** https://github.com/ml-bree/flyrank-ml-internship-starter

---

## Before & After: Generic AI vs My Voice

**Before (Generic AI):**
> *"Leveraged advanced machine learning techniques to optimize search ranking algorithms, achieving significant improvements in precision metrics through iterative experimentation."*

**After (My Voice):**
> *"Built a decision tree that beat the hand-rule by 17%. Tried different features and depths until it worked. Direct upgrade."*

---

## Bio (Who I Am)

I build things that work. I'm an ML practitioner who takes projects from raw data to working models — and I document everything along the way. I care about results, not buzzwords.

---

## Contact / CTA

**Let's build something.**

📧 [Your email]  
🔗 [GitHub](https://github.com/ml-bree/flyrank-ml-internship-starter)  
💼 [LinkedIn - optional]
