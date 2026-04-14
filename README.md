# NewsSphereAI 🎧

> A personalized, AI-powered news digest platform with audio playback — built with Airflow, OpenAI, Pinecone, FastAPI, and Streamlit.

![Tech Stack](https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Airflow](https://img.shields.io/badge/Apache%20Airflow-017CEE?style=for-the-badge&logo=apache-airflow&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Docker](https://img.shields.io/badge/Docker-0db7ed?style=for-the-badge&logo=docker&logoColor=white)
![Pinecone](https://img.shields.io/badge/Pinecone-000000?style=for-the-badge)
![GCP](https://img.shields.io/badge/Google%20Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)

---

## What it does

NewsSphereAI lets users stay informed without the noise. After registering and selecting interest categories (Business, Environment, US News, etc.), users get a personalized feed of the top 5 articles per category — summarized by OpenAI and available to **read or listen to** via text-to-speech.

Key capabilities:
- **Personalized feed** — articles filtered and ranked by user interest categories
- **AI summarization** — OpenAI condenses full articles into digestible summaries
- **Audio playback** — listen to any article via integrated text-to-speech
- **Playlist management** — save articles to named playlists stored in Azure SQL
- **Queueing** — temporary article queue for on-the-fly listening without storage
- **Real-time ingestion** — Airflow DAG runs every 8 minutes, ingesting only new/changed articles from Google News, BBC, NY Times, and more

---

## Architecture

![Architecture Diagram](images/Newsphere_Data_Architecture.png)

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Streamlit |
| Backend API | FastAPI + JWT Auth |
| Orchestration | Apache Airflow |
| AI / Summarization | OpenAI GPT |
| Vector Search | Pinecone |
| Database | Azure SQL |
| Containerization | Docker |
| Deployment | Google Cloud Platform (GCP) |

---


## My Contributions

This was a 3-person team project. My primary ownership areas:

- **Text-to-Speech integration** — implemented audio playback for all articles using OpenAI's TTS API, wired into the Streamlit player UI
- **Speech-to-Text** — voice input for article search and queue management
- **Streamlit frontend** — designed and built the full user-facing UI including article cards, category filters, and playback controls
- **Playlist feature** — end-to-end implementation of create/read/update/delete playlist functionality, from FastAPI endpoints to UI
- **Pinecone indexing** — contributed to embedding and indexing article vectors for semantic search and personalized recommendations
- **Azure SQL storage** — helped design and implement the database schema for storing articles, user preferences, and playlist data

---

## Project Structure

```
NewsSphereAI/
├── airflow/          # DAGs for news ingestion pipeline
├── fastapi/          # Backend API with JWT auth, playlists, article endpoints
├── streamlit/        # Frontend UI — article feed, audio player, playlists
├── images/           # Architecture and repo structure diagrams
└── docker-compose.yml
```

---

## Getting Started

### Prerequisites
- Python 3.9+
- Docker & Docker Compose
- OpenAI API key
- Pinecone API key
- Azure SQL connection string

### Setup

```bash
git clone https://github.com/shardulchavan/NewsSphereAI
cd NewsSphereAI

# Copy and fill in your environment variables
cp .env.example .env

# Start all services
docker-compose up --build
```

Then open:
- Streamlit app: `http://localhost:8501`
- FastAPI docs: `http://localhost:8000/docs`
- Airflow UI: `http://localhost:8080`

---

## Demo

📺 [Watch the demo video](https://www.youtube.com/watch?v=hqx6lcAuugc)

---

## Live Links (may be inactive)

- Google collab notebook (POC): https://colab.research.google.com/drive/1-u0u6Ib5aPGprUhVwmp_Yj_Ie-FEaNgi?usp=sharing

- Google codelab: [https://codelabs-preview.appspot.com/?file_id=1Ih2p01AQZP2_p7pM-CWIECQJQams-EnPEwdwYNav838#0](https://codelabs-preview.appspot.com/?file_id=1tJ3JqcmwDDNBPkk97BcidnZiWHzzjm5QJaESpIeejAw#0)

- Streamlit app: https://bigdatateam2-finalproject.streamlit.app/
- GCP deployment: http://34.118.251.190:8501/

---

## Team

| Name | Contributions |
|---|---|
| **Shardul Chavan** | Pinecone Indexing, Azure Storage, Text-to-Speech, Speech-to-Text, Streamlit UI, Playlist feature |
| Chinmay Gandi | Airflow pipeline, Pinecone integration, Azure storage |
| Dhawal Negi | JWT auth, Docker, GCP deployment, FastAPI |
