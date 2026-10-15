# Barber-AI

Учебный AI-администратор барбершопа «Бритва»: Gradio, Gemini, база знаний и запись клиентов.

## Деплой на Render

1. New → Web Service → подключить репозиторий Lliga12/Barber-AI.
2. Runtime: Python. Branch: main. Root Directory: оставить пустым.
3. Build Command: `pip install -r requirements.txt`.
4. Start Command: `python 05-example_bot/bot.py`.
5. Instance Type: Free.
6. Environment: `PYTHON_VERSION=3.12.6`, `GOOGLE_API_KEY=ваш_ключ`.
7. Deploy Web Service. После успешного запуска открыть ссылку сервиса.

Также можно создать Blueprint из render.yaml: команды уже заданы, ключ вводится в панели Render.

Ключ Gemini хранить только в Environment на Render либо локальном .env; не загружать в GitHub.
Без GOOGLE_API_KEY интерфейс запустится, но модель не сможет отвечать.

## Хранение записей

Без DATABASE_URL записи сохраняются в 05-example_bot/leads.json. На бесплатном Render они могут пропасть при перезапуске или деплое.
Для постоянного хранения позже можно добавить DATABASE_URL с адресом Postgres. Бот сам создаёт таблицу leads.

## Локальный запуск в Windows

```powershell
uv venv
uv pip install -r requirements.txt
```

Создать .env со строкой GOOGLE_API_KEY=ваш_ключ, затем:

```powershell
uv run 05-example_bot/bot.py
```

Для локальной Ollama в bot.py переключить PROVIDER на "ollama". Потребуется модель qwen2.5.
