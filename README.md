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
git clone https://git.truetecharena.ru/true-tech-hack-15/truetecharena1745056424-team-12681/zadacha-168.git
cd zadacha-168
```

### 2. Запуск через Docker

```bash
docker-compose up --build
```
запуск фронта в соседнем териминале после запуска бд
```bash
cd front
npm install
npm start
```

в соседнем териминале после запуска бд и фронта
```bash
python3.12 -m venv venv
source venv/bin/activate
pip install -r back/requirements.txt
python back/src/main.py
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
MWS_API_KEY=sk-KNo006G2a48UVE3IxFlQEQ
MWS_BASE_URL=https://api.gpt.mws.ru/v1

OPENAI_API_KEY=sk-KNo006G2a48UVE3IxFlQEQ
OPENAI_API_BASE=https://api.gpt.mws.ru/v1

LITELLM_PROVIDER=openai
QDRANT_API_KEY=QDRANT_API_KEY
```

---

## Структура проекта

```
.
├── backend/
├── frontend/
├── agents/
├── qdrant/
├── docker-compose.yml
├── .env
└── README.md
```

---


## 📄 Лицензия

MIT License. Свободное использование.