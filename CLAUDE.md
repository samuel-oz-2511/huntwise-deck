# Sentriq Deck Project — Standing Rules

These rules apply to every file, deliverable, email, slide, and copy produced in this directory.
They are non-negotiable and override any default behavior.

---

## HARD STOPS — CHECK BEFORE MARKING ANY TASK COMPLETE

Before delivering any written output (HTML, Word doc, PDF, email copy, slide text):

1. **Grep for em dashes.** Run: `grep -c "—\|&mdash;" <file>`. Count must be zero. If not zero, fix before delivering.
2. **Grep for .io domain.** Run: `grep -c "sentriq\.io" <file>`. Must be zero. Domain is always sentriq.co.
3. **Check for AI jargon.** Words like "delve", "leverage" (as filler), "unlock", "transformative", "game-changing", "cutting-edge", "robust solution" — remove on sight.

---

## Writing Rules

### Em Dashes
- **Never use em dashes** (— or &mdash;) anywhere. Not in titles, not inline, not in labels, not in HTML comments.
- Replace with: colon (:) for labels and headers, comma for inline parentheticals, period for sentence breaks.
- This rule has been violated repeatedly. It is a hard stop.

### Double Dashes
- **Never use double dashes** ( -- ) as a substitute for em dashes. This is the same bad practice with a different character.
- Double dashes are not a valid replacement for em dashes. They must also be replaced with colon, comma, or period.
- Hard stop check: `grep -c ' -- ' <file>` must return zero.

### Sentence Rhythm
- Short sentences. No filler. No trailing summaries after a task is done.
- Copy should sound like a security operator wrote it, not a pitch deck generator.

---

## Brand Rules

### Company Names
- Always **Sentriq** (not Sentriq Inc, not SENTRIQ)
- Always **Huntwise** (not HuntWise, not HUNTWISE)
- Domain: always **sentriq.co** (never sentriq.io, never sentriq.com)
- Emails: samuel@sentriq.co, ben@sentriq.co, access@sentriq.co (public-facing alias)

### Product Language
- Product is a **Candidate Hiring Captcha** — surfaces trust signals for humans to decide. It does not block or reject automatically.
- Never: "Candidate Application Firewall", "CAF", "trust score"
- Always: "trust signal" or "trust signals" — sounds like infrastructure, not SaaS
- Never: "ATS-agnostic" — use "platform-agnostic"
- The Cloudflare analogy: Sentriq is a pre-submission layer, upstream of everything. Use freely.

### Product Status (Critical)
- Sentriq has **no live product in production**. There is a demo only.
- Never claim: real sessions, live testing with paying customers, enterprise deployments, signed contracts.
- What is true: demo exists, design partner pipeline active, engineering underway.

---

## Deck Rules

### All Decks
- Mobile responsive — always.
- Never specify async challenge duration.
- Never say "no competitors" — the category exists in pieces. Name competitors confidently and land the gap.
- Traction language: "Each lead at a different stage of the process." Not "nothing signed yet."
- Team slide: always full names — Samuel Kemper and Ben Czarninski.

### HR Decks
- Lifecycle diagram in every HR deck.
- Narrative order: problem → lifecycle → solution → social proof → company data → ROI → ask → CTA.
- Calculator input = open roles. Dollar rate = $60/hr from lifecycle benchmarks.
- Trust layer block (Cloudflare analogy) always in solution section.

### Cold / External Decks
- GTM at position 11 (after product, competitive, moat).
- No pre-emptive objection answering.
- No meeting-specific context.
- Remove demo links and co-founder emails before cold external send.

### VC-Specific Decks
- Always place the VC's portfolio companies at their correct stage in the lifecycle diagram.
- Never add "Most verify here" or comparative claims to the lifecycle diagram — stage name, tool, cost only.

---

## Competitive Positioning

### Clarity (getclarity.ai)
- **Complement, not competitor.** Interview-layer (late funnel). Sentriq is application-layer (pre-ATS).
- When investors name Clarity: treat it as a diligence test. Answer: funnel stage difference + cost structure + knowledge graph structural barrier.
- Their $16M raise (Bessemer, Feb 2024) = market validation. Use it.
- Never position Clarity as a threat. Name them confidently.

### General
- Never say "no competitors."
- The right frame: "The category exists in pieces. Nobody has assembled the layer."
- Two most dangerous near-term threats: Persona (ATS distribution) and ATS bundling (Greenhouse, Ashby, Phenom).

---

## Legal Language

- Never paraphrase or adapt approved legal text. Use verbatim approved wording only.
- Controller/processor classification: still pending — do not state a position.
- Q1 biometric classification: fully approved language exists in memory. Retrieve it, do not rewrite it.

---

## Investor Pipeline Rules

- **FutureFirst Ventures**: fallback only. Do not activate until UpWest IC resolves.
- **SYN Ventures**: CISO-native framing only. No HR language. Shift-left, attack surface, threat intelligence.
- **UpWest**: warm deck variant — preserve "the caliber of who is spending time is the signal" framing.

---

## GitHub Pages

- Repo: `samuel-oz-2511/huntwise-deck`
- Branch: `master`
- Live URL base: `https://samuel-oz-2511.github.io/huntwise-deck/`
- Never use BeautifulSoup to reorder HTML slides — it moves nav and script tags. Use string replacement only.
- PDF export: use Playwright + img2pdf. Script at `/tmp/export_sniff_pdf.py` as reference.
