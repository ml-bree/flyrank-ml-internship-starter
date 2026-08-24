# Agent Build Log — Job Application Assistant

## Date: 24/08/2026

### What I Built
A Claude Project agent that takes a job description and outputs a custom cover letter using my FlyRank experience and voice card.

### Agent Details
- Platform: Claude Project (no MCP needed — all tools are built into the project)
- Core job: Job description → cover letter
- Steps: GATHER → SYNTHESIZE → DRAFT → REVIEW
- Tools: Claude Project files (voice card, experience, prompts)

### What Worked
- Step 1 (GATHER): Extracts requirements correctly from any job description
- Step 2 (SYNTHESIZE): Matches my FlyRank experience to requirements
- Step 3 (DRAFT): Produces a cover letter in my voice, under 200 words
- Step 4 (REVIEW): Checks tone and specificity (cross-checked with ChatGPT)

### What Broke
1. **Agent skipped the review step** sometimes
   - Fixed: Added explicit instruction: "Run Step 4 after drafting"
2. **Some cover letters were too generic**
   - Fixed: Added "No buzzwords" rule to the prompt
3. **PyTorch gap showed up repeatedly**
   - Fixed: Honest framing in the draft step

### What I Cut from Spec
- Removed: Company research step (can add later)
- Removed: Web search (not needed for MVP)
- Reason: Start with core job, add extras later

### What I Changed
- Changed: File output from saving to text → keep in chat (faster to iterate)
- Changed: Review step from optional → always run

### What I Learned
1. Start smaller than you think — the core workflow is enough
2. Be explicit with instructions — the AI will skip steps otherwise
3. Voice card is the most important prompt — it keeps the output human
4. Honest gap framing works better than pretending you have a skill

### Time Spent
- Setup (initial Claude Project): 15 min
- Running 5 tests: 60 min
- Debugging: 30 min
- Total: ~1.75 hours
