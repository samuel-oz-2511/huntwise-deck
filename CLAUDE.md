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

## PRODUCT ARCHITECTURE — FROZEN. DO NOT CHANGE WITHOUT EXPLICIT INSTRUCTION.

The three-layer product architecture is a hard constant. The names, order, and concepts are locked.

| Layer | Name | Trigger |
|---|---|---|
| Layer 1 | Behavioral Baseline | Always — passive, invisible |
| Layer 2 | Async Challenge | Only when Layer 1 flags an anomaly |
| Layer 3 | Human Review | Only when Layer 2 flags divergence |

**What each name means:**
- Layer 1: behavioral metadata captured while the form is filled. No friction.
- Layer 2: short async task framed as part of the application. Not a quiz. Not biometric. Detects proxy impersonation and AI-assisted responses.
- Layer 3: Sentriq analyst reviews the full signal stack. Employer decides. Zero automated rejections. EU AI Act compliant by design.

**What is NOT a layer:**
- The cross-company signal graph is NOT Layer 2. It is the network effect / moat, described separately in the Network Effects slide. It has never been a numbered product layer.

**Pre-push check — run before committing any deck:**
```bash
grep -c 'Trust Layer' <file>       # must be 0 — Trust Layer is dead
grep -c 'Async Personalized' <file> # must be 0 — old name, retired
```

**Authorization rule:** Never rename, reorder, or redefine any of the three layers in any deck, slide, email, or copy without Samuel explicitly saying so. If the product architecture changes, Samuel will state it. Do not infer it from memory, prior decks, or any other source.

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

## ntfy.sh Open Tracking

Every new password-gated deck must include open tracking. Follow this exact pattern:

**1. Topic naming:** `sentriq-[shortname]-[4char random]` e.g. `sentriq-libertad-x3n7`

**2. Register in analytics script:** Add entry to `TRACKED_ROOMS` in `~/.compass/scripts/dataroom-analytics.py` with topic, label, contact, fund, and url.

**3. JS implementation — always use this pattern:**
```js
function pingOpen() {
  var ua = navigator.userAgent;
  var t = new Date().toISOString();
  fetch('https://ipapi.co/json/')
    .then(function(r){ return r.json(); })
    .then(function(geo) {
      var loc = (geo.city || '') + ', ' + (geo.country_name || '') + ' (' + (geo.ip || '') + ')';
      var org = geo.org || '';
      var msg = '[DECK NAME] deck opened\n' + loc + '\n' + org + '\n' + t;
      fetch('https://ntfy.sh/[TOPIC]', { method: 'POST', mode: 'no-cors', body: msg }).catch(function(){});
    })
    .catch(function() {
      fetch('https://ntfy.sh/[TOPIC]', {
        method: 'POST', mode: 'no-cors',
        body: '[DECK NAME] deck opened (location unavailable)\n' + ua.substring(0,80) + '\n' + t
      }).catch(function(){});
    });
}
```

**Rules:**
- Always use `mode: 'no-cors'` on the ntfy fetch — custom headers trigger CORS preflight which blocks silently
- Always enrich with IP/city/country/org via `ipapi.co/json/` before pinging ntfy
- Always include a fallback ping if ipapi fails
- Fire on password entry AND on session resume (auto-unlock from sessionStorage)
- Use `sessionStorage` to fire once per browser session only — key: `[shortname]-pinged`
- Test by opening in a new tab after deploy (sessionStorage is fresh per tab)

---

## GitHub Pages

- Repo: `samuel-oz-2511/huntwise-deck`
- Branch: `master`
- Live URL base: `https://samuel-oz-2511.github.io/huntwise-deck/`
- Never use BeautifulSoup to reorder HTML slides — it moves nav and script tags. Use string replacement only.
- PDF export: use Playwright + img2pdf. Script at `/tmp/export_sniff_pdf.py` as reference.

---

## New Deck Creation Rules

These rules exist to prevent CSS and design drift between decks. They are a checklist, not guidelines. Run every item before marking a deck complete.

---

### Rule 1: Always start from the canonical standard file

The canonical CSS standard is `/Users/samuelkemper/Desktop/huntwise-deck/sentriq-97212.html`.

When creating any new deck:
1. Open `sentriq-97212.html`.
2. Copy the entire file.
3. Rename the copy to the new deck filename.
4. Change only: `<title>`, meeting badge text, password gate label, ntfy topic, `atob()` password value, and slide content.
5. Never start a new deck from scratch. Never copy from any file other than `sentriq-97212.html` unless a canonical template file has been explicitly designated to replace it.

---

### Rule 2: Never rewrite the style block from scratch

The `<style>` block between lines 10 and 202 of `sentriq-97212.html` is the locked standard. Copy it verbatim. Do not regenerate it. Do not summarize it. Do not reconstruct it from memory.

