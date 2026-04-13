# HealthAssist AI 🩺

A production-grade, full-stack clinical triage platform designed to assess medical symptoms, provide risk scoring, and enforce strict medical guardrails using Retrieval-Augmented Generation (RAG).

## 🏗️ Architecture

This project is split into a modern web frontend and a highly resilient, Python-driven AI engine.

* **Frontend (Next.js & Tailwind CSS):** A clean, clinical user interface featuring conversational memory, auto-scrolling, and dynamic rendering of clinical scorecards.
* **Backend (FastAPI):** A secure, rate-limited backend that intercepts user prompts and enforces medical safety.
* **Knowledge Base (ChromaDB & HuggingFace):** Local vector database that strictly grounds the AI in verified medical protocols (RAG).
* **AI Engine (OpenRouter Waterfall):** An "unkillable" routing system that automatically falls back through a tier of instruction-tuned models (`gpt-oss-20b`, `gemma-4-31b`, `nemotron-3-nano`) if upstream servers are rate-limited.

## ✨ Key Features

* **Semantic Guardrails:** Actively blocks non-medical prompts (e.g., coding requests, casual chat) and forces the AI to stay in character.
* **Unkillable Waterfall Routing:** Automatically catches `429` and `503` errors from overloaded AI APIs and seamlessly routes the request to backup models with zero frontend downtime.
* **Rate Limiting & Security:** Integrated `slowapi` to prevent bot spam and strict CORS configurations.
* **Dynamic UI Rendering:** Intelligently switches between a friendly conversational chat bubble for greetings and a full Clinical Risk Scorecard for symptom triage.
