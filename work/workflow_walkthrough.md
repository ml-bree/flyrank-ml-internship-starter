# Job Application Workflow — Walkthrough

## Flow Diagram

┌─────────────────────────────────────────────────────────────────────┐
│ STEP 1: GATHER │
│ Input: Job description text │
│ Tool: Claude │
│ Output: Extracted requirements (company, skills, responsibilities)│
└─────────────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────────┐
│ STEP 2: SYNTHESIZE │
│ Input: Job requirements + FlyRank experience │
│ Tool: Claude (same chat) │
│ Output: Matched skills + top selling points + one key gap │
└─────────────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────────┐
│ STEP 3: DRAFT │
│ Input: Matched skills + voice card │
│ Tool: Claude (same chat) │
│ Output: Custom cover letter (under 200 words) │
└─────────────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────────┐
│ STEP 4: REVIEW │
│ Input: Draft cover letter │
│ Tool: Claude (new chat) + ChatGPT (cross-check) │
│ Output: Final edited version + tone/specificity/voice check │
└─────────────────────────────────────────────────────────────────────┘

---

## Step 1: GATHER — Extract Job Requirements

**Prompt used:**
I need you to analyze this job description and extract key information.

Job Description:
[PASTE JOB DESCRIPTION HERE]

Extract the following:

Company name and industry

Top 5 required skills (hard skills)

Top 3 nice-to-have skills

Key responsibilities (3-5 bullets)

Any specific requirements (years experience, education, certifications)

Output format:

Company Overview
Required Skills
Nice-to-Have Skills
Responsibilities
Key Requirements

**Example input:** Western Digital AI/ML Development Engineer Intern job description.