If a rule change requires updating the style block (new component, revised color), update `sentriq-97212.html` first, then propagate to all decks. The standard file is the source of truth, not any individual deck.

---

### Rule 3: Required :root CSS variables

Every deck must have all of the following variables in its `:root` block, with exactly these values:

```css
--bg:      #09090F;
--card:    #0D0E1A;
--border:  #161728;
--muted:   #8080A8;
--amber:   #E8A020;
--amber-d: #B87010;
--text:    #ffffff;
--text-sub: rgba(255,255,255,0.72);
--green:   #44CC88;
--primary: #E8A020;
--white: #ffffff;
--gray-900: #09090F;
--gray-800: #0D0E1A;
--orange: #E8A020;
--red: #E05555;
--purple: #3A2058;
--text-dim: rgba(255,255,255,0.52);
```

Before pushing, run:
```bash
grep -c "\-\-amber:" <file>   # must return 1
grep -c "\-\-text-sub:" <file>  # must return 1
grep -c "\-\-text-dim:" <file>  # must return 1
grep -c "\-\-amber-d:" <file>  # must return 1
```

If any count is 0, the variable is missing. Do not push.

---

### Rule 4: Inline color rules for slide HTML

**Permitted inline uses (hardcoded hex/rgba):**

These exact values may appear inline in slide HTML because they express transparency variants not captured by variables:
- `rgba(232,160,32,...)` — amber at any opacity
- `rgba(255,255,255,...)` — white at any opacity
- `rgba(9,9,15,...)` — background at any opacity
- `rgba(239,68,68,...)` — red at any opacity
- `rgba(68,204,136,...)` — green at any opacity
- `rgba(245,158,11,...)` — orange-amber variant at any opacity
- `rgba(26,26,53,...)` — used in bg-cover gradient only
- `#E8A020`, `#B87010`, `#44CC88`, `#E05555`, `#09090F`, `#0D0E1A`, `#161728`, `#ffffff` — full hex for SVG fills and gradient stops

**Required: use CSS variables for all named color references in slide HTML:**
- Use `var(--amber)` not `var(--primary)` or `var(--orange)` when the intent is the primary amber accent color. `--primary` and `--orange` both resolve to `#E8A020` but `var(--amber)` is the canonical token for slide copy.
- Use `var(--text)` for body text references.
- Use `var(--text-sub)` for secondary text.
- Use `var(--text-dim)` for tertiary/caption text.
- Use `var(--muted)` for muted labels.
- Use `var(--border)` for border colors.
- Use `var(--card)` for card backgrounds.

**Prohibited inline colors (these must never appear hardcoded in slide HTML):**
- `#A06010` — off-brand amber variant. Use `var(--amber-d)` or `rgba(232,160,32,...)`.
- `#604010` — not in the system. No equivalent. Remove.
- `#2A2A50` — not in the system. Use `var(--purple)` (`#3A2058`) for dark purple.
- `rgba(5,150,105,...)` — teal/emerald not in the variable system. Not a brand color. Remove and use green alternatives (`var(--green)`, `rgba(68,204,136,...)`).
- Any hex value not in the permitted list above.

---

### Rule 5: Required head tag structure

Every deck must have these four head tags in this order, with no omissions:

```html
<meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<link href="https://fonts.googleapis.com" rel="preconnect"/>
<link href="https://fonts.gstatic.com" rel="preconnect" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet"/>
```

The `crossorigin` attribute on the `fonts.gstatic.com` preconnect is required. Without it, the font preconnect provides no benefit.

Check: `grep -c "fonts.gstatic.com" <file>` must return 1. `grep -c "crossorigin" <file>` must return at least 1.

---

### Rule 6: Required structural elements with correct IDs

Every deck must have these elements with the exact IDs shown:

```html
<div class="progress-bar" id="progressBar"></div>
<div class="confidential">Confidential</div>
<div class="meeting-badge" id="meetingBadge">[Fund Name]</div>
<div class="deck" id="deck">
```

The `id="meetingBadge"` is required. Without it, the JS that shows/hides the badge on slide 0 will throw a silent error. Check: `grep -c 'id="meetingBadge"' <file>` must return 1.

---

### Rule 7: Use CSS component classes in slide HTML, never inline equivalents

The following CSS classes exist for a reason. When a slide needs one of these components, use the class. Never recreate the component with inline styles.

