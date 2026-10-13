---
name: site-audit
description: "Independent, adversarial pre-launch audit of a finished website or landing page. Use whenever asked to review, audit, critique, QA, grade, or sanity-check a site/page, or whether it is ready to ship — 'оцени этот сайт', 'проверь лендинг', 'audit this page', 'is this ready to launch', 'найди баги на сайте', 'что не так с этим сайтом'. Also trigger proactively as a self-check immediately after building or editing a page, before declaring it done. Covers functional QA (broken links, CTAs that do not do what they promise, responsive breakage at real viewports), the Anti-AI-Slop checklist, conversion/CRO gaps, accessibility spot-checks, and performance sanity — and delivers a blocking-issues verdict, not a compliment sandwich."
---

# Site Audit

An adversarial pre-launch QA pass. The job is to find what would get this rejected at sign-off, not to reassure the person who built it.

## Independence rule — read this first

Self-grading is unreliable. If the page being audited was built earlier in *this same conversation*, that context is a liability here, not an asset — knowing the intent behind a choice makes it easy to excuse the choice instead of judging the result.

- If at all possible, prefer running this audit in a **fresh conversation**, with only the file/screenshot as input and no memory of building it.
- If that isn't possible, explicitly drop the builder's-eye view: judge only what is actually rendered/in the code, not what was *intended*. Do not credit an element for effort or for the idea behind it — only for what it does on screen. State plainly if you are auditing your own recent work, and hold the bar higher, not lower, because of it.
- Never soften a verdict to protect the previous turn's work. A correct earlier build does not make this pass a formality.

## Workflow

### 1. Render at real viewports, don't just read the code

Reading source can miss what actually breaks on screen (a `max-width: 11ch` heading looks fine in markup and becomes a 9-line ladder only when rendered). If a file is available, screenshot it before judging anything visual:

```bash
npm install puppeteer --prefix /tmp/audit 2>&1 | tail -5
node -e "
const puppeteer = require('/tmp/audit/node_modules/puppeteer');
(async () => {
  const browser = await puppeteer.launch({args:['--no-sandbox']});
  const page = await browser.newPage();
  await page.goto('file://$(pwd)/PAGE.html');
  await page.setViewport({width: 390, height: 844}); // real mobile, not a round number
  await page.screenshot({path: '/tmp/audit/mobile.png'});
  await page.setViewport({width: 1440, height: 900});
  await page.screenshot({path: '/tmp/audit/desktop.png'});
  await page.setViewport({width: 1440, height: 700}); // short laptop height — catches fold issues
  await page.screenshot({path: '/tmp/audit/desktop-short.png'});
  await browser.close();
})();
"
```

View all three screenshots. Mobile and desktop are separate tests — a page can pass on one and fail on the other (this has happened: a hero that worked at 1440px hid the CTA entirely at 390px). Always include a short-viewport-height desktop shot; laptop screens at 700–800px tall are common and get missed by only testing tall viewports.

### 2. Functional QA — before anything about taste

Bugs disqualify a page regardless of how good the design is. Check, and cite the exact line/selector for each:

- Every `href`/`action` resolves to something real — no bare `t.me/`, `#`, or `mailto:` placeholders left in
- Every CTA does what its label promises. A button that says "Choose a delivery day" must let you choose one, not just scroll to a static list — the label is a contract with the click
- Forms actually submit or visibly indicate they're not wired up yet
- Interactive elements (accordions, toggles, menus) function — click them, don't assume from the markup
- No console errors on load or interaction
- Content fits without illogical overflow at 375–390px width specifically, not just "mobile" in the abstract

### 3. First screen — separately, for mobile and desktop

Look only at what's visible with zero scroll. Can a first-time visitor tell what this is, who it's for, and what to do — in both viewports independently? A decorative element (hero graphic, video, illustration) that outranks the offer/CTA in the DOM order on mobile is a common, easy-to-miss failure.

### 4. Anti-AI-Slop + Conversion/CRO checklist

Read `/mnt/skills/user/modern-web-design/references/conversion_ux_and_authenticity.md` (sections 1–8) and check the page against every item — visual tells, code-level tells, CTA/typography/color rules, forms, trust signals. Don't summarize the file from memory; re-read it each audit, since it gets updated over time.

Run this alongside Nielsen's 10 usability heuristics (NN/g) as the structural frame for the UX pass: visibility of system status, match with the real world, user control/freedom, consistency, error prevention, recognition over recall, flexibility, aesthetic/minimalist design, error recovery, help/documentation.

**Forms, if present** — check against this, not just field count:
- Label sits above the field, not placeholder-only (a placeholder disappears on input and is not a substitute for a label)
- Errors shown inline at the field, in plain language, naming what's wrong and how to fix it — not just a banner at the top
- Single column, related fields grouped
- Field count matches the form's actual stakes: a newsletter signup justifies 1–3 fields; a full checkout averages ~11 fields industry-wide but should be trimmed toward ~8 by cutting low-value fields specifically (not just cutting the count) — removing a field users actually wanted to fill in can hurt conversion, so check *which* fields are cut, not just how many remain

### 5. Accessibility spot-check

Contrast on body text and buttons (≥4.5:1 text, ≥3:1 for UI component borders), visible focus states on interactive elements, keyboard reachability, `prefers-reduced-motion` respected on any animation. Tap targets ≥24×24px minimum (WCAG 2.2 §2.5.8), 44px+ preferred on mobile. Automated scanners (axe, Lighthouse, WAVE) only catch a subset of real WCAG violations — flag when a claim needs manual keyboard/screen-reader verification rather than asserting compliance from a scan alone. For a deeper WCAG pass, the `design-critique`/`accessibility-review` catalog plugins (already enabled) can supplement this — this skill's check is a fast spot-check, not a full WCAG audit.

### 6. Performance sanity

Animation count (2–4 meaningful ones is the ceiling, not a target to hit), any autoplay video/large images in the first render, unoptimized image dimensions. If real Lighthouse/CrUX data is available, note that lab data (Lighthouse, a single simulated run) and field data (real users, e.g. CrUX/Search Console) can disagree — a clean local Lighthouse score doesn't guarantee real-user performance, so prefer field data when both exist.

## Output format

No praise padding, no "but there are also good things" as a cushion — say plainly if the page is weak. Structure:

1. Findings by category (functional / first-screen / anti-slop / conversion / accessibility / performance), each with **exact location** (line number, selector, or screenshot region) and what's wrong
2. Group findings into a priority matrix, not a flat list:
   - **Critical (fix before shipping)** — broken functionality, dead links, CTAs that don't do what they say, content unreadable/missing on a real viewport
   - **High (fix next)** — conversion/trust gaps, clear anti-slop tells, accessibility failures
   - **Medium/Low (fix later)** — polish, nice-to-haves, minor consistency issues
3. One-sentence verdict: **ready to ship / needs revision / rebuild from scratch**

If the person then asks for fixes, apply them directly rather than re-describing the same findings as suggestions.
