# Komrad Engineering Collective

> *"The enemy does not announce itself. The collective must see before it is seen."*
> — Komrad Engineering Collective, May 2026

Komrad is a Rust-native security platform built for event correlation at scale. It ingests streams of JSON events, evaluates them against declarative detection rules, and alerts the collective when a threat is confirmed. Every component is a crate. Every crate has a single duty. No crate exceeds its mandate.

---

## Ecosystem

```
Quickwit (JSON event stream)
    └──► Korelator          — correlation engine, entry point of the pipeline
              ├── Kompiler  — YAML rule parser, produces Vec<Rule>
              └── Khronika  — unified logging, single approved channel for all telemetry
```

| Repository | Role |
|---|---|
| [Korelator](https://github.com/komrad-company/Korelator) | Correlation engine — consumes Quickwit events, evaluates rules, raises alerts |
| [Kompiler](https://github.com/komrad-company/Kompiler) | Rule parser — transforms YAML detection rules into typed Rust structs |
| [Khronika](https://github.com/komrad-company/Khronika) | Logging layer — initialises the log pipeline once, re-exports `tracing` macros |
| [Kontinuous-integration](https://github.com/komrad-company/Kontinuous-integration) | CI infrastructure — shared reusable workflows and composite actions for the entire ecosystem |

---

## Principles

**One duty per crate.** Khronika logs. Kompiler parses. Korelator correlates. A crate that exceeds its purpose is a liability.

**The dependency arrow is one-way.** Khronika and Kompiler do not know Korelator exists. Business logic belongs to the consumer.

**Errors are not hidden.** Recoverable anomalies are warned. Non-recoverable failures are errors. Silent failure is forbidden.

**The pipeline is law.** Security runs first. Formatting is not taste — it is a decree. Warnings are errors.

**Dependencies are vetted.** Every external crate is evaluated before admission. None are added lightly. `cargo deny` enforces what the collective has ratified.

---

## License

AGPL-3.0-or-later — the source remains open, as all things should be.