| Component | Correct class | Never do this |
|---|---|---|
| Lifecycle grid | `<div class="lc-grid">` | Custom inline grid |
| Lifecycle stage | `<div class="lc-stage">` | Custom inline stage |
| Sentriq-highlighted stage | `<div class="lc-stage lc-sentriq">` | Inline amber border/background |
| Danger stage | `<div class="lc-stage lc-danger">` | Inline red border/background |
| Security stack row | `<div class="stack-layer">` | Custom flex row |
| Layer Zero row | `<div class="stack-layer-zero">` | Custom amber row |
| Stat number | `<div class="stat-num">` | Custom font-size + weight inline |
| Signal tag | `<span class="signal-tag">` | Custom inline badge |
| Slide label | `<span class="label">` | `<span class="slide-label">` or any other name |
| Source block | `<div class="sources">` | Plain paragraph |
| Moat card | `<div class="moat-card">` | Custom position:relative card |
| Hero quote | `<div class="hero-quote">` | Custom left-border block |
| Milestone card | `<div class="milestone-card">` | Custom inline card |

Check for rogue class names: `grep -c "slide-label" <file>` must return 0. `grep -c "class=\"label\"" <file>` must return the count of label elements.

---

### Rule 8: Pre-push grep checklist

Run all of the following commands before pushing any new or updated deck. Every command must pass its required result.

```bash
# 1. Em dashes
grep -c "—\|&mdash;" <file>
# Required: 0

# 2. Wrong domain
grep -c "sentriq\.io" <file>
# Required: 0

# 3. Double dashes
grep -c " -- " <file>
# Required: 0

# 4. Missing canonical CSS variables
grep -c "\-\-amber:" <file>
grep -c "\-\-text-sub:" <file>
grep -c "\-\-text-dim:" <file>
grep -c "\-\-amber-d:" <file>
grep -c "\-\-muted:" <file>
# Required: 1 each

# 5. meetingBadge ID present
grep -c 'id="meetingBadge"' <file>
# Required: 1

# 6. crossorigin font preconnect present
grep -c "fonts.gstatic.com" <file>
# Required: 1

# 7. Rogue slide-label class
grep -c "slide-label" <file>
# Required: 0

# 8. Prohibited off-brand colors
grep -c "#A06010\|#604010\|rgba(5,150" <file>
# Required: 0

# 9. var(--primary) in slide HTML (outside the :root and style block)
# Allowed in CSS block. Not allowed in slide div HTML as a substitute for var(--amber).
# Manual check: any var(--primary) in slide divs should be replaced with var(--amber).

# 10. Viewport meta tag present
grep -c "width=device-width" <file>
# Required: 1

# 11. Wrong plain-pillar variant — must be zero
grep -c 'rect x="10" y="20" width="9"' <file>
# Required: 0

# 12. Correct bracket+dot logo present
# THE DOT (circle) IS PART OF THE LOGO. NEVER remove it. Removing it = broken logo.
grep -c 'circle cx="28" cy="7"' <file>
# Required: 1+  — if zero, the dot was stripped by mistake. Restore it immediately.

grep -c 'rect x="9" y="16" width="11"' <file>
# Required: 1+
```

---

### Rule 9: ntfy tracking is mandatory on every new deck

Every password-gated deck must register an ntfy topic and follow the tracking pattern in the "ntfy.sh Open Tracking" section above. No deck goes live without it. The topic must also be added to `~/.compass/scripts/dataroom-analytics.py` under `TRACKED_ROOMS`.

---

### Rule 10: Audit before delivery

When adapting `sentriq-97212.html` to a new deck, before delivering:
1. Run the full grep checklist from Rule 8.
2. Visually scan for any inline hex color that is not in the permitted list from Rule 4.
3. Confirm all lifecycle, stack, and signal components use CSS classes, not inline reconstruction.
4. Confirm `id="meetingBadge"` is present and the badge text matches the fund/partner name.
5. Confirm the ntfy topic is unique, registered in `dataroom-analytics.py`, and the `atob()` password is correct.

If any item fails, fix it before delivering. Do not deliver a deck that fails the checklist.

---

### Rule 11: Copy density — text length limits

Every slide must pass this check before delivery:

**Bullet points:** Max 9 words per bullet. If a bullet is a full sentence with a subject + verb + explanation, cut it.

**Bullets per section:** Max 4. If there are 5+, merge or cut the weakest one.

**Stat cards / milestone cards:** Headline only. One supporting line max (12 words). No explanatory paragraph inside a card.

**Slide headlines (h2):** Max 12 words. Punchy, not descriptive.

**Body paragraphs:** Max 2 sentences. If you need 3 sentences to explain something, it's too complex for a slide.

**Kill list — remove on sight:**
- "That's what..." / "This is the..."
- "We believe..." / "Our approach is..."
- Parentheticals that explain the obvious
- Trailing clauses after the key claim is already made

**Per-fund decks:** Never name another investor fund in a deck going to a specific fund. Replace with "anchor investor" or "early check commitment."

**Manual check:** Read every bullet aloud. If it takes more than 3 seconds to say, it's too long.
