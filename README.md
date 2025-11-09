# 🤖 MM-V2 — AI-Powered Mock Interview App

> A local AI-driven mock interview web application that helps users practice real interviews.  
> Generates questions, records spoken answers, evaluates them using AI, and provides spoken feedback — all in one place.  
> Built with **Next.js**, **TailwindCSS**, **Express**, **MongoDB**, **AssemblyAI (STT)**, **ElevenLabs (TTS)**, and **Groq (Evaluation + Question Generation)**.

---

## 🔗 Repository Structure


mm-v2/
├── app/ # Next.js frontend (TypeScript)
│ ├── components/
│ ├── app/ or pages/
│ └── package.json
├── my-auth-backend/ # Express backend (Auth + AI Routes)
│ ├── routes/
│ ├── controllers/
│ └── package.json
├── prisma/ # Database models (if used)
├── public/ # Static assets
├── styles/ # Tailwind styles
└── README.md

> Project currently runs locally (not deployed).

---

## 📖 Overview

**MM-V2** is a full-stack mock interview platform that simulates a real interview experience.  
Users can log in, choose their preferred **role** and **difficulty level**, and answer questions via **speech**.  
The system then evaluates their responses using AI and provides instant feedback — both in text and voice format.

---

## ✨ Features

- 🧠 **Dynamic Interview Generation** — Groq generates domain- and level-specific questions.
- 🗣️ **Speech-to-Text (STT)** — Uses **AssemblyAI** to transcribe user voice input.
- 💬 **Automated Evaluation** — Groq API analyzes user answers and provides feedback.
- 🔊 **Text-to-Speech (TTS)** — ElevenLabs generates realistic audio feedback.
- 🔐 **JWT Authentication** — Secure login and user session management.
- 💾 **MongoDB Integration** — Saves user sessions, scores, and feedback data.
- 🎨 **Modern UI** — Built with TailwindCSS and responsive layout.
- ⚡ **Local-first Architecture** — Fully functional on a local setup.

---

## 🧠 System Workflow

1. User registers or logs in (JWT-based).
2. Selects **role** (e.g., Frontend, ML Engineer) and **difficulty level**.
3. System fetches relevant interview questions (via **Groq**).
4. User answers verbally → audio sent to backend.
5. Backend uses **AssemblyAI** to convert speech → text.
6. Text answer sent to **Groq** for evaluation → feedback generated.
7. Feedback sent to **ElevenLabs** → audio generated and played back.
8. Session data (questions, responses, feedback, scores) saved to **MongoDB**.

---

## 🧩 Tech Stack

| Layer | Technologies |
|-------|---------------|
| **Frontend** | Next.js, React, TailwindCSS |
| **Backend** | Node.js, Express |
| **Database** | MongoDB (Mongoose / Prisma) |
| **AI APIs** | AssemblyAI (Speech-to-Text), ElevenLabs (Text-to-Speech), Groq (Evaluation + QG) |
| **Authentication** | JWT |
| **Deployment (Local)** | Node.js + Next.js dev servers |

---

## ⚙️ Environment Variables

Create `.env` files in both the backend and frontend directories with the following keys:

### Backend (`my-auth-backend/.env`)
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=super_secret_jwt_key
PORT=5000

AI API Keys

ASSEMBLY_API_KEY=your_assemblyai_key
GROQ_API_KEY=your_groq_api_key
ELEVEN_API_KEY=your_elevenlabs_key
ELEVEN_VOICE_ID=preferred_voice_id

### Frontend (`app/.env.local`)
NEXT_PUBLIC_API_BASE=http://localhost:5000/api


> ⚠️ Keep API keys private. Do **not** expose them with `NEXT_PUBLIC_` unless necessary.

---

## 🚀 Setup & Installation

### 1️⃣ Clone the repository
```bash
git clone https://github.com/Bharathreddy374/mm-v2.git
cd mm-v2

cd my-auth-backend
npm install
# Add your environment variables in .env
npm run dev   # or: node index.js

cd ../app
npm install
npm run dev
```

| Method | Endpoint                                  | Description                                    |
| ------ | ----------------------------------------- | ---------------------------------------------- |
| `POST` | `/api/auth/register`                      | Register new user                              |
| `POST` | `/api/auth/login`                         | Login and get JWT                              |
| `GET`  | `/api/questions?role=frontend&level=easy` | Get AI-generated questions                     |
| `POST` | `/api/ai/stt`                             | Convert audio → text using AssemblyAI          |
| `POST` | `/api/ai/evaluate`                        | Evaluate text answer with Groq                 |
| `POST` | `/api/ai/tts`                             | Convert feedback text → voice using ElevenLabs |


)

🧱 Future Enhancements

📊 Add analytics dashboard for progress tracking.

🗂️ Cloud storage for user recordings (AWS S3 / Firebase).

🧩 Real-time streaming STT for instant feedback.

🔍 Expand Groq prompt library with domain-based models.

🧠 Adaptive difficulty adjustment based on past scores.

👨‍💻 Author

P Bharath Reddy
📧 bharathreddy372k4@gmail.com
