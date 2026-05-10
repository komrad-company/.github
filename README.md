> *"The collective maintains its forms as it maintains its code — with discipline, brevity, and no room for improvisation."*
> — Komrad Engineering Collective, May 2026

Organization-wide community health files for the Komrad ecosystem. Pull request templates, label definitions, and the organization profile are declared here and apply to every repository under the `komrad` organization.

## Structure

| Path | Role |
|---|---|
| `PULL_REQUEST_TEMPLATE.md` | Default PR template |
| `PULL_REQUEST_TEMPLATE/` | Specialized templates — feature, bugfix, refactor, docs, chore, security |
| `labels.yml` | Issue label definitions — to be synced to all repositories |
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

## License

MIT. The collective's work remains open, as all things should be.
