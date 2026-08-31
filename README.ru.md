[English](README.md) · **Русский**

# Привет 👋

Мобильный разработчик — Flutter / Dart. Пишу не только клиент, но и бэкенд к нему:
REST на Dart (shelf) и на Python (FastAPI), PostgreSQL, Docker, CI.
Люблю задачи, где качество нужно доказывать цифрами, а не обещать.

✉️ [egzodd@gmail.com] · 💬 [tg: @egzodddd]

---

## Проекты

### 💰 Личный бюджет — Flutter + Dart backend

Кроссплатформенное приложение для учёта финансов. Монорепозиторий: клиент, сервер,
инфраструктура и документация. Весь стек поднимается одной командой `make up`.

- **Клиент:** Flutter, Clean Architecture, Riverpod, go_router, get_it, Dio
- **Офлайн-режим:** локальный кэш на sqflite, синхронизация при появлении сети
- **Безопасность:** JWT + refresh, защищённое хранилище, вход по биометрии
- **Функции:** транзакции с поиском и фильтрами, лимиты по категориям, цели с
  накоплениями, графики, экспорт в PDF и CSV, светлая/тёмная тема, локализация RU/EN
- **Сервер:** Dart + shelf, PostgreSQL 16, materialized view для агрегатов,
  soft-delete, пагинация
- **Инфраструктура:** Docker Compose, nginx, Prometheus + Grafana, GitHub Actions

→ [Репозиторий](https://github.com/EgzodD/DIPLOM_WORK_DONGY_IVT-1)

---

### 🔒 Сервис обезличивания персональных данных

Находит и заменяет ПДн в русскоязычном тексте: ФИО, телефоны, адреса, паспорт, ИНН,
СНИЛС, email, даты рождения, номера карт. Обезличивание обратимо — сохраняется
mapping, восстановление через `/deanonymize`.

- **Свой распознаватель под каждый тип ПДн.** Номера документов — regex с привязкой
  к ключевому слову рядом, телефоны и адреса — паттерны под русские форматы,
  ФИО — нейросетевая модель. Инструмент выбирается под тип, а не один на всё
- **Выбор модели по замерам.** Harness сравнения 2×2: стоковая Natasha → стоковый
  ruBERT → свой дообученный; отдельный прогон изолировал вклад дообучения
- **Дообучение под реальные ошибки:** негативы из ложных срабатываний (топонимы,
  ФИО рядом с городом) — FP 7→5 при сохранении recall 100%
- **Качество как блокирующий гейт:** регрессия LeakRate — ноль утечек ПДн
  на held-out наборе останавливает CI; состязательный QA закрыл 4 утечки
- **Безопасность:** API-ключ, HMAC-подпись вебхуков, доступ к mapping
  secure-by-default с аудитом, pip-audit блокирующим шагом
- **Модульность:** ядро автономно и не требует БД; Chatwoot и документы PDF/Word —
  адаптеры за флагами, зависимости не грузятся при выключенном флаге

→ [Репозиторий](https://github.com/EgzodD/ANONIMIZATION_MODULE)

---

## Стек

**Мобильная разработка**

<img src="https://skillicons.dev/icons?i=flutter,dart,sqlite&perline=3" alt="Flutter, Dart, SQLite" />

`Flutter` `Dart` `sqflite (offline-first)`
`Clean Architecture` `Riverpod` `flutter_test` `integration_test` `mocktail`

**Backend**

<img src="https://skillicons.dev/icons?i=python,fastapi,postgres&perline=3" alt="Python, FastAPI, PostgreSQL" />

`Python 3.12` `FastAPI` `PostgreSQL 16`
`Pydantic v2` `SQLAlchemy 2.0` `Dart` `shelf` `JWT` `HMAC`

**NLP**

`Presidio` `spaCy` `Natasha` `ruBERT (fine-tuning)` `разметка датасетов`
`метрики NER по типам` `дистилляция`

**Инфраструктура и качество**

<img src="https://skillicons.dev/icons?i=docker,githubactions,nginx,prometheus,grafana,git&perline=6" alt="Docker, GitHub Actions, nginx, Prometheus, Grafana, Git" />

`Docker` `GitHub Actions` `nginx` `Prometheus` `Grafana` `Git`
`Docker Compose` `pytest` `ruff` `pip-audit`
