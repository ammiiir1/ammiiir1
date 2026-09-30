# Project Record — Template & Authoring Rules

schema: 1

This spec defines the exact template and rules for every project record at:

```
src/projects/<project-slug>/README.md
```

Read [`career-profile.md`](./career-profile.md) first for repository-wide invariants (slugs, linking, public data, unknown fields).

## Template

Use this template as the skeleton for every new project record. Required fields must be present; optional sections are included **only when the information is known** — never invent content for them, and omit optional sections entirely when their information is unknown.

```markdown
# <Project Name>

<Short description — one clear sentence or two stating what the project is.>

- **Role:** <e.g. Lead Frontend Developer>
- **Period:** <Start> – <End or Present>
- **Relationship:** <How the project relates to a company/employer — e.g. built at MiroTech, personal project, client work>

## Overview

<Paragraph(s) describing the project's purpose, scope, and context — as much as is actually known.>

## Responsibilities & Contributions

- <What the person was responsible for or contributed>

## Notable Implementation Details

- <Architectural decision, integration, or technical detail worth recording>

## Achievements & Outcomes

- <Measurable or notable result>

## Tech Stack

- <Technology>

<!-- Skill naming: exact canonical names (including parentheticals) in this list — see "Skill naming (Tech Stack section)" below. -->

## Public URL

- <URL>

## Repository URL

- <URL — only if the repository is public>

## Screenshots & Media

![<Description>](assets/<file>)

## Related Experience

- [<Role / Title> @ <Organization>](../../experiences/<experience-slug>/README.md)
```

## Field reference

### Required

| Field | Rule |
|---|---|
| **Project name** | The `# <Project Name>` heading. Use the project's real name as it is publicly known. |
| **Short description** | One clear sentence or two directly under the heading, stating what the project is. |

### Optional

| Section | Rule |
|---|---|
| **Role** | The person's role on this project, when known. |
| **Period** | `YYYY-MM` or `YYYY` per known precision; `Present` for ongoing. Omit if unknown. |
| **Project/company relationship** | How the project relates to an employer or client (e.g. built at MiroTech, personal project, client work). Include when it clarifies context; omit for standalone personal projects where it adds nothing. |
| **Overview** | Purpose, scope, and context — as much as is actually known. |
| **Responsibilities & Contributions** | Bullet list of what the person did on this project. |
| **Notable Implementation Details** | Bullet list of architecture, integrations, or technical decisions worth recording. |
| **Achievements & Outcomes** | Bullet list of results. Omit entirely if none are known. |
| **Tech Stack** | Bullet list of technologies actually used. Use **canonical names** from the root README Skills / Tech Stack registry — see the skill naming note below. |
| **Public URL** | Public, live URL only. Omit if none exists. |
| **Repository URL** | Only if the repository is public. Never link private repositories. |
| **Screenshots & Media** | See "Asset placement" below. Omit entirely if no assets exist. |
| **Related Experience** | See "Referencing experiences" below. |

## Skill naming (Tech Stack section)

> **Before adding or changing any skill in this record, verify its canonical name in the root README Skills / Tech Stack registry. If the skill is new, register it there first, then reuse the exact same name here.**

- Canonical names only — no locally invented aliases, no alternate spellings. Use the exact registered name including any parenthetical qualifier.
- Structured lists (this Tech Stack section) use exact canonical names; running prose may use widely recognized short forms (e.g. `GSAP`, `Swift`) where they aid readability.
- Registry-first handling for new skills (see the canonical skill registry rules in [`career-profile.md`](./career-profile.md)).

## Asset placement & relative linking

- Assets live **only** at `src/projects/<project-slug>/assets/`, and the directory is created **only when assets exist** — never commit an empty `assets/` directory.
- Reference assets with **relative paths** from the record: `![Dashboard](assets/dashboard.png)`.
- Use web-supported formats (e.g. `png`, `jpg`, `webp`, `svg`, `gif`, `mp4`, `pdf`).
- Keep repository size in mind: compress and resize before committing; avoid large binaries.
- No assets outside the project's own `assets/` directory (no shared or root-level asset folders).

## Referencing experiences

- A project references a related experience with a **standard relative link** to the experience record: `[Role / Title @ Organization](../../experiences/<experience-slug>/README.md)` (from `src/projects/<slug>/README.md`).
- Link only experiences that genuinely relate to this project; do not invent relationships.
- If the experience has no record yet, either note the relationship by name without a link, or create the experience record (following [`experience.md`](./experience.md)) first.

## What belongs where

| Location | Holds |
|---|---|
| **Project record** (this spec) | Everything about the project: full description, role, period, contributions, implementation details, tech stack, links, media. |
| **Root README** | A one-line summary in the project index: project name and a very short descriptor — linking to the record. No full descriptions. |
| **Experience record** | The role perspective (see [`experience.md`](./experience.md)), including a one-line link to this project under *Associated Projects*. |

The project record owns the **project perspective** (what the project is and how it was built); the experience record owns the **role perspective** (what the person did in that position). The same fact may appear in both only as a one-line summary from the other's perspective.

## Rules recap

- One project per directory; slug per [`career-profile.md`](./career-profile.md) naming conventions. **Exception:** a record may bundle closely related projects when they were introduced as a single line of work in the source and splitting them would require inventing facts — see the bundling exception in [`career-profile.md`](./career-profile.md). Bundled records use a hyphen-joined slug of the member projects and keep each member's facts internally separated.
- Never guess, infer, embellish, or invent — leave unknown fields out or mark them unknown (see [`career-profile.md`](./career-profile.md)).
- All content is public by definition; never add non-public information. Public URL and Repository URL sections carry public links only.
- Tech Stack uses canonical skill names from the root README registry — no local aliases (see "Skill naming" above and [`career-profile.md`](./career-profile.md)).
- Adding, renaming, or removing a project record requires updating the root README project index in the same change.