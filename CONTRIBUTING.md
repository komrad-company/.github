# Contributing

> *"A contribution not reviewed is a vulnerability not caught."*
> — Komrad Engineering Collective, May 2026

The collective welcomes contributions. They must meet the standards below without exception. These are not suggestions.

---

## Branches

| Branch | Purpose |
|---|---|
| `main` | Stable — protected. No direct push. |
| `develop` | Integration — the daily work of the collective |
| `feat/<name>` | New feature spanning multiple commits |
| `issue/<id>` | Corrective branch derived from `main` |

One-shot, single-commit additions go directly to `develop`. A branch is opened only when the work spans multiple commits or extends over time.

---

## Commits

Format: `[ACTION] message` — in English, always.

| Action | Usage |
|---|---|
| `ADD` | A new capability is given to the collective |
| `FIX` | An error is corrected |
| `DEL` | Dead weight is removed |

Group files by functional scope into separate commits. Neither `git add .` in a single commit nor one commit per file. Each commit must be readable and understandable on its own.

```bash
# ✅ Correct
git add src/errors.rs
git commit -m "[ADD] error type for rule parsing"

git add src/rules.rs src/rules/condition.rs
git commit -m "[ADD] condition evaluation logic"

# ❌ Forbidden
git add .
git commit -m "[ADD] feature"
```

Commits must be signed with a GPG key.

---

## Before every commit

```bash
cargo fmt -- --check
cargo clippy -- -D warnings
cargo test
cargo deny check
```

Code that does not pass these checks is not ready. It will fail CI.

---

## Pull Requests

- Rebase onto the target branch before opening — no merge commits
- Reference the issue being closed (`Closes #<id>`)
- One approval from a CODEOWNER is required
- All CI checks must pass before merge
- No squash — history is preserved, blame is sacred

---

## Kolektor catalogue contributions

Kolektor is not a Rust crate — it is a catalogue of Vector.dev pipeline configurations. The Rust rules below do not apply. Kolektor contributions follow their own standards, documented in [`_schema/README.md`](https://github.com/komrad-company/Kolektor/blob/main/_schema/README.md) in the Kolektor repository.

The mandatory requirements are:

- One `vector.toml` per source — source, VRL transform, and Quickwit sink in a single file
- Minimum three tests per source using real raw log samples (`nominal`, `optional_missing`, `malformed`)
- All events retain the original log in the `raw` field
- Invalid events are routed to `raw-logs` with `parse_status = "failed"`, never silently discarded
- `catalog/index.json` must be regenerated via `ci/catalog_index.py` before committing

---

## Code standards

These rules apply to all Rust code contributed to the ecosystem.

**Errors**

- `let-else` for every `Option` and `Result` — no nested `match`
- `.unwrap()` and `.expect()` are forbidden outside of tests
- Errors are never silently ignored — log with `warn` (recoverable) or `error` (fatal)
- Use `thiserror` in libraries — one `Error` enum in `src/errors.rs`

**Logging**

- Khronika macros only — `println!` is forbidden outside of tests
- `error`: non-recoverable — `warn`: recoverable — `info`: business event — `debug`: normal flow — `trace`: verbose

**Design**

- `Arc<T>` over lifetimes `'a` in async or multi-threaded contexts
- `enum` for closed sets known at compile time

**Naming**

- All function and variable names must be explicit — short non-descriptive names (`f`, `h`, `p`) are forbidden, including in tests

**Visibility**

- Internal modules: `pub(crate) mod` — never exposed directly
- Public API: `pub use` in `lib.rs` — the only exit for types
- Internal methods: `pub(crate)` even when the parent type is `pub`

**Dependencies**

- Inter-crate references: git tag in production, `path` only in local dev via `[patch]`
- Every new external dependency updates `deny.toml`
- No comments in `Cargo.toml`
