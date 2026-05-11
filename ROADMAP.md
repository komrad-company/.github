# Roadmap

This document describes the intended direction of the Komrad project. It is not a commitment to specific delivery dates. Priorities may shift as the project evolves and the contributor base grows.

---

## What is Komrad?

Komrad is a sovereign, open-source SIEM stack built entirely in Rust. It is designed for organisations that need a capable, affordable, and non-American security monitoring solution — without the operational burden of JVM-based stacks, without vendor lock-in, and without paying for features that should be standard.

**Core differentiators:**

- Full Rust stack — performance, memory safety, low operational footprint
- Quickwit as the search and storage backend — S3-native, cheap to operate at scale
- Pull-based collection model — no inbound sockets, no agents phoning home
- OCSF normalisation — interoperable, vendor-neutral event schema
- Sigma-based detection rules with temporal extensions — time-based correlation natively supported, open standard, portable across tools
- 100% open-source, 100% self-hostable — no feature paywalls
- European — designed with European regulatory context in mind

---

## Components

| Component | Repo | Status | Description |
|-----------|------|--------|-------------|
| **Khronika** | [`Khronika`](https://github.com/komrad-company/Khronika) | 🟡 Active | Structured logging library used across all Komrad components |
| **Kontracts** | [`Kontracts`](https://github.com/komrad-company/Kontracts) | 🟡 Active | gRPC contract definitions (protobuf + generated Rust types) shared across components |
| **Kompiler** | [`Kompiler`](https://github.com/komrad-company/Kompiler) | 🟡 Active | Compiles extended Sigma detection rules into Quickwit queries |
| **Korelator** | [`Korelator`](https://github.com/komrad-company/Korelator) | 🟡 Active | Correlation engine — evaluates compiled rules against incoming events and generates alerts |
| **Kolektor** | private | 🔴 Early | Catalogue of Vector.dev pipeline configurations with OCSF normalisation, manageable via Kontrol |
| **Krawler** | private | 🔴 Planned | Pull-based log collector — fetches logs from remote sources (APIs, syslog, file, cloud) without requiring inbound connectivity |
| **Kontrol** | private | 🟠 Refactor | Web UI (Svelte) — central interface for managing pipelines, rules, alerts, and search |
| **Kontinuous-integration** | [`Kontinuous-integration`](https://github.com/komrad-company/Kontinuous-integration) | 🟡 Active | Shared CI/CD infrastructure and reusable GitHub Actions workflows |

---

## Phases

### Phase 0 — Foundations ✅ (current)

The goal of this phase is to establish the core building blocks that all other components depend on.

- [x] Khronika — structured logging across components
- [x] Kontracts — gRPC contracts and shared Rust types
- [x] Kompiler — Sigma rule compilation to Quickwit queries
- [x] Korelator — correlation engine skeleton
- [x] Kontinuous-integration — shared CI/CD infrastructure
- [x] Governance, security policy, contribution guidelines
- [x] Public organisation on GitHub with consistent AGPL-3.0 licensing

---

### Phase 1 — MVP

The goal of this phase is to produce a functional, self-hostable SIEM that a technically capable team can deploy and operate.

**Kolektor**
- [ ] Initial catalogue of Vector.dev pipeline configurations for Tier 1 sources (Linux syslog, Windows Event Log, OPNsense, AWS CloudTrail, CrowdStrike)
- [ ] OCSF normalisation for all Tier 1 pipelines
- [ ] CI testing for pipeline configs (lint, schema validation)
- [ ] gRPC API for pipeline management (Kontracts)
- [ ] Message queue integration (Kafka / Redpanda) — durable buffer between Vector pipelines and the rest of the stack, absorbs backpressure when a downstream component is unavailable

**Korelator**
- [ ] End-to-end rule evaluation pipeline (Kompiler → Korelator → alert)
- [ ] Time-based correlation engine — evaluate sequences of events over sliding or fixed time windows
- [ ] Extended Sigma rule format supporting temporal correlation conditions (not supported by standard Sigma)
- [ ] Alert storage and retrieval via Quickwit
- [ ] gRPC API for rule and alert management

**Kontrol**
- [ ] Svelte refactor — clean, maintainable codebase
- [ ] Pipeline management (Kolektor)
- [ ] Rule management (Kompiler + Korelator)
- [ ] Alert dashboard
- [ ] Event search interface (Quickwit)

**Deployment**
- [ ] Kubernetes manifests (Kustomize or Helm)
- [ ] Docker Compose stack for single-node deployments

---

### Phase 2 — Hardening & Ecosystem

The goal of this phase is to make Komrad production-ready and extend the catalogue of supported sources.

**Detection**
- [ ] Expanded Sigma rule catalogue (community contributions welcome)
- [ ] Evaluate a unified query/rule language (SPL-like DSL covering both search and detection)
- [ ] Rule testing framework

**Kolektor catalogue expansion**
- [ ] Tier 2 sources (Azure, GCP, Okta, Palo Alto, Fortinet, etc.)
- [ ] Community-contributed pipelines with review process

**Krawler**
- [ ] Pull-based collector supporting initial source types (file, syslog receiver, HTTP/API polling)
- [ ] Controlled via Kontrol through gRPC

**Operability**
- [ ] Metrics and health endpoints for all components (Prometheus-compatible)
- [ ] Upgrade and migration tooling
- [ ] Backup and restore documentation

**Packaging**
- [ ] `.deb` and `.rpm` packages for standalone deployments (non-Kubernetes environments)

---

### Phase 3 — Scale & Openness

- [ ] Multi-tenant architecture (for MSSP / SOC-as-a-service use cases)
- [ ] RBAC — role-based access control in Kontrol
- [ ] Audit logging of all administrative actions
- [ ] Public rule repository (community Sigma catalogue)
- [ ] SDK / integration documentation for third-party connectors

---

## What we are not building (right now)

- A hosted SaaS offering — this may be explored in the future subject to core team consensus
- An agent-based collection model — pull is a deliberate architectural choice
- An Elastic/OpenSearch compatibility layer — we are not an Elastic replacement, we are an alternative

---

## Contributing

The areas most open to external contribution today are:

- **Kolektor** — Vector.dev pipeline configurations and OCSF mappings for new log sources
- **Kompiler** — Sigma rule extensions and test cases
- **Documentation** — deployment guides, architecture diagrams, runbooks

For anything else, open an issue or a discussion before investing significant effort. See [`CONTRIBUTING.md`](./CONTRIBUTING.md) and [`GOVERNANCE.md`](./GOVERNANCE.md).

---

*Last updated: May 2026*
