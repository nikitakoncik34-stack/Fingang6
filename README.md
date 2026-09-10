# Finkaif v0.6 — Railway Edition

## На iPhone: как развернуть
1. Распакуйте архив и загрузите содержимое папки в новый GitHub-репозиторий.
2. В Railway: **New Project → Deploy from GitHub Repo** → выберите репозиторий.
3. В этом же Railway-проекте: **+ New → Database → PostgreSQL**.
4. Откройте PostgreSQL → Query / Data (либо подключитесь через внешний SQL-клиент) и выполните `db/schema.sql`.
5. В сервисе приложения откройте **Variables** и добавьте:
   - `DATABASE_URL=${{Postgres.DATABASE_URL}}`
   - `JWT_SECRET` — длинная случайная строка (минимум 32 символа)
   - `OPENAI_API_KEY` — секретный ключ LLM API
   - `OPENAI_MODEL=gpt-4o-mini`
   - `NODE_ENV=production`
6. Нажмите Deploy. Затем **Settings → Networking → Generate Domain**.

Откройте выданный адрес в Safari. Для установки: Поделиться → На экран «Домой».

## Важно
- Не добавляйте `.env` и API-ключи в GitHub.
- В текущем MVP нет подтверждения email и восстановления пароля; это следующий этап.
- До публичного запуска добавьте rate limiting для `/api/assistant`, CSRF-защиту, почтовый сервис, аудит, резервные копии и политику конфиденциальности.
