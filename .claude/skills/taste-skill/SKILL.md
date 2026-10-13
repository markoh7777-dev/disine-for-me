---
name: taste-skill
description: "Consolidated frontend design-taste skill — merges 13 separate third-party skills (taste-skill, brutalist, minimalist, soft/agency, gpt-taste/GSAP, stitch, redesign, brandkit, image-first workflow, output-enforcement) into one non-contradictory system. Use for any landing page, portfolio, or marketing site build or redesign where the goal is a distinctive, non-templated result — code-level anti-AI-slop patterns (banned fonts/shadows/gradients/layouts), named aesthetic presets (brutalist, minimalist, soft-premium, bento/GSAP), and a detailed audit checklist for upgrading existing sites. Complements modern-web-design (conversion/authenticity strategy) and ui-ux-pro-max (the rule database) — this skill is the concrete code-pattern layer: specific hex values, Tailwind classes, font names, spacing numbers."
---

# Taste Skill (Consolidated)

This merges 13 separate skills from one archive into one system, because they overlapped heavily (most banned the same fonts/shadows/gradients) and in a few cases actively disagreed. Where sources disagreed, this file states which won and why — don't reintroduce the losing rule.

## 0. Brief inference — read before anything else

Before touching code, infer: page kind (landing / portfolio / redesign / editorial), vibe words the person used, any reference URLs/screenshots/named competitors, the audience, existing brand assets, and quiet constraints (accessibility-first, regulated industry, trust-first commerce — these override aesthetic preference).

State a one-line **Design Read** before generating: *"Reading this as: [page kind] for [audience], with a [vibe] language, leaning toward [aesthetic family]."* If genuinely ambiguous, ask exactly one clarifying question — never a multi-question dump. If you can infer confidently, don't ask.

## 1. The three dials

Set these after the design read — they gate every layout/motion/density decision downstream:

- **VARIANCE** (1 = perfect symmetry → 10 = artsy chaos)
- **MOTION** (1 = static → 10 = cinematic/physics)
- **DENSITY** (1 = art-gallery airy → 10 = cockpit/packed)

| Signal | VARIANCE | MOTION | DENSITY |
|---|---|---|---|
| minimalist / calm / editorial / Linear-style | 5–6 | 3–4 | 2–3 |
| premium consumer / Apple-y / luxury / brand | 7–8 | 5–7 | 3–4 |
| playful / Dribbble / Awwwards / experimental | 9–10 | 8–10 | 3–4 |
| landing/portfolio/marketing (default) | 7–9 | 6–8 | 3–5 |
| trust-first / public-sector / regulated | 3–4 | 2–3 | 4–5 |

The named presets in Section 3 are pre-tuned dial combinations with specific hex/font/spacing values — pick the closest preset to your dial reading rather than improvising from zero.

## 2. Universal banned defaults

This list is deduped from 6 of the 13 source skills, which independently converged on nearly the same bans — treat that convergence as signal, not repetition.

**Typography:** Inter, Roboto, Arial, Open Sans, Helvetica as the only/default face. Use fonts with character instead: `Geist`, `Outfit`, `Cabinet Grotesk`, `Satoshi`, `Clash Display`, `Plus Jakarta Sans`. Only Regular+Bold weights used — add Medium/SemiBold for hierarchy. Title Case on every header — use sentence case. Orphaned single words on the last line — fix with `text-wrap: balance`.

**Color:** purple/blue "AI gradient" mesh — the single most common AI fingerprint. Pure `#000000` backgrounds — use off-black (`#0a0a0a`, `#121212`). More than one accent color — pick one. Oversaturated accents above ~80% saturation. Generic flat `box-shadow` in pure black — tint shadows to the background hue.

**Layout:** three equal-width feature cards in a row — the most generic AI layout, replace with asymmetric/zig-zag/masonry. Everything centered and symmetrical. `height: 100vh` for full-screen sections — use `min-height: 100dvh` (iOS Safari viewport bug). No max-width container on wide screens.

**Icons:** Lucide/Feather/standard Heroicons as the only set — these read as the default AI choice. Rocketship for "Launch," shield for "Security" — reach for a less obvious metaphor. Inconsistent stroke widths across an icon set.

