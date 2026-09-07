# Experience Record — Template & Authoring Rules

schema: 1

This spec defines the exact template and rules for every experience record at:

```
src/experiences/<experience-slug>/README.md
```

Read [`career-profile.md`](./career-profile.md) first for repository-wide invariants (slugs, linking, public data, unknown fields).

## Template

Use this template as the skeleton for every new experience record. Required fields must be present; optional sections are included **only when the information is known** — never invent content for them, and omit optional sections entirely when their information is unknown.

```markdown
# <Role / Title> @ <Organization>

<Optional: 1–3 sentence overview of the position — what it was and its scope.>

- **Employment type:** <e.g. Full-time, Freelance, Internship>
- **Location:** <e.g. Bucharest, Romania — Remote>
- **Period:** <Start date> – <End date or Present>

## Responsibilities

- <Responsibility>

## Achievements & Highlights

- <Achievement or highlight>

## Technologies

- <Technology>

<!-- Skill naming: exact canonical names (including parentheticals) in this list — see "Skill naming (Technologies section)" below. -->

## Associated Projects

- [<Project Name>](../../projects/<project-slug>/README.md) — <one-line summary>

## Relevant Public Links

- <Public link title>: <URL>
```

## Field reference

### Required

| Field | Rule |
|---|---|
| **Role / Title** | The heading `# <Role / Title> @ <Organization>`. For freelance/self-employed periods, use the professional role as title (e.g. `Senior Full-Stack Engineer (Agentic Development)`) with `Self-Employed / Freelance` as organization. |
| **Organization** | Part of the heading. For freelance/self-employed, `Self-Employed / Freelance`. |
| **Start date** | In the `Period:` line, `YYYY-MM` or `YYYY` when the month is unknown — as much precision as is actually known. `Present` for current roles. |

### Optional

| Section | Rule |
|---|---|
| **Employment type** | Include when known. |
| **Location** | Include when known. Note remote/on-site as actually known. |
| **End date** | In the `Period:` line. Use `Present` for current roles; for a known start with an unknown end, write only the start (e.g. `2022-04 –`). |
| **Overview** | 1–3 sentences directly under the heading. Scope and context only — no duplicated detail from later sections. |
| **Responsibilities** | Bullet list. What the person was responsible for, as known. |
| **Achievements & Highlights** | Bullet list. Concrete outcomes and notable work, as known. Omit entirely if none are known. |
| **Technologies** | Bullet list of technologies actually used in this role. Use **canonical names** from the root README Skills / Tech Stack registry — see the skill naming note below. |
| **Associated Projects** | See "Referencing projects" below. |
| **Relevant Public Links** | Public URLs only (see public-data rules in [`career-profile.md`](./career-profile.md)). Never link private or confidential material. |

### Career breaks

Career breaks and deliberate upskilling periods are experiences too. Use a heading like `# Career Break / Professional Development`, with no `@ <Organization>` part, and the same optional sections as any other record.

### Skill naming (Technologies section)

> **Before adding or changing any skill in this record, verify its canonical name in the root README Skills / Tech Stack registry. If the skill is new, register it there first, then reuse the exact same name here.**

- Canonical names only — no locally invented aliases, no alternate spellings. Use the exact registered name including any parenthetical qualifier.
- Structured lists (this Technologies section) use exact canonical names; running prose may use widely recognized short forms (e.g. `GSAP`, `Swift`) where they aid readability.
- Registry-first handling for new skills (see the canonical skill registry rules in [`career-profile.md`](./career-profile.md)).

## Referencing projects

- An experience references a project with a **standard relative link** to the project record: `[Project Name](../../projects/<project-slug>/README.md)` (from `src/experiences/<slug>/README.md`).
- Follow the link with a **one-line summary** — that is the maximum. **Do not duplicate full project descriptions.** The project record is the single source of truth for the project.
- If a project has no record yet, do not fabricate a summary in its place — either note the project by name without a link, or create the project record (following [`project.md`](./project.md)) first.

## What belongs where

| Location | Holds |
|---|---|
| **Experience record** (this spec) | Everything about the role: full dates, employment type, location, overview, responsibilities, achievements, technologies, links to associated projects, public links. |
| **Root README** | A one-line summary in the experience index: role/title, organization, period, and a very short descriptor — linking to the record. No full responsibilities or achievements. |
| **Project record** | Everything about the project itself (see [`project.md`](./project.md)), including a link back to this experience under *Related Experience*. |

The experience record owns the **role perspective** (what the person did in this position); the project record owns the **project perspective** (what the project is and how it was built). The same fact may appear in both only as a one-line summary from the other's perspective.

## Rules recap

- One experience per directory; slug per [`career-profile.md`](./career-profile.md) naming conventions.
- Never guess, infer, embellish, or invent — leave unknown fields out or mark them unknown (see [`career-profile.md`](./career-profile.md)).
- All content is public by definition; never add non-public information.
- Technologies use canonical skill names from the root README registry — no local aliases (see "Skill naming" above and [`career-profile.md`](./career-profile.md)).
- Adding, renaming, or removing an experience record requires updating the root README experience index in the same change.