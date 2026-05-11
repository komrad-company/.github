> *"The collective maintains its forms as it maintains its code — with discipline, brevity, and no room for improvisation."*
> — Komrad Engineering Collective, May 2026

Organization-wide community health files for the Komrad ecosystem. Pull request templates, label definitions, and the organization profile are declared here and apply to every repository under the `komrad` organization.

## Structure

| Path | Role |
|---|---|
| `PULL_REQUEST_TEMPLATE.md` | Default PR template |
| `PULL_REQUEST_TEMPLATE/` | Specialized templates — feature, bugfix, refactor, docs, chore, security |
| `labels.yml` | Issue label definitions — to be synced to all repositories |
| `default.json5` | Shared Renovate preset — extended by every repository |
| `profile/README.md` | Organization profile displayed on the GitHub organization page |
| `templates/` | README templates for new repositories |

## Labels

Labels are declared in `labels.yml`. All changes to labels must go through this file.

| Label | Color | Role |
|---|---|---|
| `Party Directive` | `#8b1a1a` | New feature ordered by the Central Committee |
| `Comrade's Mishap` | `#cc0000` | Bug — an unintentional error committed by a loyal but fallible comrade |
| `Five-Year Plan` | `#c9a800` | Improvement, refactor, documentation, or maintenance |
| `Warwatch` | `#1a3a1a` | Security vulnerability under wartime surveillance |

## Pull Request Templates

| Template | Label | URL parameter |
|---|---|---|
| `feature.md` | `Party Directive` | `?template=feature.md` |
| `bugfix.md` | `Comrade's Mishap` | `?template=bugfix.md` |
| `refactor.md` | `Five-Year Plan` | `?template=refactor.md` |
| `docs.md` | `Five-Year Plan` | `?template=docs.md` |
| `chore.md` | `Five-Year Plan` | `?template=chore.md` |
| `security.md` | `Warwatch` | `?template=security.md` |

## Renovate

The collective declares one Renovate preset. Every repository extends it. Forks of the preset are not tolerated.

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>komrad-company/.github"]
}
```

Place this file at the root of any consuming repository as `renovate.json` (or `.github/renovate.json`). Renovate resolves `default.json5` automatically.

Three categories of updates are surfaced distinctly. Each carries its own PR title prefix, cooldown, label set, and approval policy.

| Category | Trigger | Label | PR title prefix | Cooldown | Approval |
|---|---|---|---|---|---|
| Security | CVE / OSV advisory | `Warwatch` | `[FIX] security:` | 0 days | None — immediate |
| Major | `1.x → 2.x` | `Five-Year Plan` | `[FIX] major:` | 7 days | Dependency Dashboard |
| Minor | `1.2 → 1.3` and patch | `Five-Year Plan` | `[FIX] minor:` | 3 days | None |

Security updates bypass the schedule. They are filed the moment an advisory matches. The collective does not negotiate with vulnerabilities.

Major updates wait seven days after release and require explicit approval on the Dependency Dashboard. Breaking changes are not merged by reflex.

Minor and patch updates flow on the weekly schedule (`before 7am on monday`, Europe/Paris) with a three-day cooldown.

Lockfile maintenance runs on the first day of each month.

A consuming repository may add a `packageRules` entry to override behavior for a specific dependency. Overriding the three-category structure itself requires collective approval.

## License

MIT. The collective's work remains open, as all things should be.
