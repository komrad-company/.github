# Governance

## Overview

Komrad is an open-source project building a sovereign SIEM stack for European organisations. It is currently maintained by a core team of two independent contributors. There is no formal legal entity at this time.

This document defines how the project is governed, how decisions are made, and how contributors can grow their involvement.

---

## Roles

### Core Team

The core team is responsible for the overall direction of the project, architectural decisions, release management, and final approval on all pull requests.

Current core team:

| Name | GitHub | Domain |
|------|--------|--------|
| Benoit Caillabet | @bcaillabet | SOC architecture, integrations, catalog, infrastructure |
| Tristan | @wampixel | Rust development, cryptography, component internals |

The core team operates by consensus. In case of disagreement, each member holds veto rights within their primary domain (see *Domain Authority* below).

### Maintainers

Maintainers are trusted contributors who have demonstrated sustained, high-quality involvement in a specific repository or component. They can review and approve pull requests but cannot merge without at least one core team member approval.

Current maintainers:

| Name | GitHub | Domain |
|------|--------|--------|
| David Esteban | @davidesteban91120-jpg | Kubernetes, cloud infrastructure, CI/CD (`kontinuous-integration`) |

Maintainers may be invited to join the core team after a period of consistent contribution and demonstrated alignment with the project's direction.

### Contributors

Anyone who submits a pull request, opens an issue, or participates in discussions is a contributor. Contributions of all kinds are welcome: code, documentation, testing, catalog configurations, bug reports, and security feedback.

---

## Domain Authority

To avoid bottlenecks and respect expertise boundaries, each core team member holds primary authority over their domain:

- **Rust internals** (khronika, any `*-rs` component): Tristan has final say on architecture and implementation choices.
- **SOC design, OCSF normalization, Vector.dev pipelines, catalog structure, integration specs**: Benoit has final say.
- **Cross-cutting decisions** (new repositories, project scope, external partnerships, licensing changes): require consensus from both core team members.

---

## Decision Making

### Routine decisions

Day-to-day decisions (merging PRs, closing issues, triaging bugs) are made autonomously by whichever core team member is active, within their domain.

### Significant decisions

Decisions that affect project direction, architecture, or community structure are discussed openly in a GitHub issue or discussion thread before being acted upon. A minimum of 48 hours is given for async feedback before closing.

Examples of significant decisions:
- Adding a new top-level component or repository
- Changing the license of any repository
- Accepting a new maintainer
- Establishing a formal legal entity
- Adopting a new external dependency with security implications

### Disagreements

If the core team cannot reach consensus on a significant decision, the decision defaults to a 7-day open discussion period in the relevant repository. After that period, the member with primary domain authority makes the final call.

---

## Pull Request Policy

All pull requests must:

1. Target the appropriate branch (`main` is protected; use feature branches).
2. Pass all CI checks (linting, tests, where applicable).
3. Include a clear description of the change and its motivation.
4. Be reviewed and approved by **at least one core team member** before merging.

Self-merging by a core team member is allowed for trivial changes (typos, CI fixes) but discouraged for functional changes.

External contributors are encouraged to open a draft PR or an issue before investing significant effort, to validate the direction with the core team.

---

## Developer Certificate of Origin (DCO)

Komrad uses the [Developer Certificate of Origin (DCO)](https://developercertificate.org/) to certify that contributors have the right to submit their code under the project's license.

All commits must include a `Signed-off-by` line:

```
git commit -s -m "your commit message"
```

This is not a Contributor License Agreement. It is a lightweight declaration that the contribution is yours to give, and that you agree to the project's license terms. Contributors acting in a professional capacity should verify that their employer permits open-source contributions under these terms.

---

## Licenses

All Komrad repositories are licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)** unless explicitly stated otherwise in a repository's `LICENSE` file.

The AGPL-3.0 license ensures that modifications to the software, including when operated as a network service, must be made available under the same terms. This is a deliberate choice to prevent proprietary capture of the project.

---

## Legal Status

Komrad is currently an informal collaborative project with no registered legal entity. All intellectual property contributions remain governed by the AGPL-3.0 license and the DCO.

The core team may establish a formal legal structure (association, SAS, or European cooperative equivalent) in the future as the project grows. Any such decision will be announced publicly and will not retroactively affect contributions made under the current terms.

---

## Code of Conduct

Komrad follows the [Contributor Covenant Code of Conduct v2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/). All participants are expected to uphold it. Reports of unacceptable behaviour can be sent to the core team via the contact address in `SECURITY.md`.

---

## Changes to this Document

Changes to this governance document require consensus from all core team members and must be announced in the project's main communication channel with a minimum notice of 7 days before taking effect.

---

*Last updated: May 2026*
