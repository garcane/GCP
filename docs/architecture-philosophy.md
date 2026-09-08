# Architecture Philosophy (Shared Across Cloud Projects)

> Guidance distilled from portfolio planning discussions on how to structure multi-cloud Analytics Engineering projects.

## Core Principle

**Build the data product locally. Use the cloud as the production target. Use local cloud-compatible emulators only where they add value for integration testing and architecture demonstration.**

Do not optimise for 100% cloud imitation. Demonstrate understanding of the architecture, the ability to build it independently, and the ability to move it between environments.

---

## Recommended Progression

1. **Local development** – full data platform (ingestion → transformations → analytical model → ML → serving) running via Docker / local tools.
2. **Cloud-simulated** – integrate against cloud-compatible service interfaces (where an emulator exists) for development and integration testing without consuming credits.
3. **Production** – deploy and validate the real cloud architecture. Build → deploy → demonstrate → tear down.

---

## dbt as a First-Class Component

Regardless of cloud, the transformation and modelling layer should be a primary demonstration of Analytics Engineering skill:

- SQL transformations
- staging / intermediate / marts layering
- tests (uniqueness, not-null, relationships, accepted values)
- documentation and lineage
- version control and CI (`dbt build`)
- portability across analytical engines where practical

---

## Cost Discipline

Ask: “Which components provide enough additional evidence of competence to justify spending money on them?”

- Develop and iterate locally (near-zero cost).
- Use emulators for interface/integration work.
- Spend cloud credits only on genuine validation steps.
- Keep expensive resources ephemeral.

---

## Multi-Cloud View

The three projects (AWS, GCP, Azure) should eventually become three production targets of a shared architectural philosophy rather than three isolated “cloud tutorial” repositories.

Build one exceptionally well first. The others can follow as alternative implementations.

---

## Narrative Goal

An employer looking at the repository should conclude:

> “This person could actually own a data platform from ingestion through to production.”

The hybrid local → simulated → production story is stronger than either a pure local pipeline or a pure emulator project.
