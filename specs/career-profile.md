# Career Profile — Repository-Wide Invariants

schema: 1

These rules apply to the entire repository. The per-record templates live in [`experience.md`](./experience.md) and [`project.md`](./project.md).

## Content types and where they live

| Content | Location | Responsibility |
|---|---|---|
| Root README | `/README.md` | Public landing page **and** canonical index of the repository. |
| Experience records | `src/experiences/<experience-slug>/README.md` | The full, authoritative record of one role/position. |
| Project records | `src/projects/<project-slug>/README.md` | The full, authoritative record of one project (bundled records allowed — see the bundling exception below). |
| Project assets | `src/projects/<project-slug>/assets/` | Media belonging to a project (only when assets exist). |
| CHANGELOG | `/CHANGELOG.md` | Workflow/bookkeeping artifact — outside the career-data rules. |
| Specs | `specs/` | Rules only — never career data. |

## Root README responsibilities

The root README is two things at once:

1. **Public landing page** — the first thing a visitor sees. It presents a concise, scannable profile.
2. **Canonical index** — it links into the repository's records so every experience and project is reachable from the root.

It carries the **canonical small profile-level information**:

- name
- professional headline
- location
- public links / contact
- About Me
- Skills / Tech Stack
- Languages
- Education
- concise experience index (one line per experience, linking to its record)
- concise project index (one line per project, linking to its record)

The root README must stay concise. Depth belongs in the records, not the landing page.

## `src/experiences/` responsibilities

Each `src/experiences/<experience-slug>/README.md`:

- is the **full, authoritative record** of one role or position (see [`experience.md`](./experience.md) for the template),
- holds everything known about that experience: dates, responsibilities, achievements, technologies, related projects,
- links to related project records rather than duplicating them,
- is referenced from the root README's experience index.

## `src/projects/` responsibilities

Each `src/projects/<project-slug>/README.md`:

- is the **full, authoritative record** of one project (see [`project.md`](./project.md) for the template),
- holds everything known about that project: description, role, contributions, tech stack, links, media,
- links to related experience records rather than duplicating them,
- is referenced from the root README's project index.

## Bundling exception (projects)

A project record MAY bundle closely related projects — but only when **both** hold:

1. the source material introduces or treats them as a **single line of work**, and
2. distinguishing them individually would require **inventing facts** the source does not provide.

Rules for bundled records:

- Name the directory with the slugs of all member projects joined by hyphens (e.g. `miropay-dassfund-erp`).
- Keep each member project's facts internally separated (its own name, description, role, period, links) — never blend them into one merged narrative.
- Apply this exception only to projects; experience records are always one role per directory.

## Source of truth: canonical vs derived

**Canonical facts must exist in one authoritative location. Other locations may summarize or reference them but must not become competing sources of truth.**

- Canonical locations:
  - profile-level facts (name, headline, contact, education, skills, languages) → root README
  - an experience's full details → its `src/experiences/<slug>/README.md`
  - a project's full details → its `src/projects/<slug>/README.md`
- **Derived information** is anything produced *from* canonical facts: summaries in the root README, generated CVs, portfolio copy, LinkedIn content, application answers, JSON exports, or any other format. These are **downstream outputs**.
- Derived outputs **must not silently overwrite canonical facts**. When a derived output and a canonical record disagree, the canonical record wins — fix the derived output, never the other way around.
- Derived outputs are not stored as canonical sources in this repository. If they are committed at all, they must be clearly marked as generated/derived and must never be treated as authoritative.

## Canonical skill registry

The root README's **Skills / Tech Stack** section is **THE canonical registry** of skills and technologies used anywhere in this repository. This is a repository-wide invariant, not a template recommendation.

- Every skill/technology referenced anywhere — root README, `src/experiences/**`, `src/projects/**`, and any future career records — must use the **exact canonical name** defined there: same casing and punctuation (e.g. one spelling of a framework, not several: `Next.js` vs `NextJS` vs `Next JS` vs `next.js`).
- Canonical names are used **exactly as registered, including any parenthetical qualifier**. The parenthetical is part of the canonical name, not an alias or optional suffix (e.g. `GreenSock Animation Platform (GSAP)` is the canonical full form; `GSAP` alone or `GreenSock Animation Platform` alone is not).
- **Category groups are presentation, not identity.** The registry's category groups (and their names) are part of the README's presentation and may evolve; when skills are regrouped, their canonical names do not change.
- **Structured lists vs prose.** Structured skill lists (Skills / Tech Stack, Technologies, Tech Stack) must use the exact canonical registry name, parentheticals included; widely recognized short forms (e.g. `GSAP`, `Swift`) are tolerated in running prose where they aid readability.
- **No second skill database.** No JSON/YAML registry, no machine-readable skill file. Markdown-first, human-readable.
- **Repetition is fine.** Records may list skill names in readable Markdown lists. The registry enforces *terminology consistency*, not database normalization. Never replace readable lists with IDs, pointers, variables, generated syntax, or excessive hyperlinks.

### Registry-first workflow (mandatory for new skills)

When a record would introduce a skill not already in the registry:

1. Check the root README Skills / Tech Stack section first.
2. Confirm an equivalent technology isn't already registered under another canonical name.
3. If genuinely new, add it to the appropriate category in the root README **FIRST**.
4. Then use that exact canonical name in the record.
5. Use the same spelling everywhere else.

**A skill must never first appear only inside an experience or project record.**

Flow: `New skill → check canonical registry → exists? yes → reuse exact name | no → add to root README Skills → reuse exact name in project/experience`

### Renaming a skill

1. Update the canonical name in the root README.
2. Update every reference across `src/experiences/**` and `src/projects/**`.
3. Verify the old spelling no longer remains where it refers to the same technology — do not leave aliases behind unintentionally.

### Removing a skill

- Do **not** remove a skill from the registry while project/experience records still legitimately reference it.
- If a skill is no longer desirable in the public high-level Skills presentation but is still historically relevant, preserve the canonical terminology in the career records rather than creating inconsistent historical references.
- The Skills section MAY distinguish primary/current skills from additional/historical technologies without breaking canonical naming.

### Categories

Skills may be grouped into human-readable categories (e.g. Frontend, Backend, Data/APIs, State Management, Styling/UI, Motion/3D, Testing, DevOps/Tooling, AI/Agentic Development, Other). These exact categories are not forced — the existing README's structure wins. The requirement is canonical naming, not a categorization system.

### Vocabulary flow

`root README Skills → canonical vocabulary → Experiences + Projects + future records`

The registry owns the naming; individual records only reference/reuse it.

## Duplication rules

- Full descriptions of an experience or project exist **only** in their record.
- The root README may contain **summaries** (one-line index entries, short blurbs) — that is expected and allowed.
- A record may summarize another record in one line, but must never duplicate the other record's full description.
- Never copy a full section from one location to another; link instead.

## Linking conventions

- Use **standard Markdown relative links**: `[Terminal101](../../projects/terminal101/README.md)`.
- No tool-specific or non-standard link syntax (no wikilinks `[[...]]`, no HTML-only link hacks, no raw URLs where a relative link is intended).
- From an experience record, project links point to `src/projects/<slug>/README.md`.
- From a project record, experience links point to `src/experiences/<slug>/README.md`.
- From the root README, record links point to `src/experiences/<slug>/README.md` and `src/projects/<slug>/README.md`.
- Every relative link must resolve inside the repository.

## Naming and slug conventions

- Slugs are **lowercase**, **hyphen-separated**, and **descriptive**: e.g. `senior-frontend-developer-team-lead-mirotech`, `tadilo-b2c-booking-service`.
- No spaces, underscores, uppercase letters, or special characters in slugs.
- A slug must be specific enough to be unambiguous among all existing records (include the organization for experiences, and enough of the project name to disambiguate, when needed).
- Directory names for records are exactly `<slug>/` containing `README.md`.

## Asset conventions

- Assets (images, screenshots, PDFs, media) live **only** at `src/projects/<project-slug>/assets/`, and only when they exist — never create empty `assets/` directories.
- Reference assets with **relative paths** from the record that uses them: e.g. `![Dashboard](assets/dashboard.png)`.
- Use web-supported formats (e.g. `png`, `jpg`, `webp`, `svg`, `gif`, `mp4`, `pdf`).
- Keep repository size in mind: compress and resize before committing; avoid large binaries.
- Experience records do not have an `assets/` directory; if an experience genuinely needs media, it belongs in the related project's assets.

## Public-data expectations

- **All committed content is intentionally public.** This repository is part of a public GitHub profile.
- **Never add non-public information**: no personal addresses, phone numbers, private identifiers, salaries, confidential client terms, secrets, keys, tokens, or anything covered by an NDA.
- If a fact is sensitive, leave it out rather than redact or obscure it.

## Handling unknown / missing information

- **Preserve what is known.** Record every fact you actually have.
- **Never guess, infer, embellish, or invent.** No approximate dates presented as exact, no invented responsibilities, no assumed technologies.
- When a field is not known, **leave it out** (or explicitly mark it as unknown, e.g. `Unknown`) rather than fabricating a value.
- Unknown end dates, missing achievements, or unrecorded tech stacks are normal — a record may simply omit those sections.

## Updating this repository (for future agents and humans)

1. **Read the specs first** — this file plus the relevant template spec (`experience.md` / `project.md`) before touching any record.
2. **Follow the templates** exactly; do not invent new sections or reorder them.
3. **Keep indexes consistent**: adding, renaming, or removing a record under `src/` must be reflected in the root README's experience/project index in the same change.
4. **Keep links consistent**: update any record that references a changed or moved record.
5. Never edit `specs/` to accommodate a content change — specs change only when the rules themselves change.

## Consistency expectations

At all times:

- every experience record is linked from the root README's experience index, and vice versa (no orphan index entries, no unlinked records);
- every project record is linked from the root README's project index, and vice versa;
- cross-references between experiences and projects resolve to real records;
- dates in a summary never contradict the dates in the canonical record;
- roles, titles, and project names are spelled consistently across root README, experience records, and project records;
- skill and technology names use the exact canonical name from the root README Skills / Tech Stack registry (see "Canonical skill registry" above).