**Example output:**
```markdown
### Company Overview
Western Digital (BangPa-In, Thailand) — Storage/hardware infrastructure company.

### Required Skills
1. Python programming
2. Machine Learning fundamentals / data analysis
3. PyTorch (or similar ML frameworks)
4. Data collection and preprocessing
5. English proficiency

### Responsibilities
- Develop and test AI/ML models
- Collect and preprocess data
- Implement ML algorithms using Python/PyTorch
- Document and present findings

Step 2: SYNTHESIZE — Match Skills to Experience
Now match my experience to the job requirements you just extracted.

**My Experience:**
- FlyRank ML Internship: Built decision tree model on search data, improved precision from 0.680 to 0.800 (17.6% lift)
- Tested depths 2-5, swapped features to find what mattered
- Found engagement_rate better than impressions_90d
- Documented everything on GitHub

**My Skills:**
Python, pandas, scikit-learn, DuckDB, feature engineering, model evaluation

**Voice Card:** Build things, deliver results, have fun, be direct

For each required skill from the job description:
- How does my experience match?
- What specific example can I use?

Output as:
### Skill 1: [Name] - Match + Example
...
### Summary: My Top 3 Selling Points
### Summary: One Key Gap

Example output:
### Skill 1: Python
- Match: Strong fit — Python + pandas + scikit-learn is the stack used
- Example: Built the entire FlyRank decision tree pipeline in Python

### Summary: My Top 3 Selling Points
1. Real quantified result: 17% precision lift
2. Test and document reasoning, not just code
3. Python + pandas + scikit-learn matches their core stack

### Summary: One Key Gap
No PyTorch experience. Address directly: "Ready to pick up PyTorch; fundamentals aren't framework-specific."

Step 3: DRAFT — Write the Cover Letter
Now write a cover letter for this job application.

**My Proof Statement:** I turn messy data into working ML pipelines that deliver results.

**Job Requirements:** [Paste Step 1 output]
**My Best Selling Points:** [Paste Step 2 summary]

**Voice Card:** Build things, deliver results, have fun, be direct

**Structure:**
1. HOOK: Bold opening with my proof statement
2. SKILLS MATCH: 2-3 specific skills
3. PROOF: FlyRank project with numbers (0.680 → 0.800)
4. WHY I FIT: How I match their company values
5. GAP ADDRESS: Brief mention of PyTorch gap + readiness to learn
6. CLOSING: Confident call to action

**Rules:**
- Under 200 words
- No buzzwords
- Lead with numbers
- Sound human
- Use my voice card

Example output (final revised version):
Dear Hiring Team,

I turn messy data into working ML pipelines that deliver results.

Case in point: I built a decision tree on real search data that beat the hand-rule baseline by 17% — Precision@50 went from 0.680 to 0.800. I got there by testing depths 2 through 5 and swapping features until I found what actually mattered (engagement_rate, not impressions_90d). Then I wrote up what worked, what didn't, and why — so anyone could retrace the logic.

That's the same loop this role describes: build a model, test it, write it up, present it. I work in Python, pandas, and scikit-learn, and I know how to pick a metric that matches the real problem instead of defaulting to whatever's easiest.

WD is building the infrastructure under the AI boom. I want to work somewhere the models touch real systems, not just a leaderboard.

One honest gap: I haven't used PyTorch yet. My fundamentals — evaluation, feature engineering, iteration — aren't tied to one framework, so I'll pick it up fast.

I'd like to bring that same directness to your team. Let's talk.

Breattah Okeyo

Step 4: REVIEW — Cross-Model Comparison
Prompt used (Claude and ChatGPT):
Review this cover letter for:
1. Tone: Does it match the company's voice?
2. Specificity: Are there enough concrete examples?
3. Voice: Does it sound like a real person?
4. Clarity: Is every sentence clear?
5. Length: Under 200 words?

[PASTE COVER LETTER]

If anything is off, suggest specific fixes.

Claude Review Summary:
Tone: ✅ Confident, infrastructure-minded

Specificity: ✅ Real numbers: 0.680 → 0.800, depth sweep, feature swap

Voice: ✅ Mostly good; change "ablations" → plain English

Clarity: ⚠️ "Got there" repeated; "your JD" → "this role"

Best line: "One honest gap: I haven't used PyTorch yet"

ChatGPT Review Summary:
Tone: ✅ "Engineer-to-engineer" feel

Specificity: ✅ "This is the letter's biggest strength"

Voice: ✅ "Refreshingly human"

Clarity: ⚠️ "your JD" → "this role"

Verdict: 8.5–9/10, ready to send with minor edits

Five Runs
Run	Job Title	Company	Time	Quality (1-5)	Notes
1	AI/ML Development Engineer Intern	Western Digital	15 min	4.5/5	Full run documented above
2	Machine Learning Intern	Cohere	14 min	4/5	Adjusted for NLP/LLM focus; similar pattern
3	Machine Learning Engineer Intern	SRC Inc.	15 min	4/5	Adjusted for defense/signal processing context
4	Fall Intern - AI/ML Engineering	Terranox AI	13 min	4.5/5	Startup tone slightly more casual
5	PhD Intern - AI for Good	Microsoft Nairobi	14 min	4/5	Research-focused framing
Average time per application: ~14 minutes
Manual time per application: ~30-45 minutes
Time saved per application: ~20 minutes
Total time saved (5 applications): ~1.5 hours

Time Saved Estimate
Metric	Value
Manual time per application	30-45 minutes
Workflow time per application	~14 minutes
Time saved per application	~20 minutes
5 applications saved	~1.5 hours
Failure Points
Issue	When It Happens	Mitigation
Job description is too vague	Step 1 (GATHER)	Ask Claude to make reasonable inferences
Company culture/voice unclear	Step 4 (REVIEW)	Search company website/blog for tone
The cover letter sounds too generic	Step 3 (DRAFT)	Voice card + rules prevent this, but review catches it
PyTorch gap shows up repeatedly	Step 2 (SYNTHESIZE)	Honest framing works better than pretending
Required Human Review
Tone check: Does the letter actually match the company's culture? AI can approximate, but a human who knows the company is better.

Specificity check: Are the examples truly accurate and well-chosen?

Voice check: Does it sound like you, not like a template?

Summary
Evaluation Criteria	Status
3+ distinct steps with defined handoffs	✅ (GATHER → SYNTHESIZE → DRAFT → REVIEW)
Workflow runs end to end	✅ (5 runs completed)
Time accounting honest	✅ (Setup: 15 min, each run: ~14 min)
Failure points named	✅
Required human review named	✅

