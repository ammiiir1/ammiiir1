# Specs

This directory contains the **rules** for how this repository is organized and how career content must be authored. It contains no career data itself.

## Purpose

This repository is a public career record: a GitHub profile repository that presents Amir's professional history — experiences and projects — in a structured, maintainable way. The specs exist so that:

- every piece of career content has exactly one obvious home,
- future additions and updates follow the same structure and conventions,
- anyone (human or agent) can add content without guessing where it goes or how it is formatted,
- the repository stays internally consistent as it grows.

## Which file governs which content type

| File | Governs |
|---|---|
| [`career-profile.md`](./career-profile.md) | Repository-wide invariants: responsibilities of the root README, `src/experiences/`, and `src/projects/`; source-of-truth, linking, naming, asset, duplication, and public-data rules; how to update this repository. |
| [`experience.md`](./experience.md) | The exact template and authoring rules for every experience record at `src/experiences/<experience-slug>/README.md`. |
| [`project.md`](./project.md) | The exact template and authoring rules for every project record at `src/projects/<project-slug>/README.md`. |

## Rules vs. data

- The root `README.md` and everything under `src/` contain the **actual career data**.
- This `specs/` directory contains the **rules**, not duplicate career facts. Specs define how future career data must be added and updated; they never restate, summarize, or duplicate the career data itself.

When adding or updating any career content, read the relevant spec first, then follow it.

> Note: this `specs/` layout is **domain-specific authoring rules** for career content (`specs/<domain>.md`), not the generic spec-kit feature-spec layout (`specs/<feature>/spec.md`, `spec.md`/`INDEX.md`/`global.spec.md`). Do not apply the spec-kit feature-spec conventions here.