# Changelog

Append-only — never read, never rewritten.


## 2026-09-07 — Career profile authoring specs

**docs(specs)**

Added the specs/ directory defining how this career repository is organized and how future career content must be authored:

- `specs/README.md` — purpose of the specs, which file governs which content type, and the rules-vs-data split (specs contain rules; README + src/ contain career data).
- `specs/career-profile.md` — repository-wide invariants: root README responsibilities (public landing page + canonical index, canonical profile-level info), `src/experiences/` and `src/projects/` responsibilities, source-of-truth (canonical vs derived), linking, slug naming, asset, duplication, and public-data rules, unknown/missing-information handling, update procedure for future agents, and consistency expectations. Includes the required statements: canonical facts exist in one authoritative location, and derived outputs (CVs, portfolio copy, LinkedIn content, exports) must not silently overwrite canonical facts.
- `specs/experience.md` — exact template + authoring rules for experience records (`src/experiences/<slug>/README.md`), required vs optional fields, project referencing via links (no duplication), and the experience/root-README/project ownership split.
- `specs/project.md` — exact template + authoring rules for project records (`src/projects/<slug>/README.md`), required vs optional fields, asset placement (`assets/` only when assets exist) and relative linking, experience cross-referencing, and the project/experience ownership split.

Verification: all real cross-links between the four spec files resolve (checked with a link loop); line counts 26/128/95/117; the two flagged `assets/dashboard.png` matches are inline-code template examples, not links.

Next: `coder` restructures the repo into README.md + specs/ + src/experiences/<slug>/README.md + src/projects/<slug>/README.md per these specs.

---

## 2026-09-07 — Restructure career profile into specs + src architecture

**docs(profile)**

Restructured the repository per specs/ into a root README (public landing page + canonical index) plus a `src/` tree: 8 experience records under `src/experiences/<slug>/README.md` (both Danak roles, both freelance periods, MiroTech lead, career break, Termeh internship) and 8 project records under `src/projects/<slug>/README.md` (Tadilo, Terminal101, MiroPay & Dassfund ERP, Booking ERP & Easybestell, dLabel, Asan Service & Arak Government Portal, lyralabs.space, native-mobile-ios). Root README keeps presentation content verbatim (header, badges, stats, contact), carries canonical profile-level facts, and links records with concise one-line summaries. Full descriptions live only in records; cross-links are two-way. Added .gitignore (.DS_Store, .opencode/). No career facts invented; sparse fields omitted per specs.

Validation: script-checked all relative links resolve (README→records, records↔records), no orphan index entries, no asset references (none exist), 8/8 experiences and 8/8 projects linked both ways.

---

## 2026-09-07 — Refine About section wording

**docs(profile)**

Minor About-section edit in README.md: added a comma in "Today, I build and use" and split the closing sentence into its own paragraph ("Based in Bucharest…" / "Open to full-time, contract, and freelance opportunities."). No factual changes.

```text
git diff --stat: README.md only, clean tree after commit
```

---

## 2026-09-07 — Spec consistency fixes from structure audit

**docs(specs)**

Auditor findings applied to specs/ only (no src/ or README.md changes):

- **Bundling exception (medium):** specs now explicitly allow a project record to bundle closely related projects when the source treats them as a single line of work and splitting them would require invented facts (covers `miropay-dassfund-erp`, `booking-erp-easybestell`, `asan-service-arak-provincial-government-portal`). Bundled records use a hyphen-joined slug and keep member facts internally separated. Added a dedicated section to `career-profile.md` and an exception clause in `project.md`'s rules recap.
- **"Copy verbatim" contradiction (low):** template preamble in `experience.md` and `project.md` rephrased — the template is a skeleton; required fields included, optional sections omitted when unknown.
- **Garbled sentence (low):** `experience.md` end-date rule rewritten to "Use `Present` for current roles; for a known start with an unknown end, write only the start (e.g. `2022-04 –`)."
- **CHANGELOG gap (low):** `career-profile.md` content-types table now lists `/CHANGELOG.md` as a workflow/bookkeeping artifact outside the career-data rules.
- **specs/README.md:** added a note that this specs/ layout is domain-specific authoring rules, not the spec-kit feature-spec layout.

Verification: all spec-to-spec markdown links resolve; flagged links are pre-existing inline code examples. Out of scope (coder): Native Mobile casing, terminal101 redundancy in src/.

---

## 2026-09-07 — Canonical skill registry rule

**docs(specs)**

Introduced the canonical skill registry rule across the specs so skill/technology names never drift in spelling across the repository (e.g. "Next.js" vs "NextJS" vs "next.js").

- specs/career-profile.md: new "Canonical skill registry" section — root README Skills / Tech Stack is the single canonical registry; exact-name rule everywhere; no second machine-readable skill database; repetition over IDs/pointers; mandatory registry-first workflow for new skills; renaming and removal rules; category guidance; vocabulary flow. Added a consistency expectation covering skill-name consistency.
- specs/experience.md: canonical-name requirement on the Technologies section, a "Skill naming" note near the template, and a rules-recap line.
- specs/project.md: same treatment for the Tech Stack section.
- specs/README.md: governance table and rules-vs-data note now mention the canonical skill registry so the invariant is discoverable.

Verification: relative links in edited spec files resolve to existing files; `git status` shows only the four spec files modified; data files (README.md, src/**) untouched.

---

## 2026-09-07 — Normalize skill names to canonical registry

**docs(profile)**

Validated all skill/technology names across README.md and src/** against the canonical registry (root README Skills / Tech Stack).

Normalized (certain equivalence):
- "Vue.js" → "Vue" in README.md experience index and src/experiences/frontend-developer-danak-corporation/README.md Technologies (registry icon is `vue`; README prose uses Vue/Nuxt).
- "- Vue / Nuxt" → "- Vue/Nuxt" and "- React / Next" → "- React/Next" in src/experiences/full-stack-developer-self-employed/README.md, src/experiences/senior-full-stack-engineer-agentic-development-self-employed/README.md, src/projects/tadilo-b2c-booking-platform/README.md — matching the README's dominant unspaced "Vue/Nuxt" / "React/Next" shorthand.

Left unchanged (ambiguous):
- The "React/Next" and "Vue/Nuxt" shorthand form itself — used consistently in prose everywhere; expanding it would restructure lists, not normalize spelling.

Registry gaps (reported, not fixed):
- In records but absent from README Tech Stack: Swift, iOS (native-mobile-ios), PHP (full-stack-developer-danak-corporation).
- Referenced in README prose/indexes but absent from Tech Stack registry lists: GSAP, Motion, Tailwind, Stripe, Vitest, Playwright.

Verification: re-scan for Vue.js/VueJS/NextJS/NodeJS/GreenSock/"Vue / Nuxt"/"React / Next" returns no matches. No JSON/YAML registry introduced.

---
