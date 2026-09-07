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

## 2026-09-07 — Update freelance experience record with detailed copy

**docs(profile)**

Expanded `src/experiences/senior-full-stack-engineer-agentic-development-self-employed/README.md` with the user-provided freelance copy: added Location (Bucharest, Romania), moved the two spec-first/agentic-workflow items (now verbatim, with their expanded wording) into Achievements & Highlights, and added three verbatim Responsibility bullets (directing AI coding agents, continued hands-on Vue/Nuxt · React/Next · Node.js work, and the new "Working on Swift projects, extending into native mobile development" bullet). Summary replaced with the user's exact sentence; Technologies kept as-is (Swift/iOS are known registry gaps, not added). Root README experience-index line enriched with the location (Bucharest, Romania). Period kept as `2026-02 – Present` per the experience spec's YYYY-MM format rather than the user's "8 mos" duration.

```text
link check: https://lyralabs.space → 200 OK
verification: manual diff review against specs/experience.md template (no project lint/typecheck scripts apply to markdown-only change)
```

---

## 2026-09-07 — Set canonical skill list for freelance experience and registry

**docs(profile)**

Replaced the freelance experience record's Technologies section with the 11 user-specified canonical skill names (Agentic Workflows, Agentic AI Development, Node.js, React.js, Vue.js, Next.js, Nuxt.js, MongoDB, GreenSock Animation Platform (GSAP), Three.js, Swift (Programming Language)). Registered the genuinely-new canonical names in the root README Tech Stack as plain-text bullet groups (React.js/Vue.js/Next.js/Nuxt.js under Frontend, Node.js/MongoDB under Backend, new Motion & 3D, Native & Mobile, AI & Agentic Development groups); skillicons icon rows preserved untouched. Other records left as-is (consistency sweep found no direct contradictions). Verified all README relative links resolve.

---

## 2026-09-07 — Refine canonical skill naming rules for parentheticals and prose

**docs(specs)**

Refined the canonical skill registry rules across the specs so they stay coherent with the extended root README Skills / Tech Stack registry:

- `specs/career-profile.md` (Canonical skill registry): added that canonical names are used exactly as registered, including any parenthetical qualifier (e.g. "GreenSock Animation Platform (GSAP)" — the parenthetical is part of the name, not an alias); that category groups are README presentation and may evolve without changing canonical names; and a one-line structured-lists-vs-prose rule (exact canonical names in structured lists, recognized short forms like GSAP/Swift tolerated in prose).
- `specs/experience.md` / `specs/project.md`: skill-naming sections now require the exact registered name including parentheticals in the Technologies/Tech Stack lists, and allow recognized short forms in prose; template comments updated to match.
- `specs/README.md`: governance line touched up for coherence (structured lists exact, prose tolerant).

No registry contents enumerated in specs; README remains the sole registry. Relative links verified to resolve.

Verification: link check across edited specs — all real links resolve (only template placeholders/examples flagged, pre-existing). `git diff` reviewed.

Committed as docs(specs): no code or career-data files touched.

---

## 2026-09-07 — Expand career-break record and reorder README sections

**docs(profile)**

Expanded the career-break record with user-provided copy (title "Career break", employment type Career break, Bucharest location, Dec 2025 – Feb 2026, new summary, bullets mapped to Responsibilities/Achievements, added lyralabs.space associated-project link). Reordered root README sections to About Me → Tech Stack → What I Do → Experience → Projects → Education (remainder unchanged). Experience index already sorted most-recent-first — verified, no changes needed. Languages section is absent in README; not invented per instructions.

---

## 2026-09-07 — Add Languages, expand Education, register full canonical skill vocabulary

**docs(profile)**

README.md: added a Languages section (English — Professional working proficiency; Persian — Native or bilingual proficiency) after Education. Replaced the one-line Education summary with a detailed list (M.Sc. Computer Software Engineering 2019–2021 Grade 14; B.Sc. Information Technology 2014–2018 Grade 16.45, both Azad University (IAU)). Expanded the Tech Stack into the full canonical skill registry of 63 entries across 10 category groups (Frontend, Backend, State Management, Testing, Motion & 3D, Mobile & Desktop, AI & Agentic Development, Architecture & Practices, IT & Infrastructure, Tools & Workflow), skillicons rows intact. Normalized "Front-end Development" → canonical "Front-End Development" to match "Back-End Development" (user had supplied both casings; registered once). "ReduxTK" kept verbatim per user spelling.