**Motion:** default `linear`/`ease-in-out` transitions, or none at all — use custom cubic-beziers. Animating `top`/`left`/`width`/`height` — animate only `transform`/`opacity` (GPU-safe, and the only properties that stay smooth). `window.addEventListener('scroll')` for reveals — use `IntersectionObserver`.

**Content:** "Elevate," "Seamless," "Unleash," "Next-Gen," "Game-changer," "Delve," "In the world of…" — write plain, specific language. Lorem Ipsum. Fake round numbers (`99.99%`, `50%`) — use organic messy data (`47.2%`). Generic placeholder names ("John Doe," "Acme Corp"). Cheap meta-labels ("SECTION 01," "QUESTION 05"). Emojis anywhere in UI copy or code — use real icons.

**Code:** div soup — use semantic HTML (`nav`, `main`, `article`, `aside`). Dead `href="#"` links. `window.alert()` for errors. Arbitrary `z-index: 9999` — use a defined scale. Missing alt text.

## 3. Named aesthetic presets

Pick one per project and commit — don't blend two in the same interface. Each is a complete, internally-consistent system (colors + type + spacing + one signature technique).

### Brutalist (industrial / tactical)
Two sub-modes, pick one, never mix: **Swiss Industrial Print** (light: bg `#F4F4F0`, ink `#050505`, single red accent `#E61919`, heavy Neo-Grotesque display type at `clamp(4rem,10vw,15rem)` with tight/negative tracking) or **Tactical Terminal** (dark: bg `#0A0A0A`, phosphor-white text `#EAEAEA`, same red accent, monospace-dominant). Zero border-radius anywhere — 90° corners only. `display: grid; gap: 1px` with contrasting parent/child backgrounds for razor-thin dividers instead of border declarations. Signature: ASCII framing (`[ DELIVERY SYSTEMS ]`, `>>>`) and ID-plate metadata (`REV 2.6`, `UNIT / D-01`) used as real structural elements, not decoration.

### Minimalist (warm editorial)
Warm bone background (`#F7F6F3`/`#FBFBFA`), off-black text `#111111`/`#2F3437` (never pure black), pale desaturated pastel accents only (e.g. pale blue `#E1F3FE` / text `#1F6C9F`). Editorial serif for hero headings (`Newsreader`, `Playfair Display`, `Instrument Serif`) at tight tracking (`-0.02em` to `-0.04em`) paired with a geometric sans body. Cards: `1px solid #EAEAEA`, max `12px` radius, shadows near-invisible (opacity < 0.05). Bento grids for feature sections. Motion is closer to invisible than punchy — `translateY(12px)` fade-ins over 600ms, nothing louder.

### Soft / premium agency
Three vibe sub-modes: **Ethereal Glass** (SaaS/tech: OLED black `#050505`, glowing mesh gradients, heavy `backdrop-blur-2xl`), **Editorial Luxury** (lifestyle/agency: warm cream `#FDFBF7`, variable serif headings, subtle film-grain overlay), **Soft Structuralism** (consumer/portfolio: silver-grey/white, bold grotesk, heavily diffused ambient shadows). Signature technique: the "double-bezel" nested card — an outer shell (subtle bg, hairline ring, large radius) containing an inner core with its own inset highlight and a mathematically smaller radius (`rounded-[calc(2rem-0.375rem)]`), so containers read as machined hardware rather than a flat div. Buttons are pills with a trailing icon nested in its own circular sub-wrapper, never sitting bare next to the label. Section padding is heavy — `py-24` to `py-40` minimum.

### Bento / GSAP-heavy (AIDA structure)
For pages that lean into motion as the main differentiator. Structure the page as Attention (cinematic hero, H1 capped at 2–3 lines via a wide container — `max-w-5xl`+, never a narrow column that wraps to 5–6 lines) → Interest (bento grid, `grid-auto-flow: dense` so no cell is ever empty, 3–5 intentional cards beats 8 messy ones) → Desire (GSAP ScrollTrigger: pin one element while a gallery scrolls past it, or scale/fade images as they enter and exit view) → Action (large high-contrast CTA + footer). Huge inter-section padding (`py-32` to `py-48`) so sections read as distinct chapters.

## 4. Redesign / audit protocol

When applied to an *existing* project: **scan** the codebase (framework, styling method, current patterns) → **diagnose** against the checklist below → **fix** by working with the existing stack, not a rewrite.

