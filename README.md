# Aurora — Mental Health Support Platform

A Flask-based web app that provides mental health support through an AI chatbot, mood tracking, journaling, and a directory of mental health professionals.

## Features

- 💬 **AI Chatbot** — Streams responses from a local DeepSeek model (privacy-first, no cloud API)
- 📊 **Mood Tracker** — Log daily mood (1–10) with notes and visualize trends over time
- 📝 **Journal** — Create, edit, and delete journal entries with streak tracking
- 🏥 **Professionals Directory** — Browse psychologists, psychiatrists, and counselors
- 👥 **Community** — Forums, support groups, and events
- 📋 **Dashboard** — Overview of your activity, goals, and progress
- 🔐 **Auth** — Register and login with secure password hashing

## Tech Stack

- **Backend:** Python, Flask, SQLAlchemy, SQLite
- **Frontend:** Jinja2, Bootstrap, Chart.js, Vanilla JS
- **AI:** DeepSeek-R1 7B via [Ollama](https://ollama.ai) (runs locally)

## Getting Started

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Set up the AI model (required for chat)
```bash
# Install Ollama from https://ollama.ai, then:
ollama pull deepseek-r1:7b
ollama serve
```

### 3. Run the app
```bash
# macOS — port 5000 is blocked by AirPlay, use 5001
FLASK_APP=app.py flask run --port 5001
```

Then open [http://127.0.0.1:5001](http://127.0.0.1:5001)

### 4. Optional: Environment variables
Create a `.env` file in the project root:
```
SECRET_KEY=your-secret-key
DATABASE_URL=sqlite:///mental_health.db
```

## Project Structure

```
├── app.py                  # App factory, blueprint registration
├── config.py               # Dev/Test/Prod configuration
├── db.py                   # SQLAlchemy instance
├── controllers/            # Route handlers (one per feature)
├── models/                 # Database models
├── services/               # AI service (DeepSeek streaming)
├── templates/              # Jinja2 HTML templates
├── static/                 # CSS, JS, images
└── data/                   # Static JSON (professionals, resources)
```

## Notes

- The chat feature requires Ollama running locally on port `11434`
- Database is auto-created as `instance/mental_health.db` on first run
- Community and booking features use sample data (DB integration in progress)
