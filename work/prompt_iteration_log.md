# Prompt Iteration Log

**Task:** Job/Scholarship Applications — Cover Letter for ML Intern Role

**What "Done Well" Looks Like:**
- 3-5 quality applications submitted per week
- Tailored cover letters that match the job description
- No generic or AI-generated-sounding phrases
- Includes specific numbers and results

---

## Version 0: Naive Baseline

**Technique:** Baseline (No technique)

**Prompt:**
Write a cover letter for a job application.

**Output (excerpt):**
Claude gave three cover letter options: Standard Professional, Bullet Point Style, and Short & Punchy, with tips for personalization.

**What changed in the prompt:**
N/A — This is the baseline.

**What improved in the output:**
N/A — This is the baseline.

**What still failed:**
Too generic. Sounds like a template. No personalization. Uses corporate buzzwords. No specific experience or numbers.

**What I would try next:**
Add role assignment.

---

## Version 1: Role Assignment

**Technique:** Role Assignment

**Prompt:**
You are a hiring manager with 10 years of experience in tech, specifically in AI/ML roles. You've read thousands of cover letters and can spot generic ones immediately. Write a cover letter that would actually grab your attention and make you want to interview the candidate.

**Output (excerpt):**
A hiring manager's perspective cover letter with technical vocabulary: "I don't care about your 'passion for machine learning.' I care about: Can you frame a business problem as an ML problem? Do you understand the gap between a Kaggle notebook and production?" Includes a sample cover letter with sections on Math, Bottlenecks, and Skepticism.

**What changed in the prompt:**
Added role (hiring manager perspective).

**What improved in the output:**
Now it's specific and technical. Uses actual ML vocabulary (catastrophic forgetting, internal covariate shift, data leakage). Shows understanding of production concerns (GPU utilization, data loading bottlenecks).

**What still failed:**
Still generic in some places. No specific job description match. No mention of MY actual experience.

**What I would try next:**
Add context and motivation (competitive role, my actual experience).

---

## Version 2: Context & Motivation

**Technique:** Context & Motivation

**Prompt:**
You are a hiring manager with 10 years of experience in tech, specifically in AI/ML roles. I'm applying for a Machine Learning Intern position with over 200+ applicants. Use my FlyRank experience: built a decision tree on search data, improved precision from 0.680 to 0.800 (17.6% improvement), tested depths 2-5, found engagement_rate better than impressions_90d. Write a cover letter that proves I understand ML fundamentals, shows results, and stands out.

**Output (excerpt):**
A cover letter that leads with numbers: "Most intern cover letters tell me about their 'passion for AI.' I'll skip that. Let me show you what I actually did." Includes specific details: decision tree depths, feature swapping, engagement_rate vs impressions_90d, 0.680 → 0.800 precision (17.6% improvement).

**What changed in the prompt:**
Added context (competitive role) + my actual experience (FlyRank numbers).

**What improved in the output:**
Now it's SPECIFICALLY about me. Has actual numbers: 0.680 → 0.800, 17.6%. Shows engineering rigor: "Tested depths 2, 3, 4, and 5" not just "tuned a model."

**What still failed:**
Still a template. Could use examples of what "good" looks like.

**What I would try next:**
Add few-shot examples (strong vs weak).

---

## Version 3: Few-Shot Examples

**Technique:** Few-Shot Examples

**Prompt:**
You are a hiring manager with 10 years of experience. I'm applying for an ML Intern role. Use my FlyRank experience: built decision tree, improved precision 0.680 → 0.800 (17.6%), tested depths 2-5, found engagement_rate better than impressions_90d.

Here's a WEAK cover letter (generic):
"I am writing to express my strong interest... I have a strong foundation in Python... I am passionate about AI..."

Here's a STRONG cover letter (specific):
"In my FlyRank ML Internship, I built a decision tree on real search data. The hand-rule baseline was 0.680 precision. I tested depths 2-5 and swapped features... My final model hit 0.800 precision — a 17.6% improvement..."

Now write MY cover letter following the STRONG example.

**Output (excerpt):**
"Subject: 0.680 → 0.800 Precision / FlyRank ML Intern. At FlyRank, I took a search relevance baseline at 0.680 precision and pushed it to 0.800. I built a decision tree... Tested depths 2, 3, 4, and 5. Swapped features systematically. Found that engagement_rate consistently outperformed impressions_90d... Final model: 0.800 precision. 17.6% lift. Not from tuning hyperparameters. From knowing which features to trust." (143 words)

**What changed in the prompt:**
Added few-shot examples (weak vs strong).

**What improved in the output:**
Now it's short (143 words). No fluff. No passion statements. Every sentence contains specific information. Numbers front and center.

**What still failed:**
Still has bracketed sections. Could be more structured.

**What I would try next:**
Add output structure (clear sections).

---

## Version 4: Output Structure

**Technique:** Output Structure

**Prompt:**
You are a hiring manager with 10 years of experience. I'm applying for an ML Intern role. Use my FlyRank experience: built decision tree, improved precision 0.680 → 0.800 (17.6%), tested depths 2-5, found engagement_rate better than impressions_90d.

Write my cover letter with EXACTLY this structure:
1. HEADLINE: Bold statement with numbers
2. PROBLEM: What I was solving
3. APPROACH: What I did (specifics)
4. RESULT: The numbers
5. WHAT I LEARNED: One key insight
6. THE ASK: What I want

Keep it under 200 words. No buzzwords. No passion statements.

