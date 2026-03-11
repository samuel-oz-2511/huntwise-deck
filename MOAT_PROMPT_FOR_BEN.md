# Prompt for Ben — Technical Moat Extraction

Copy-paste the prompt below into your Claude Code session (the one with the HuntWise codebase). It will analyze the repo and produce a structured technical moat summary we can use for the FutureFirst meeting.

---

## PROMPT (copy everything below this line)

```
I need you to analyze this entire HuntWise codebase and produce a structured "Technical Moat" document for a VC meeting. This is for our seed round pitch — the investor will ask "what's defensible here?" and "why can't someone rebuild this in a weekend with ChatGPT?"

## What to produce

Create a markdown document called `TECHNICAL_MOAT.md` with the following sections:

### 1. Architecture Overview
- Map the full system architecture: backend, frontend, database, AI pipeline, integrations
- What languages, frameworks, databases, and infra do we use?
- How do the components connect? (diagram in text/ascii if helpful)
- How many services/modules exist? Rough lines of code?

### 2. The ATS Intelligence Engine — Our Core IP
This is our main moat. Analyze all prompt files, scoring logic, and adaptation rules. Specifically:
- List every rule in our CV adaptation prompt system (there should be ~17 rules)
- For each rule, explain what it does and WHY it exists (what failure mode it prevents)
- Explain how technical vs non-technical role detection works and why it matters
- Explain the hidden keyword layer — when it helps, when it hurts
- Explain our ATS scoring model awareness (AI-based vs keyword-matching ATS behavior)
- What is the "prime directive" (never score lower than raw) and how is it enforced?

### 3. Data Flywheel & Feedback Loop
- How does our system learn from each CV adaptation?
- What data do we collect per candidate run? (gaps, scores, ATS platform, success/failure)
- How does the gap analysis pipeline work (database → prompt → output)?
- What's the feedback loop: does ATS score data feed back into improving the rules?
- How many test iterations have we run and what patterns emerged?

### 4. ATS Platform Intelligence
- How do we detect which ATS a company uses?
- What ATS-specific behaviors have we discovered through testing?
- List all ATS platforms we've tested against and key findings per platform
- How does our system adapt output per ATS type?

### 5. Built with Claude Code — The Meta-Moat
Be honest and specific here. We used Claude Code (Anthropic's CLI agent) to build HuntWise:
- What parts of the codebase were built using Claude Code?
- How did the AI-assisted development process work? (iterative prompt engineering, test-driven refinement, etc.)
- How does using AI to build an AI product create compounding speed advantage?
- What's our estimated development velocity vs a traditional team?
- How many engineers would it normally take to build what we've built? How many did it actually take?

### 6. Why This Can't Be Replicated Easily
Synthesize everything above into a clear moat argument:
- **Empirical knowledge**: We've run 30+ real ATS tests across multiple platforms and discovered non-obvious behaviors (e.g., AI-based ATS holistic scoring, technical vs non-technical divergence, hidden keyword backfire effects). This took months of iteration. A competitor starting from scratch would need to rediscover all of this.
- **Rule system complexity**: 17 interacting rules with edge cases — not something you get from a single prompt engineering session
- **ATS behavioral database**: Platform-specific intelligence that grows with every test
- **Speed of iteration**: Claude Code lets a 3-person team ship at the pace of a 10-person team
- **Network effects**: As more candidates use the system, gap patterns and success data compound

### 7. Key Metrics for the Pitch
Pull exact numbers from the codebase/data:
- Cost per CV analysis (we know it's ~$0.013 per credit)
- Number of beta users
- Number of ATS test iterations run
- Number of rules in the prompt system
- Supported ATS platforms
- Lines of code / number of modules
- Time from zero to working product

## Format requirements
- Be precise and factual — every claim must be provable from the codebase
- If you can't find something in the code, say so explicitly (don't make it up)
- Include file paths for key components so I can verify
- Keep it concise — this feeds into a 30-minute VC pitch, not a whitepaper
- Use bullet points, not paragraphs
```

---

## What to do with the output

Send me the `TECHNICAL_MOAT.md` file. I'll use it to:
1. Update the pitch deck's moat slide with hard technical evidence
2. Prepare talking points for when Tomer Golan asks "what's defensible?"
3. Have ready answers for "why can't [big company] just copy this?"
