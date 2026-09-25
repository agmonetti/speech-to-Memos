# Speech to Memos

> Converts Telegram voice notes into text and automatically saves them to a self-hosted Memos instance.

![Python](https://img.shields.io/badge/Python-3.9-blue?style=flat&logo=python)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue?style=flat&logo=docker)
![GCP](https://img.shields.io/badge/Google_Cloud-Speech_to_Text-red?style=flat&logo=google-cloud)
![Memos](https://img.shields.io/badge/Memos-Integration-green?style=flat)

#### This bot is designed with a **Microservices Architecture** that is modular. It receives audio files, processes them to comply with Google standards (16kHz, 16-bit Mono), transcribes them using Google Cloud Speech-to-Text, and saves them to a Memos instance.

---

### Features

* **AI Transcription:** Uses Google Cloud Speech-to-Text for enterprise-level accuracy.
* **Audio Processing:** Automatic conversion from OGA (Telegram) to optimized Linear PCM WAV.
* **Privacy:** Notes are saved with `PRIVATE` visibility by default.
* **Security:** Restricted by `ALLOWED_USER_ID`. Only the person defined in the .env file can use it.

---

### Structure

```text
voice_bot/
├── src/
│   ├── main.py        # Entrypoint (Manejo de Telegram)
│   ├── config.py      # Gestión de configuración y validación 
│   └── services/      # Lógica de Negocio
│       ├── audio.py   # FFmpeg wrapper (Conversión y normalización de audios)
│       ├── gcp.py     # Cliente Google Cloud STT
│       └── memos.py   # Cliente API Memos
├── Dockerfile         # Imagen base Python + FFmpeg
├── requirements.txt   # Dependencias congeladas
└── .env.template      # Plantilla de variables de entorno