Validation: all 63 registry names verified present exactly once via exact-line grep; relative links resolve; no stale "Native & Mobile"/"Front-end Development" leftovers; no JSON/YAML registry.

---

## 2026-09-07 — Overhaul experience records with detailed career history

**docs(profile)**

Rewrote all experience records with the user-supplied verbatim copy: full summaries, employment type, location, responsibilities/achievements, and complete Technologies lists. Updated 7 existing records (MiroTech, freelance self-employed, Danak CTO, Danak full-stack, Danak frontend, Termeh internship) and created 4 new ones (career-break-foundations-2016-2017, computer-repair-technician-negaran-fard, computer-repair-technician-pishro-computer, computer-technician-internship-farhikhteh-negar). Rebuilt the README Experience index most-recent-first (Feb 2026 → Jul 2014) with one-line summaries. Registry-first: added `Git` to README Tech Stack (Tools & Workflow). Kept the existing 2025-12–2026-02 career-break record untouched. Verification: all README↔record and record↔project relative links resolve; every Technologies entry matches the canonical registry (known casing variants "Front-end Development" vs "Front-End Development" retained verbatim per user instruction).

---

## 2026-09-07 — Remove incorrect Asan Service project record

**docs(profile)**

Deleted src/projects/asan-service-arak-provincial-government-portal/ (user stated the project is incorrect; corrected project list to follow). Removed the 🏛️ entry from the README Projects index and the broken Associated Projects link (and now-empty section) in src/experiences/full-stack-developer-self-employed/README.md. The verbatim experience bullet mentioning Asan Service is retained.

Verification:
- `grep -rin "asan-service"` (excluding .git, node_modules, .opencode): zero remaining references outside CHANGELOG.md history entries.
- Remaining "asan" text is the user's verbatim experience bullet only; no links to the deleted project remain.
- Relative-link check across README.md and the experience record: no broken links; README Projects index still links the other 7 projects.

---

## 2026-09-07 — Replace project dataset with detailed project records

**docs(profile)**

Deleted all 7 old project record directories and created 33 new per-project records from the user's detailed project list (user split everything explicitly; bundling exception not applied). Each record: Summary verbatim as short description + overview, period in YYYY(-MM) format, role when given, company relationship, Tech Stack from the user's Tech Stack line with canonical registry spellings (render-mode qualifiers kept as parentheticals, e.g. "Nuxt3 (SSR)"), Related Experience link. Rebuilt README project index grouped by employer (MIROTECH GROUP 13, Freelance 1, Danak 18, Termeh 1); refreshed Associated Projects in 6 experience records; removed broken lyralabs-space project links from career-break record (prose mention kept); registry additions: WebSocket, PHP (Laravel), PHP, Python, MySQL, React Native, Firebase.

Period-to-experience mapping: MiroTech projects → mirotech record; dLabel (2021-05 – 2021-07) → full-stack-developer-self-employed; Danak "2020 – 2021" → CTO + Full-Stack (both); "2021"/"2020"/"2019 – 2020" → CTO or Full-Stack per overlap; "2018 – 2019" (Mod Star) → Frontend + Full-Stack; Aug–Nov 2018 (MSA, Tabesh) → Frontend + Full-Stack; Mar–Jul 2018, Feb–Apr 2018, Jan 2018 → Frontend; Termeh Soft → Termeh internship. Note: lyralabs.space and the native-mobile iOS learning project were omitted from the user's list and are gone from the repo.

Validation: all README/experience/project cross-links resolve both ways, no orphans, no stale references to deleted slugs, every Tech Stack name exists in the README canonical registry, periods use YYYY(-MM).

---

## 2026-09-07 — Simplify README header

**docs(profile)**

User-edited README.md committed as-is: merged the greeting line into a single centered H1 (headline only), dropping the "Hi 👋 I'm Amir" greeting line. No other changes.

---

## 2026-09-07 — Enrich project records with ownership and engineering stories

