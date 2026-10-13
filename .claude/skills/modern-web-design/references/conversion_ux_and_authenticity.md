# Conversion UX & Authenticity Guide

Practical, field-tested rules distilled from CRO/usability case studies (heatmap-backed) and design-critique content. Two goals this reference serves:

1. **Conversion UX** — first-screen effectiveness, CTA design, trust signals, content depth.
2. **Authenticity / Anti-AI-Slop** — the visual and code-level tells that make a site read as unreviewed AI output, and how to avoid them.

Read this alongside `design_trends_2024.md` (aesthetic trends) and `interaction_patterns.md` (micro-interactions) — this file is the conversion-and-credibility layer, not a replacement for either.

---

## 0. Discovery — before any design decision

Skipping this step is the single biggest cause of generic output. There is no universal "ideal" landing page template; copying a competitor's block structure without this step reliably produces low conversion.

1. **Audience research**: what does the target user actually search for / complain about? If no customer list exists, mine forums, review sites, and search-suggest data. Negative reviews are the richest source of objections.
2. **Competitor matrix**: list direct competitors, check how each addresses the audience's needs — gaps here become the USP.
3. **Needs → Block matrix**: for every audience pain/objection, define which product feature answers it, and which page block communicates that. If a block doesn't map to a real objection, cut it.
4. **Block order**: sort sections top-to-bottom by descending importance of the need they answer — never by arbitrary/aesthetic order.

## 1. The first screen (3–5 second rule)

Within 3–5 seconds a visitor must know: where they landed, whether the offer is relevant, whether they'll get an answer to their need. ~95% of visitors on cold/paid traffic do not scroll past the first section — so the offer, headline, and primary CTA carry almost the entire conversion burden.

- Write the headline/subheadline in plain audience language. No metaphors, no withheld details, even if that costs some visual elegance.
- Cold traffic does not reliably use a search bar or jump straight to "Get Started" — many will scan the header nav first (About/Services/Reviews) looking for context. If the audience is cold, give them that context on the first screen, not just a CTA.
- Split long headlines into a short punchy line (3–5 words) + a detail subheadline, rather than one dense 4–5 line block.
- Visual card grids of real content (destinations, categories, products) reliably out-convert a bare search bar or text-only CTA on a first screen — people click pictures more readily than they type.

## 2. CTA & buttons

- **Contrast is the whole game.** A clickable element that looks the same as a non-clickable info chip will not get clicked, no matter how good the copy is. Buttons must be unmistakably interactive.
- Reserve the accent color **exclusively** for the CTA and the highest-priority interactive elements (rule of 60-30-10: dominant neutral 60%, secondary 30%, accent 10%). If the accent color also appears in headings, menu items, or borders, it stops functioning as a signal.
- Button label: 1–2 words, imperative, concrete ("Get a quote", "Book now"). Long sentence-length CTAs read as heavy and hurt click-through.
- Button text size: keep to 14–18px regardless of button size — oversized text inside a button looks cheap and does not improve conversion.
- For services where users have split channel preference (call vs. chat vs. book online), offer 2–3 explicit entry points on the first screen instead of a single CTA — different users commit through different channels.
- Case-study / portfolio cards convert far better when they carry a **concrete metric** ("+30% ROI") next to the CTA, not just an aesthetic preview.

## 3. Typography

**Pairing (safe → expressive):**
- Safest: one family, two weights (e.g. Bold headline + Light/Regular subhead) — near-zero risk of clashing.
- Classic contrast: serif headline + sans-serif body (or vice-versa) signals editorial/premium; pure sans-serif pairings read as SaaS/utility.
- Differentiate heading vs. subheading by **both** size and weight and color (e.g. subheading in Regular/Medium + a softer gray, not pure black) — same-weight same-color stacks are hard to scan.
- Decorative/handwritten fonts: 1–3 words only, headlines/badges. Never body copy.
- Law of proximity: subheadline sits close to its headline (~25px), with a larger gap (~40px) before the next unrelated block — large gaps between related elements make them read as disconnected.
- Keep one consistent type scale across the whole page — same H2 size/line-height everywhere, not 48px in one section and 36px in the next.

**Color palette:**
- Never use pure/maxed-saturation hex values (`#FF0000`, `#0000FF`). Pull saturation and brightness in one or two notches from the wheel's edge — this alone makes a palette look considered rather than default.
- Building a palette by hand: don't just raise Brightness for tints — walk the point along an arc, nudging Hue slightly warmer as it lightens; for shades, nudge Hue slightly cooler/toward burgundy as it darkens. A flat brightness-only ramp looks synthetic.
- White text is the only acceptable body-text color on dark backgrounds — dark-gray-on-dark is a contrast failure, not a stylistic choice.
- Text over a busy photo needs a 30–60% overlay or blur, or gets moved onto a solid chip — never placed raw.
- Pick the base hue from the niche/brand, not from what "looks nice": eco/organic → green/natural tones; premium/tech → dark, restrained minimalism.

## 4. Composition & layout

