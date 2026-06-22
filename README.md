# ImageGen

> **Archived:** I built this small React and Express application for a personal image-generation workflow that I no longer use. It is kept as a record of that project and is not under active development.

ImageGen generates and edits images through OpenAI's image API and keeps a separate local history for each reverse-proxy user.

## Technology

- React, Vite and Tailwind CSS
- Node.js and Express
- Local JSON history rather than a database
- Nginx Basic Authentication

## Running it

Start the frontend:

```bash
cd frontend
npm install
npm run dev
```

Start the backend in another terminal:

```bash
cd backend
cp .env.example .env
npm install
node server.js
```

Add an OpenAI API key to `backend/.env`. The frontend defaults to `http://localhost:5173`; the backend listens on `http://127.0.0.1:3001`.

## Authentication boundary

The application has no login screen. Its original deployment used Nginx Basic Authentication, with Nginx passing the authenticated username in `X-User`.

The backend trusts that header. It must therefore remain behind a proxy that removes any client-supplied `X-User` value and replaces it with the authenticated username.

## Licence

MIT