**Output (excerpt):**
"HEADLINE: Took search precision from 0.680 to 0.800 at FlyRank.
PROBLEM: Search relevance baseline used hand-rules...
APPROACH: Built a decision tree on real search data. Tested depths 2, 3, 4, and 5. Swapped features...
RESULT: Final model hit 0.800 precision. 17.6% relative lift...
WHAT I LEARNED: Feature selection matters as much as model architecture...
THE ASK: I documented everything on GitHub. Would like 15 minutes to walk you through what I built..." (121 words)

**What changed in the prompt:**
Added output structure (6 clear sections).

**What improved in the output:**
Now has clear structure. Every section has a purpose. Easy to skim. Short (121 words).

**What still failed:**
Still generic — doesn't match a specific job description.

**What I would try next:**
Add step decomposition (analyze job description first).

---

## Version 5: Step Decomposition

**Technique:** Step Decomposition

**Prompt:**
I need a cover letter for a Machine Learning Intern position. Follow these steps:

STEP 1: Analyze this job description:
[Job description for ML Intern role with search ranking responsibilities]

STEP 2: Identify the top 3 skills they're looking for.

STEP 3: Match my FlyRank experience to those skills:
- Built decision tree model on search data
- Improved precision from 0.680 to 0.800 (17.6%)
- Tested depths 2-5 and swapped features
- Found engagement_rate better than impressions_90d
- Documented everything on GitHub

STEP 4: Write the cover letter with structure:
1. HEADLINE: Bold statement with numbers
2. PROBLEM: What I was solving
3. APPROACH: What I did (specifics)
4. RESULT: The numbers
5. WHY I FIT THIS ROLE: Match my skills to the job description
6. THE ASK: What I want

Keep it under 200 words. No buzzwords. No passion statements.

**Output (excerpt) (Claude):**
"HEADLINE: Took search precision from 0.680 to 0.800 at FlyRank—a 17.6% lift.
PROBLEM: The existing search relevance baseline was a hand-rule heuristic...
APPROACH: I built a decision tree on real search data. I systematically tested depths 2, 3, 4, and 5...
RESULT: Final model hit 0.800 precision...
WHY I FIT: Your job description emphasizes hands-on model experimentation and shipping improvements. I didn't just run a notebook—I ran controlled experiments, documented findings, and pushed to GitHub.
THE ASK: I've documented everything on GitHub with ablation results. Would like 15 minutes to walk through what I built..."

**Output (excerpt) (ChatGPT):**
"Built a search ranking model that improved precision from 0.680 to 0.800 (17.6% lift)
I recently worked on a search ranking project where the goal was to improve the relevance of search results...
I built a decision tree model in Python and evaluated it using precision metrics. I tested tree depths from 2–5, swapped ranking features...
The final model improved precision from 0.680 to 0.800, a 17.6% lift...
This role matches the work I have already been doing: building and evaluating ML models, experimenting with feature selection...
I'm applying for the Machine Learning Intern position because I want to contribute to search ranking improvements..."

**What changed in the prompt:**
Added step decomposition (analyze job description → identify skills → match experience → write letter).

**What improved in the output:**
Now includes a specific company reference from the job description. "WHY I FIT" section directly connects FlyRank experience to the job requirements.

**What still failed:**
Could benefit from cross-model comparison.

**What I would try next:**
Compare Claude vs ChatGPT.

---

## Cross-Model Comparison

### Final Prompt (Run on Both):

### Comparison Table:

| Aspect | Claude | ChatGPT |
|--------|--------|---------|
| Tone | Direct, confident, slightly edgy | Professional, clear, straightforward |
| Specificity | Used exact numbers (0.680, 0.800, 17.6%) | Used exact numbers (0.680, 0.800, 17.6%) |
| Structure | Followed requested format (6 sections) | Followed requested format (6 sections) |
| Length | ~150 words | ~120 words |
| Failure Points | Slightly informal for some corporate settings | More formal and safer, slightly generic in places |

**Which was better and why:**
ChatGPT wrote a cleaner, more professional cover letter that is safer for most companies — it's clear, uses the numbers, and directly maps skills to the job description. Claude was more direct and confident, with lines like "I'm not applying to 50 companies" — which could stand out or feel too casual depending on the company culture. For general use, ChatGPT's output is more versatile.

---

## Final Reusable Prompt Template
I need a cover letter for [JOB TYPE] position. Follow these steps:

STEP 1: Analyze this job description:
[JOB DESCRIPTION]

STEP 2: Identify the top 3 skills they're looking for.

STEP 3: Match my experience to those skills:
- [EXPERIENCE 1 with number]
- [EXPERIENCE 2 with number]
- [EXPERIENCE 3 with number]

STEP 4: Write the cover letter with structure:
1. HEADLINE: Bold statement with numbers
2. PROBLEM: What I was solving
3. APPROACH: What I did (specifics)
4. RESULT: The numbers
5. WHY I FIT THIS ROLE: Match my skills to the job description
6. THE ASK: What I want

Keep it under 200 words. No buzzwords. No passion statements.


---

## Summary Table

| Version | Technique | What Improved |
|---------|-----------|---------------|
| 0 | Baseline | N/A |
| 1 | Role Assignment | Became specific and technical |
| 2 | Context & Motivation | Included my actual FlyRank experience |
| 3 | Few-Shot Examples | Shortened to 143 words, no fluff |
| 4 | Output Structure | Clear 6-section format |
| 5 | Step Decomposition | Tailored to specific job description |

**Most valuable technique:** Step Decomposition — it forced the prompt to analyze the job description and match skills directly, making the output truly tailored.

**What I learned:** Prompt engineering is iterative. Each layer builds on the previous one. The best results come from combining multiple techniques in the right order. Step decomposition was the most impactful because it forced the AI to understand the job requirements before writing.
