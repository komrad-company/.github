# Governance

> *"The collective does not govern by committee. It governs by clarity."*
> — Komrad Engineering Collective, May 2026

Komrad is an open-source project building a sovereign SIEM stack for European organisations. It is maintained by a core team of two independent contributors. There is no formal legal entity at this time.

This document defines how the project is governed, how decisions are made, and how contributors grow their involvement. It is not a suggestion.

---

## Roles

### Core Team

The core team holds final authority over project direction, architecture, release management, and all pull requests.

| Name | GitHub | Domain |
|------|--------|--------|
| Benoit Caillabet | @bcaillabet | SOC architecture, integrations, catalog, infrastructure |
| Tristan | @wampixel | Rust development, cryptography, component internals |

The core team operates by consensus. Each member holds veto rights within their primary domain. See *Domain Authority*.

### Maintainers

Maintainers are trusted contributors with sustained, high-quality involvement in a specific repository or component. They review and approve pull requests. They do not merge without at least one core team member approval.

| Name | GitHub | Domain |
|------|--------|--------|
| David Esteban | @davidesteban91120-jpg | Kubernetes, cloud infrastructure, CI/CD (`kontinuous-integration`) |

A maintainer demonstrating consistent contribution and alignment with the project's direction may be invited to join the core team.

### Contributors

Anyone who submits a pull request, opens an issue, or participates in discussions is a contributor. Code, documentation, testing, catalog configurations, bug reports, and security feedback are all welcome.

---

## Core Team Continuity

A core team member is not removed from the project without their explicit consent. The collective does not expel its builders.

No pull request, branch, or contribution from a core team member may be closed, rejected, or overridden without their acknowledgement. Disagreements on contributions follow the process defined in *Decision Making*.

Authorship is permanent. Past contributions cannot be erased, reassigned, or used to exclude their author from the project's history.

---

## Domain Authority

Each core team member holds final authority within their domain. Bottlenecks are not acceptable.

- **Rust components** (all Rust repositories): Tristan has final say on architecture and implementation.
- **SOC design, OCSF normalisation, Vector.dev pipelines, catalog structure, integration specs**: Benoit has final say.
- **Cross-cutting decisions** (new repositories, project scope, external partnerships, licensing changes): require consensus from both core team members.

---

## Decision Making

### Routine decisions

Day-to-day work — merging PRs, closing issues, triaging bugs — is handled autonomously by whichever core team member is active, within their domain.

### Significant decisions

Decisions affecting project direction, architecture, or community structure are discussed openly in a GitHub issue or discussion thread. A minimum of 48 hours is given for async feedback before action is taken.

Significant decisions include:

- Adding a new top-level component or repository
- Changing the licence of any repository
- Accepting a new maintainer
- Establishing a formal legal entity
- Adopting a new external dependency with security implications

### Disagreements

When the core team cannot reach consensus, a 7-day open discussion period is opened in the relevant repository. After that period, the member with primary domain authority makes the final call.

---

## Pull Request Policy

All pull requests must:

1. Target the appropriate branch — `main` is protected, use feature branches.
2. Pass all CI checks.
3. Include a clear description of the change and its motivation.
4. Receive approval from **at least one core team member** before merging.

Core team members may self-merge trivial changes (typos, CI fixes). Functional changes require review.

External contributors are encouraged to open a draft PR or an issue before investing significant effort. Validate direction with the core team first.

---

## Developer Certificate of Origin (DCO)

Komrad uses the [Developer Certificate of Origin](https://developercertificate.org/). Every commit must carry a `Signed-off-by` line:

```bash
git commit -s -m "[ACTION] your commit message"
```

This is not a CLA. It is a declaration that the contribution is yours to give and that you agree to the project's licence terms. Contributors acting in a professional capacity must verify that their employer permits open-source contributions under these terms.

---

## Licences

All Komrad repositories are licensed under **AGPL-3.0** unless explicitly stated otherwise in a repository's `LICENSE` file.

This is a deliberate choice. Modifications to the software — including when operated as a network service — must be made available under the same terms. Proprietary capture of the collective's work is not permitted.

---

## Legal Status

Komrad is an informal collaborative project with no registered legal entity. All contributions are governed by AGPL-3.0 and the DCO.

The core team may establish a formal legal structure in the future. Any such decision will be announced publicly and will not retroactively affect prior contributions.

---

## Code of Conduct

Komrad follows the [Contributor Covenant v2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/). All participants are expected to uphold it. Reports of unacceptable behaviour are sent to the core team via the contact address in `SECURITY.md`.

---

## Changes to this Document

Changes to this governance document require consensus from all core team members. They must be announced in the project's main communication channel with a minimum of 7 days notice before taking effect.

---

*Last updated: May 2026*
