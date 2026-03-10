# Meetus AI — Meeting Processing Bot

**SaaS Telegram bot that transforms meetings into structured insights**

![Python](https://img.shields.io/badge/Python-3.9+-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Production--Ready-brightgreen)

Turn voice meetings, audio files, and transcripts into:
- ✅ Meeting summaries
- ✅ Actionable task lists
- ✅ Decision logs
- ✅ Automated follow-ups

---

## 🎯 Features

### Core
- 🎤 **Voice Messages** — Send voice notes, bot processes instantly
- 📁 **File Support** — MP3, WAV, M4A (audio), MP4, WebM (video), TXT, PDF
- 📝 **Smart Analysis** — Multi-provider transcription with fallbacks
- ✅ **Task Extraction** — LLM-powered task identification with due dates
- 🔄 **Async Processing** — Non-blocking, production-grade concurrency

### Business  
- 💳 **Subscriptions** — Trial (3 uses) → Pro (unlimited) → Team (5 users)
- 📊 **User Tracking** — SQLite per-user subscriptions and usage logs
- 💰 **Monetization** — Built-in paywall and trial enforcement
- 🔐 **Privacy** — Files deleted after 7 days, no data selling

---

## 🚀 Quick Start

### Prerequisites
```bash
- Python 3.9+
- Telegram bot token from @BotFather
- FFmpeg: brew install ffmpeg
- OpenAI/Groq API key (optional, for transcription)
```

### Installation

```bash
git clone https://github.com/botus-ai/meetus-ai-bot.git
cd meetus-ai-bot
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

cp .env.example .env
# Edit .env with TELEGRAM_BOT_TOKEN and other keys

python3 tg_bot.py
```

---

## 📖 Usage

### Telegram Commands
- `/start` — Onboarding
- `/menu` — Command menu
- `/status` — Your subscription
- `/subscription` — Pricing

### Send Files
1. Voice message (record in Telegram)
2. Audio file (MP3, WAV, M4A)
3. Video file (MP4, WebM)
4. Document (TXT, PDF)

---

## ⚙️ Configuration

**Required:**
```env
TELEGRAM_BOT_TOKEN=123456:ABC-DEF...
MEETUS_ADMIN_ID=your_telegram_id
```

**Optional:**
```env
TRANSCRIBE_PROVIDER=auto  # or: groq, openai, local_whisper
ANALYSIS_PROVIDER=openclaw
TRIAL_LIMIT=3
MAX_FILE_SIZE_MB=50
```

---

## 💾 Database Schema

SQLite with 3 tables:
- `users` (user_id, first_name, username, created_at)
- `subscriptions` (user_id, plan, usage_count, period_start, period_end)
- `usage_log` (id, user_id, file_type, success, error_msg, processed_at)

---

## 💳 Pricing

| Tier | Price | Uses |
|------|-------|------|
| Trial | Free | 3 uses |
| Pro | 990 РУБ/month | Unlimited |
| Team | 4990 РУБ/month | 5 users |

---

## 🔐 Security

- No API keys in code (all in .env)
- Files deleted after processing
- Per-user data isolation
- Rate limiting & validation

---

## 🚀 Deployment

### Docker
```bash
docker build -t meetus-ai .
docker run -e TELEGRAM_BOT_TOKEN=xxx meetus-ai
```

### systemd (Linux)
```ini
[Unit]
Description=Meetus AI Bot
After=network.target

[Service]
Type=simple
ExecStart=/opt/meetus/venv/bin/python3 tg_bot.py
Restart=always
```

---

## 🤝 Contributing

Fork → Branch → Commit → Push → PR

---

## 📄 License

MIT License

---

**Built with ❤️ in Novosibirsk**
