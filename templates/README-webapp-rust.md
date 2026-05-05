# 🦀 Nom du projet

> Description courte de l'application web Rust

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Rust](https://img.shields.io/badge/rust-1.75+-orange.svg)
![Version](https://img.shields.io/badge/version-0.1.0-green.svg)

---

## Table des matières

---

## 📖 À propos

Description détaillée du projet, sa raison d'être et ses objectifs.

---

## ✨ Fonctionnalités

- 🎯 Fonctionnalité 1
- ⚡ Fonctionnalité 2
- 🔒 Fonctionnalité 3

---

## Architecture générale

---

## Structure du projet

---

## 🛠️ Stack technique

**Backend**
- Langage : Rust (edition 2021)
- Framework web : Axum / Actix-web / Rocket
- Async runtime : Tokio
- ORM / DB : SQLx / Diesel / SeaORM
- Base de données : PostgreSQL / SQLite

**Frontend** (si applicable)
- Templates : Askama / Tera / Maud
- Hydration : HTMX / Leptos / Yew

**Infra**
- Conteneurisation : Docker
- CI/CD : 
- Hébergement : 

---

## 📋 Prérequis

- Rust >= 1.75 ([rustup](https://rustup.rs))
- Cargo
- PostgreSQL (ou autre BDD configurée)
- `sqlx-cli` pour les migrations : `cargo install sqlx-cli`

---

## 🚀 Installation

```bash
# Cloner le repo
git clone https://github.com/user/repo.git
cd repo

# Copier le fichier d'environnement
cp .env.example .env

# Lancer les migrations
sqlx migrate run

# Builder
cargo build
```

---

## ⚙️ Configuration

Variables d'environnement requises dans `.env` :

```env
DATABASE_URL=postgres://user:pass@localhost/dbname
SERVER_HOST=127.0.0.1
SERVER_PORT=3000
RUST_LOG=info
```

---

## 💻 Développement

```bash
# Lancer le serveur en mode dev (avec hot-reload via cargo-watch)
cargo install cargo-watch
cargo watch -x run

# Ou simplement
cargo run

# Linter
cargo clippy -- -D warnings

# Formatter
cargo fmt
```

L'application sera disponible sur `http://localhost:3000`.

---

## 🏗️ Build & Déploiement

```bash
# Build de production (release)
cargo build --release

# Lancer le binaire de production
./target/release/<nom-du-binaire>

# Build via Docker
docker build -t mon-app .
docker run -p 3000:3000 --env-file .env mon-app
```

---

## 🧪 Tests

```bash
cargo test                    # Tous les tests
cargo test --lib              # Tests unitaires uniquement
cargo test --test integration # Tests d'intégration
cargo tarpaulin               # Couverture (nécessite cargo-tarpaulin)
```

---

## 📁 Structure du projet

```bash
.
├── src/
│   ├── main.rs
│   ├── lib.rs
│   ├── routes/
│   ├── handlers/
│   ├── models/
│   ├── db/
│   └── config.rs
├── migrations/
├── tests/
├── Cargo.toml
└── Dockerfile
```

---

## Roadmap / état actuel

---

## 🤝 Contribuer

Les contributions sont les bienvenues ! Voir [CONTRIBUTING.md](CONTRIBUTING.md).

## 👥 Contributeurs

- [@username](https://github.com/username)

## 📝 Licence

[MIT](LICENSE)