**docs(profile)**

Enriched 13 existing project records and created 2 new ones with user-sanctioned facts: ownership/engineering stories (Tadilo near-total frontend ownership + real-time incremental WebSocket search + chunked rendering + SSR Docker fix; Terminal101 B2B framing; MiroPay panels leadership framing, removed "similar to PayPal"; Booking ERP leadership framing; dLabel Project Manager redesign; Asan Service solo full-stack + internal-system integration; Easybestell ecosystem + Electron printing-bridge contribution; Arak Rail engineering calculator with structural validation; Tabesh/Persia Art/Doshell/Barg UI-and-motion emphasis). Created lyralabs-space (Three.js splash, GSAP, Agentic Workflows) and native-ios-qr-code-generator (Swift, SwiftUI — registry-first). Added SwiftUI to README Mobile & Desktop registry; added Personal project-index group; updated MiroPay/Doshell/Arak Rail one-liners. Restored Associated Projects links in career-break and freelance-agentic records. Link check: all relative links resolve, no stale references.

---

## 2026-09-07 — Light overview cleanup for remaining project records

**docs(profile)**

Each of the 15 remaining un-enriched project records had an Overview that was a verbatim repetition of the one-liner under the heading. Rewrote each Overview minimally using only facts already canonical in the record (relationship/employer, role, tech stack) — no invented impact, features, or ownership:

- arak-provincial-government-portal, arak-provincial-government-vcm, danak-corporation-website: added Danak client-work context + stack summary (Nuxt SSR/SPA + Express/MongoDB/REST)
- asan-service-mobile-app-v1: Danak client-work context + React Native/Redux summary
- negareh-agency, msa-landing-page, vcv, rashin-protein: Danak client-work context + Vue (SSG/SPA) summary
- dorsa-morq: Danak client-work context + PHP-site modifications/JS-features framing (from role)
- termeh-soft: Termeh internship context + PHP (Laravel)
- nuwa-coin, offense-coin, dassfund, dassfund-erp, pahlawan-webview: MIROTECH GROUP context + stack/relationship summary

Left unchanged: miropay-staff-panel — its Overview already carries full leadership framing, no verbatim repetition. All metadata, tech stacks, links, and periods preserved; no new skills; all relative links verified resolving.

Verification: link-resolution check across all 15 touched records (18 relative links, all OK); git diff review (15 files, 1-line Overview change each).

---

## 2026-09-07 — Remove GitHub Stats section

**docs(profile)**

Removed the GitHub Stats section from README.md (both github-readme-stats widget images and the section heading). No other changes.

---

## 2026-09-07 — Replace What I Do with Engineering Profile

**docs(profile)**

Replaced the "🔥 What I Do" bullet list in README.md with a new "Engineering Profile" section containing the user-provided three-paragraph narrative. No other changes.

---

## 2026-09-07 — Compact two-tier Tech Stack presentation

**docs(profile)**

Replaced README's ~100-line Tech Stack section (icon rows + 10 bullet groups) with a 22-line two-tier layout:

- Tier 1 "Primary Stack": one row of shields.io badges (icon+label in one badge) for Vue.js, Nuxt.js, React.js, Next.js, Node.js, TypeScript, MongoDB, GSAP. Chose badges over skillicons icon rows because they combine icon and label in one element and render consistently on GitHub desktop and mobile; GSAP chosen over Three.js for the visual-specialization slot.
- Tier 2 "Complete Technical Skills": a compact | Area | Technologies | Markdown table with 10 rows using "·" separators.

All ~63 canonical skill names (verified across 72 canonical name strings) remain present exactly once — nothing removed, renamed, or added. The skillicons icon rows (which also covered css/sass/vite/webpack/vscode/github icons without text entries) were dropped as presentation-only; no new canonical skills were introduced for them. Section heading "## 🛠️ Tech Stack" kept.

Verification: grep-count check of every canonical name (0 missing); shields.io badge URLs return HTTP 200; section length reduced 100 → 22 lines; no skillicons references remain.

---

## 2026-09-07 — Remove Engineering Focus section

**docs(profile)**

Removed the "🧪 Engineering Focus" section (heading + 4 bullets) from README.md. No other changes.

---
