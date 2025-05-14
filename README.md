# Multi-Agent Contact Center Support System

## 🧾 Описание

Мультиагентная система для поддержки операторов контакт-центра. Все компоненты запускаются в контейнерах Docker.

Проект включает:

- **FastAPI** — бэкенд-часть
- **React** — фронтенд-интерфейс
- **Qdrant** — векторное хранилище
- **CrewAI** — система для запуска агентов
- **6 агентов** с индивидуальными SOP (Standard Operating Procedures)
- **Agent Knowledge** — агент с доступом к базе знаний через эмбединги

---

## Технологии

- Python 3.10+
- FastAPI
- React
- Docker + Docker Compose
- Qdrant
- CrewAI
- Langchain / OpenAI / Embeddings

---

## Запуск проекта

### 1. Клонирование репозитория

```bash
git clone "git@github.com:LLM-MTS/devops.git"

cd devops

git clone "git@github.com:LLM-MTS/backend.git"
git clone "git@github.com:LLM-MTS/frontend.git"
```

### 2. Запуск через Docker

```bash
docker-compose up --build
```

Это поднимет следующие сервисы:

- `backend` — FastAPI сервер
- `frontend` — React интерфейс
- `qdrant` — база векторов
- `agents` — модуль мультиагентов
  
При запуске бэкенда какое-то время будут создаваться эмбеддинги и подгружаться модель.

### 3. Проверка

- Бэкенд: [http://localhost:8000/docs](http://localhost:8000/docs)
- Фронтенд: [http://localhost:3000](http://localhost:3000)
- Qdrant UI (если подключена): [http://localhost:6333](http://localhost:6333)

---

## Мультиагенты

В системе настроены 6 агентов, каждый с индивидуальным SOP:

- `AgentIntent` — определяет намерение клиента
- `AgentEmotion` — анализирует эмоции по сообщению
- `AgentSummary` — делает автосводку диалога
- `AgentSuggestion` — предлагает действия оператору
- `AgentKnowledge` — отвечает на вопросы на основе базы знаний
- `AgentQuality` — управляет качеством обработки

### AgentKnowledge

Использует:

- **Qdrant** как векторное хранилище
- **Embeddings** сгенерированные на основе собранного датасета для поиска по знаниям (существующие кейсы)

---

## Настройки

Переменные окружения задаются в `.env` файле:

```env
LITELLM_PROVIDER=openai
HUGGINGFACE_API_TOKEN=...

GROQ_TOKEN=...

QDRANT_URL=http://localhost:6333
QDRANT_COLLECTION=knowledge_collection
QDRANT_VECTOR_NAME=embedding
QDRANT_TOP_K=3
```

---

## Структура проекта

```
.
├── backend/
│   ├── src/
│   │   ├── agents/
│   │   ├── embedding/
│   │   ├── crew.py
│   ├── Dockerfile
│   ├── main.py
│   ├── README.md
│   ├── requirements.txt
├── frontend/
├── .env
├── .gitignore
├── compose.yaml
└── README.md
```

---


## 📄 Лицензия

MIT License. Свободное использование.