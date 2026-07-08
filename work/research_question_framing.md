# Research Question Framing

## Provisional Lane
**User Intent**

---

## Research Question
Can we predict user intent from search behavior and content engagement signals, and use that to improve content recommendations?

More specifically: **Can we identify whether a user's search session indicates informational, navigational, or transactional intent based on their interaction patterns?**

---

## Unit of Analysis
**Search sessions / query-page pairs**

- Each row represents a search interaction between a user and a page
- Data includes: query terms, page viewed, engagement metrics (CTR, scroll rate, time on page)

---

## The Output
**Intent classification or intent score**

- **Option A:** A 3-class prediction: informational / navigational / transactional
- **Option B:** A probability score for each intent type
- **Option C:** A ranking of pages most likely to satisfy each intent type

---

## Action Someone Could Take
1. **Search ranking:** Adjust ranking based on predicted intent
   - Example: For "navigational" intent, show known brand pages higher
   - For "transactional" intent, show product/service pages higher

2. **Content strategy:** Identify gaps in content that match user intent
   - Example: If users have "informational" intent but only see product pages, add educational content

3. **Personalization:** Customize the search experience based on intent patterns

---

## Cost of a Wrong Recommendation

| Error Type | Cost |
|------------|------|
| **False Positive (predicts intent but wrong)** | Show irrelevant content → user gets frustrated → leaves → lost engagement |
| **False Negative (misses intent)** | Don't show what user needs → same result: frustration + churn |
| **Misclassifying intent type** | Example: Showing product pages when user wants information → poor experience |
| **Over-relying on intent model** | If model is 60% accurate, 40% of users get wrong content → bad user experience |

---

## Why ML Can Help (Not Just a Simple Rule)

**A simple rule approach:**
- "If query has 'buy' or 'price' → transactional"
- "If query has 'how to' → informational"

**Problems with simple rules:**
1. Too rigid – misses edge cases
2. Doesn't capture context
3. Can't learn from feedback

**Why ML is better:**
- Can learn complex patterns across multiple features
- Adapts to new behavior over time
- Captures interactions between features (e.g., scroll rate + time on page + query length together tell a story)

**Features I might use:**
- Query length, word count
- CTR, engagement_rate, scroll_rate
- Session duration, pages visited
- Content type, content age
- Position metrics, impression tier

---

## Cautious Language

> *"This is a provisional research question for my capstone project. I recognize that predicting user intent is complex and this model will be an approximation, not a perfect solution. The question may evolve as I explore the data and discover what signals are most useful. Any findings will be directional, not causal."*

---

## Next Steps

1. **Explore the data:** What features are available? Which ones might indicate intent?
2. **Baseline model:** Start with a simple model (like the decision tree from Week 1)
3. **Feature engineering:** Create new features that might capture intent signals
4. **Evaluate:** Use client-holdout validation to avoid leakage
5. **Iterate:** Based on results, refine the question and approach

---

## Notes to Self

- This lane is **mentor-gated** – I'll need to discuss with mentor before full implementation
- The data may not have explicit intent labels – I may need to create proxy labels (e.g., high CTR + high engagement = informational intent)
- Consider starting with a simpler question and building up
- Remember: it's about the *action*, not just the model
