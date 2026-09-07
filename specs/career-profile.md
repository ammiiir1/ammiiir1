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

- Slugs are **lowercase**, **hyphen-separated**, and **descriptive**: e.g. `senior-frontend-developer-team-lead-mirotech`, `tadilo-b2c-booking-platform`.
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
- roles, titles, and project names are spelled consistently across root README, experience records, and project records.