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