Beyond the banned-defaults in Section 2, check specifically for:
- **Alignment drift**: buttons not bottom-aligned across cards of different content length; feature lists starting at different Y-positions in a pricing table; misaligned baselines across side-by-side columns
- **Missing states**: no hover/active feedback, no visible focus ring (accessibility requirement, not optional), no loading/empty/error states, no current-page indicator in nav
- **Flat, undifferentiated cards**: border+shadow+white-bg on every card regardless of whether elevation communicates real hierarchy — remove it where it doesn't
- **One dark section dropped into an otherwise light page** (or vice versa) — reads as a copy-paste accident; commit to one mode or step contrast gradually within the same palette family

**Fix priority (highest impact, lowest risk first):** 1) font swap, 2) color palette cleanup (one accent, one gray family), 3) hover/active states, 4) layout/spacing/max-width, 5) replace generic components (3-card testimonial carousel, sun/moon toggle, 4-column footer farm), 6) loading/empty/error states, 7) typographic scale polish.

Rules while redesigning: don't migrate frameworks or styling libraries to do this. Don't break existing functionality — test after every change. Check the dependency file before importing anything new. Small, targeted, reviewable diffs over a big rewrite.

*(This overlaps with the separate `site-audit` skill, which focuses on functional QA and conversion/CRO rather than CSS-pattern-level fixes — run both if doing a full pre-launch pass; they check different things.)*

## 5. Design-spec-first technique (optional)

Before writing code, optionally produce a short `DESIGN.md`: visual theme/atmosphere in one paragraph, color palette with named roles (not just hex), type rules, component styling, layout principles, motion rules, and an explicit anti-patterns list for this specific project. Writing the spec first catches contradictions (e.g. "premium AND playful AND dense") before they show up as inconsistent code, and gives a stable reference to hold the build to across a long session.

## 6. Brand asset direction (condensed)

When the deliverable includes a logo/brand system rather than just a page: start from brand strategy (what the mark needs to communicate), not from a style keyword. Logo concept families to choose from: monogram+meaning, product-action mark, metaphor fusion, negative-space trick, construction-geometry mark. Match visual mode to sector rather than defaulting to one look — e.g. dark/terminal for dev tools, warm editorial for compliance/trust-first, dark nature for calm/wellness. Keep text rules and tagline style consistent with whichever mode is chosen; don't mix a luxury serif wordmark with a terminal-mono tagline.

## 7. Image-first workflow (optional, requires an image-generation tool)

Three of the source skills (image-to-code, imagegen-frontend-web, imagegen-frontend-mobile — ~3,700 lines combined) describe generating standalone reference images *before* writing code: one full-resolution image per page section (never one compressed board for the whole page), regenerated fresh rather than cropped from old images, deeply analyzed before implementation. Core discipline worth keeping even without their tooling: don't crop/reuse one hero image to represent multiple sections, and don't skip straight from a vague text brief to code — a concrete visual reference (generated or found) beats a text description every time.

This workflow assumes a dedicated image-generation tool, which is not currently in this environment's toolset (only image *search* is available, which finds existing web images rather than generating new ones). Treat this section as dormant guidance rather than an active step until such a tool is connected — at that point the full source files in the original archive have the detailed prompt engineering for it.

## 8. Output completeness (unrelated to aesthetics, keep regardless of preset)

Treat every task as production-critical — a partial output is a broken output. Never use `// rest of code`, `// ... implement here`, `// similar to above`, or prose like "I can continue if needed" as a substitute for finishing. Before responding: count how many distinct deliverables were requested, lock that number, and cross-check the output against it before sending.

If a response would run out of room, don't compress the remaining sections to fit — finish the current section at full quality, then stop at a clean breakpoint and say explicitly what's done and what's next, rather than silently truncating.

## 9. Pre-flight check

- [ ] Design Read stated in one line before generating
- [ ] Dials set and a named preset chosen (or explicit reason for a custom combination)
- [ ] Nothing from the Section 2 banned list appears
- [ ] Only one aesthetic preset is active — no blending brutalist with soft-glass, etc.
- [ ] Layout collapses to a clean single column below 768px, no overlap/rotation artifacts carried to mobile
- [ ] All motion is `transform`/`opacity` only, `prefers-reduced-motion` respected
- [ ] If this was a redesign: fix-priority order followed, existing functionality still works
- [ ] Output is complete — no placeholder comments, no "continues in the same pattern"
