# 📰 News Digest Generator

![Python 3.11+](https://img.shields.io/badge/Python-3.11%2B-3776AB?style=flat-square&logo=python&logoColor=white) ![MIT License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square) ![Gemma 4](https://img.shields.io/badge/Gemma_4-Google-4285F4?style=flat-square&logo=google&logoColor=white) ![Privacy-First](https://img.shields.io/badge/Privacy--First-100%25_Local-8b5cf6?style=flat-square) ![Ollama](https://img.shields.io/badge/Ollama-Powered-000000?style=flat-square&logo=ollama&logoColor=white)

**Turn a folder of news articles into a structured, categorized digest with sentiment analysis and trend detection — all processed 100 % locally on your machine.**

---

## Architecture

```
┌──────────────────────────────────────────────────┐
│             News Digest Generator                │
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────────┐   │
│  │   CLI    │  │  Web UI  │  │  REST API    │   │
│  │  (Click) │  │(Streamlit)│  │  (FastAPI)   │   │
│  └────┬─────┘  └────┬─────┘  └──────┬───────┘   │
│       └──────────────┼───────────────┘           │
│              ┌───────┴───────┐                   │
│              │  Core Engine  │                   │
│              │ read_files()  │                   │
│              │ categorize()  │                   │
│              │ digest()      │                   │
│              │ sentiment()   │                   │
│              └───────┬───────┘                   │
│              ┌───────┴───────┐                   │
│              │  Ollama LLM   │                   │
│              │   (Gemma 4)   │                   │
│              └───────────────┘                   │
│  ┌───────────────────────────────────────────┐   │
│  │  Input: .txt files  │  Output: .md digest │   │
│  └───────────────────────────────────────────┘   │
└──────────────────────────────────────────────────┘
```

---

## ✨ Key Features

- **Smart Categorization** — auto-groups articles into N topic categories with names, article lists, and summaries
- **Daily & Weekly Digests** — generates professional digests with key headlines, topic summaries, and outlook
- **Sentiment Analysis** — per-article sentiment scoring (positive / negative / neutral) with explanations
- **Trend Detection** — surfaces overarching themes and emerging trends across all articles
- **8 Built-in Categories** — Technology, Business, Politics, Science, Sports, Health, Entertainment, World
- **Configurable Topic Count** — request any number of topic groups; auto-adjusts if fewer articles exist
- **File-Based Input** — drop .txt articles into a folder and run a single CLI command
- **Markdown Export** — save the full digest (categorization + summary) to a Markdown file
- **FastAPI REST API** — /categorize, /digest, and /sentiment endpoints for programmatic use
- **100 % Local & Private** — no cloud APIs, no data leaves your network

---

## 🚀 Quick Start

### Prerequisites

| Requirement | Version |
|-------------|---------|
| Python      | 3.11+   |
| Ollama      | latest  |
| Gemma 4 model | pulled via Ollama |

### Installation

```bash
git clone https://github.com/kennedyraju55/news-digest-generator.git
cd news-digest-generator
pip install -r requirements.txt
ollama pull gemma4
```

### Run

```bash
# CLI — generate a daily digest from a folder of .txt articles
python -m src.news_digest.cli --sources ./news_articles --topics 5

# CLI — weekly digest with sentiment analysis
python -m src.news_digest.cli --sources ./news_articles --format weekly --sentiment

# CLI — save output to file
python -m src.news_digest.cli --sources ./news_articles --output digest.md

# Web UI
streamlit run src/news_digest/web_ui.py

# REST API
uvicorn src.news_digest.api:app --host 0.0.0.0 --port 8018

# Docker
docker compose up
```

---

## 🛠️ Tech Stack

| Component        | Technology             |
|------------------|------------------------|
| Language         | Python 3.11+           |
| LLM              | Gemma 4 via Ollama     |
| CLI Framework    | Click + Rich           |
| Web UI           | Streamlit              |
| REST API         | FastAPI + Uvicorn      |
| Output Format    | Markdown               |
| Configuration    | YAML (config.yaml)     |
| Containerization | Docker + Docker Compose|
| Testing          | pytest + pytest-cov    |

---

## 📁 Project Structure

```
news-digest-generator/
├── src/news_digest/
│   ├── core.py        # Article reading, categorization, digest, sentiment
│   ├── cli.py         # Click CLI with Rich console output
│   ├── web_ui.py      # Streamlit web interface
│   ├── api.py         # FastAPI REST endpoints
│   ├── utils.py       # Logging, sys path setup, header formatting
│   └── config.py      # YAML config loader
├── common/            # Shared LLM client
├── tests/             # pytest test suite
├── config.yaml        # Default configuration
├── requirements.txt   # Python dependencies
├── Dockerfile         # Container build
└── docker-compose.yml # Multi-service orchestration
```

---

## 👤 Author

**Nrk Raju Guthikonda**

- GitHub: [kennedyraju55](https://github.com/kennedyraju55)
- Dev.to: [https://dev.to/kennedyraju55](https://dev.to/kennedyraju55)
- LinkedIn: [https://www.linkedin.com/in/nrk-raju-guthikonda-504066a8/](https://www.linkedin.com/in/nrk-raju-guthikonda-504066a8/)

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