- Every element in a text/CTA group anchors to one guide line (left edge or center) — mixed indentation is one of the fastest ways to look unpolished.
- Classic Z/F scanning patterns are a floor, not a ceiling — modern layouts often build around a **central visual anchor**, with the eye starting mid-screen rather than top-left. Direct attention through visual weight (size/contrast/position), not just grid position.
- If the hero's dominant element is a video or 3D object, keep accompanying text visually lighter (smaller, less bold) — don't let text compete with the primary media for the first glance.
- In visually loud/colorful layouts, size and color contrast stop working as attention tools — use motion/micro-animation instead to force the eye to the target element.
- Layered technique for a hero section: (1) set the eye's geometric path → (2) set size-based emphasis (headline > photo > body) → (3) reserve one accent color for the final action → (4) add micro-animation on the interactive element to lock attention there.
- Soft, diffuse shadows only: push blur radius up, drop opacity to 5–15%, use a color close to the background. Tight, dark, high-opacity shadows read as amateur.
- One icon style for the entire project (pick line-weight, fill or outline, and stick to it site-wide) — mixed icon styles break visual coherence fast.
- One border-radius / stroke-weight system for the whole page — cards, buttons, and inputs should share the same rounding logic.

## 5. Content depth by decision type

Match text volume to how the audience actually decides:
- **Impulse / low-consideration** (attention span ~1–2 seconds): cut ruthlessly, minimal copy, one clear path.
- **High-consideration / B2B / high ticket**: do *not* shorten. These audiences need depth — detailed sections, downloadable specs/presentations, and explicit objection-handling before they'll convert.

## 6. Trust signals

- Plain-text testimonials are low-trust (trivially fabricated). Highest-converting social proof links to a real, checkable identity (a clickable profile) or ties to verifiable numbers.
- Real photography of the actual product/team/process consistently outperforms stock photography or abstract illustration for trust — this is true even when the real photos are less polished.
- Avoid recognizable stock-photo tropes (the "thumbs-up businessman") — audiences have seen them too many times for the image to still signal anything.

## 7. Mobile specifics

- Collapse navigation into a hamburger/off-canvas menu on mobile — never let a desktop nav auto-wrap and push the offer below the fold.
- Keep nav items visually modest — if menu items compete in size with the H1 or the CTA, priority is wrong.
- Design mobile-first when the workflow allows it; if not, adaptivity testing must be an explicit final step before ship, not an afterthought.

---

## 8. Anti-AI-Slop Checklist

Two audiences use this checklist: run it against reference sites (to explain why something reads as "not template"), and — more importantly — run it against **your own output before delivering it**.

### Visual tells of unreviewed AI output

- [ ] Purple-to-blue glow gradients, neon accents — the model's default "soulless beauty." If nothing about the palette was chosen for the brand/niche, this is probably it.
- [ ] Hero built from the two default templates: (a) text-left / photo-in-rounded-mask-right, or (b) full-bleed darkened photo + centered white text. Both are instantly recognizable defaults — break the symmetry or change the crop instead.
- [ ] "Plastic" AI-generated people photos — overly symmetric, generically smiling, faint rendering artifacts. Use real photography, even if rougher.
- [ ] Every emphasis technique stacked on one element at once (fill + border + flat drop shadow simultaneously). Pick exactly one.
- [ ] A small CAPS-LOCK eyebrow label above the headline, usually with a stray dash or period — a very recognizable template tic.
- [ ] Headline wraps into ragged lines of uneven length instead of a deliberate rectangle; tighten line-height (~80–90%) and hand-break the lines.
- [ ] Whitespace that's just large and empty rather than doing hierarchy work — negative space should group/separate meaning, not fill space because "modern design has whitespace."
- [ ] Hover/scroll animation applied to everything uniformly, with no relationship to what it's drawing attention to ("animation because modern sites have animation").
- [ ] Literal arrow/checkmark characters (→ ✓) or keyboard emoji standing in for iconography — replace with a real vector icon set.
- [ ] Bullet-point dots (•) used to separate every few words inline — replace with spacing, a slash (/), or real punctuation.
- [ ] Any hallucinated numbers, broken/garbled characters, or placeholder-looking copy that was never proofread.

### Code-level tells (when writing the actual implementation)

- [ ] Emoji inside `console.log` / debug output (`console.log("🚀 done")`) — real production code doesn't do this.
- [ ] Comments that restate *what* a line does (`// send email` above `sendEmail()`) instead of *why* it exists. Delete restating comments; keep only comments that explain a non-obvious reason.
- [ ] Bloated implementations — 20 lines and three levels of nesting where 3 lines would do. Prefer the shorter, idiomatic solution.
- [ ] Decoration with no function: for every non-content visual element, ask "what does this communicate or do?" — if there's no answer, delete it.

### Prompting note (when generating with AI tooling)

Vague style instructions ("make it modern and minimal") reliably regress to the model's statistical average — which is exactly the generic look this checklist is trying to catch. Naming a **specific, concrete aesthetic reference** (a named style, era, or genre — not an adjective) produces sharply better, less generic results, and an attached image reference outperforms a text description of the same style every time.

---

## 9. Pre-delivery pass

Before calling a page done, walk both the CRO list (section 0–7) and the Anti-Slop checklist (section 8) against the actual output — not from memory, against what's on screen. If any anti-slop box is checked, fix it before delivery rather than noting it as a known issue.
