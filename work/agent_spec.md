# Agent Spec: Job Application Assistant

## 1. Job to Be Done

My agent helps me research companies, match my experience to job descriptions, and draft tailored cover letters. It does **one job well**: turning a job description into a custom cover letter that sounds like me.

**What it does:**
- Reads a job description
- Extracts key requirements
- Matches my FlyRank experience to those requirements
- Drafts a cover letter using my voice card
- Suggests improvements or alternatives

**What it does NOT do:**
- Submit applications (that's my job)
- Make decisions about which jobs to apply for (I decide)
- Negotiate offers (far outside scope)

## 2. The User (Me)

**Who:** Me — an ML intern applying for ML roles
**Usage frequency:** 3-5 times per week (as I find job postings)
**Key needs:**
- Fast, consistent cover letters
- Honest about my experience
- Uses my voice, not a template
- Includes specific numbers (17% lift, 0.680 → 0.800)

## 3. Tools and Data Needed

| Tool/Data | What It Does | Access Plan |
|-----------|--------------|-------------|
| Job description text | Input for each run | I paste it from the job posting |
| My FlyRank experience | Context for matching | Stored in Claude Project files |
| My voice card | Maintains consistent tone | Stored in Claude Project |
| My GitHub repo | Proof of work | Public URL, accessible via MCP |
| Company search | Research company culture | MCP web search tool |

## 4. Draft Instructions (How the Agent Works)

**System prompt:**
"You are a job application assistant. Your job is to help me write custom cover letters that sound like me.

**About Me:**
- ML practitioner with FlyRank ML Internship experience
- Built decision tree model, improved precision 0.680 → 0.800 (17.6%)
- Voice: Build things, deliver results, have fun, be direct

**Rules:**
- No buzzwords (leveraged, optimized, passionate)
- Lead with numbers
- Under 200 words
- Sound human, not like a template

**Process:**
1. Extract requirements from job description
2. Match my experience to those requirements
3. Identify any gaps honestly
4. Draft cover letter with structure: Hook → Skills → Proof → Fit → Closing
5. Review tone and specificity"

## 5. Five Eval Cases (Before Building)

| Case | Input | Expected Output |
|------|-------|-----------------|
| 1 | ML job with Python, scikit-learn | Cover letter highlighting FlyRank experience |
| 2 | ML job requiring PyTorch | Cover letter acknowledging gap + readiness to learn |
| 3 | Non-ML job (e.g., data analyst) | Cover letter adapted to analytical skills |
| 4 | Job with unclear description | Agent asks clarifying questions |
| 5 | Job with strong company mission | Cover letter includes company-specific reference |

## 6. Guardrails (Risks and Safety)

**What the agent must confirm:**
- The job description is complete enough to process (not a snippet)
- The cover letter includes specific numbers (no generic claims)
- The tone matches my voice card

**What the agent must NEVER do:**
- Apply to jobs automatically
- Add fake experience or exaggerate results
- Use corporate buzzwords
- Send emails without my review

**What the agent must flag:**
- Any request that seems unethical (e.g., "write a cover letter for a job I'm unqualified for")
- Any attempt to use my personal data in unsafe ways

## 7. Platform Choice

**I choose: Claude Project with MCP connectors**

**Why:**
- I already have a Claude Project set up (Job Application Workflow)
- It supports MCP for reading files and searching the web
- Free tier is sufficient for this scope
- I can reuse my existing prompts and voice card

**Alternatives considered:**
- **Custom GPT (OpenAI)**: Requires paid plan, less control
- **n8n workflow**: Overkill for a simple agent, more setup time
- **Scripted agent**: Too much code for a 10-hour build

**Why Claude Project wins:**
- Already has my voice card, experience, and prompts
- MCP gives it tool access without coding
- I can iterate quickly

## 8. Summary

| Element | Decision |
|---------|----------|
| **Job** | Job Application Assistant |
| **User** | Me (ML intern) |
| **Frequency** | 3-5x/week |
| **Tools** | MCP (file read, web search) |
| **Platform** | Claude Project + MCP |
| **Eval Cases** | 5 defined |
| **Guardrails** | Confirm, flag, never do |
| **Build Time** | ~10 hours |

## 9. What Success Looks Like

The agent is successful when:
1. It generates a cover letter in under 5 minutes
2. The letter sounds like me (voice card match)
3. The letter includes specific numbers from my FlyRank experience
4. I don't need to rewrite major sections
5. It catches gaps in my experience honestly

## 10. Next Steps

1. Set up MCP web search
2. Add company research step to workflow
3. Test on 5 real job postings
4. Refine based on eval cases
5. Use it for actual applications
