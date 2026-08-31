[English](README.md) · **Русский**

# Привет 👋

Мобильный разработчик — Flutter / Dart. Пишу не только клиент, но и бэкенд к нему:
REST на Dart (shelf) и на Python (FastAPI), PostgreSQL, Docker, CI.
Люблю задачи, где качество нужно доказывать цифрами, а не обещать.

✉️ [почта] · 💬 [@telegram]

---

## Проекты

### 💰 Личный бюджет — Flutter + Dart backend

Кроссплатформенное приложение для учёта финансов. Монорепозиторий: клиент, сервер,
инфраструктура и документация. Весь стек поднимается одной командой `make up`.

- **Клиент:** Flutter, Clean Architecture, Riverpod, go_router, get_it, Dio
- **Офлайн-режим:** локальный кэш на sqflite, синхронизация при появлении сети
- **Безопасность:** JWT + refresh, flutter_secure_storage, вход по биометрии (local_auth)
- **Функции:** транзакции с поиском и фильтрами, лимиты по категориям, цели с
  накоплениями, графики на fl_chart, экспорт в PDF и CSV, светлая/тёмная тема,
  локализация RU/EN
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
`Flutter` `Dart` `Riverpod` `go_router` `get_it` `Dio` `Clean Architecture`
`sqflite` `flutter_secure_storage` `shared_preferences` `connectivity_plus`
`Material 3` `fl_chart` `intl (RU/EN)` `local_auth` `share_plus`
`flutter_test` `integration_test` `mocktail`
`Android (Java, Gradle)` — базовый уровень

**Backend**
`Python 3.12` `FastAPI` `Uvicorn` `Pydantic v2` `SQLAlchemy 2.0` `PostgreSQL 16`
`Dart` `shelf` `JWT` `PBKDF2 / HMAC` `REST`

**NLP**
`Presidio` `spaCy` `Natasha` `ruBERT (fine-tuning)` `разметка датасетов`
`метрики NER по типам` `дистилляция`

**Инфраструктура и качество**
`Docker` `Docker Compose` `GitHub Actions` `nginx` `Prometheus` `Grafana` `Makefile` `Git`
`pytest` `ruff` `flutter_lints` `pip-audit`

---

## Сейчас

Углубляюсь в мобильную разработку — тестирование, производительность, платформенный код.
Параллельно продолжаю NLP: интересна обработка русского текста под ограничения по железу.
