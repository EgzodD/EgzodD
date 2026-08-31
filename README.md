**English** · [Русский](README.ru.md)

# Hi 👋

Mobile developer — Flutter / Dart. I build the client and the backend behind it:
REST APIs in Dart (shelf) and Python (FastAPI), PostgreSQL, Docker, CI.
I like problems where quality has to be proven with numbers rather than promised.

✉️ [email] - egzodd@gmail.com · 💬 [@telegram] - @egzodddd

---

## Projects

### 💰 Personal Budget — Flutter + Dart backend

Cross-platform personal finance app. A monorepo holding the client, the server,
infrastructure and docs. The whole stack comes up with a single `make up`.

- **Client:** Flutter, Clean Architecture, Riverpod, go_router, get_it, Dio
- **Offline mode:** local sqflite cache, syncs once connectivity returns
- **Security:** JWT + refresh, secure storage, biometric login
- **Features:** transactions with search and filters, per-category budgets, savings
  goals, charts, PDF and CSV export, light/dark themes, RU/EN localization
- **Server:** Dart + shelf, PostgreSQL 16, materialized view for aggregates,
  soft delete, pagination
- **Infrastructure:** Docker Compose, nginx, Prometheus + Grafana, GitHub Actions

→ [Repository](https://github.com/EgzodD/DIPLOM_WORK_DONGY_IVT-1)

---

### 🔒 PII Anonymization Service

Detects and replaces personal data in Russian-language text: full names, phone
numbers, addresses, passport numbers, tax IDs (INN), social insurance numbers
(SNILS), emails, dates of birth, card numbers. Anonymization is reversible — the
mapping is kept and the original is restored through `/deanonymize`.

- **A dedicated recognizer per data type.** Document numbers are matched by regex
  anchored to a nearby keyword; phones and addresses by patterns tuned to Russian
  formats; names by a neural model. The tool is picked per entity type instead of
  one model covering everything
- **Model choice driven by measurement.** A 2×2 evaluation harness compared stock
  Natasha → stock ruBERT → my fine-tuned ruBERT, with a separate run isolating the
  contribution of fine-tuning itself
- **Fine-tuned against real errors:** negatives drawn from actual false positives
  (place names, a person's name next to a city) cut false positives from 7 to 5
  while keeping 100% recall
- **Quality as a blocking gate:** a LeakRate regression test — zero PII leaks on a
  held-out set — fails the CI build; adversarial QA closed 4 leaks
- **Security:** API key auth, HMAC-signed webhooks, secure-by-default mapping access
  with an audit trail, pip-audit as a blocking CI step
- **Modular:** the core runs standalone with no database; Chatwoot and PDF/Word
  handling are feature-flagged adapters whose dependencies stay unloaded when off

→ [Repository](https://github.com/EgzodD/ANONIMIZATION_MODULE)


---

## Stack

**Mobile**

<img src="https://skillicons.dev/icons?i=flutter,dart,sqlite&perline=3" alt="Flutter, Dart, SQLite" />

`Flutter` `Dart` `sqflite (offline-first)`
`Clean Architecture` `Riverpod` `flutter_test` `integration_test` `mocktail`

**Backend**

<img src="https://skillicons.dev/icons?i=python,fastapi,postgres&perline=3" alt="Python, FastAPI, PostgreSQL" />

`Python 3.12` `FastAPI` `PostgreSQL 16`
`Pydantic v2` `SQLAlchemy 2.0` `Dart` `shelf` `JWT` `HMAC`

**NLP**

`Presidio` `spaCy` `Natasha` `ruBERT (fine-tuning)` `dataset annotation`
`per-entity NER metrics` `distillation`

**Infrastructure & quality**

<img src="https://skillicons.dev/icons?i=docker,githubactions,nginx,prometheus,grafana,git&perline=6" alt="Docker, GitHub Actions, nginx, Prometheus, Grafana, Git" />

`Docker` `GitHub Actions` `nginx` `Prometheus` `Grafana` `Git`
`Docker Compose` `pytest` `ruff` `pip-audit`
