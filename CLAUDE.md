# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## Project Overview

AGI House Agents Hack is a multi-agent AI system built during a hackathon. It features a Next.js frontend with real-time video/audio communication via LiveKit, and a Python backend for AI agent logic including web scraping and embedding generation. The agents communicate through a real-time UI.

## Tech Stack

### Frontend
- **Language**: TypeScript
- **Framework**: Next.js 14.2.6
- **Real-time**: LiveKit SDK (@livekit/components-react, livekit-client)
- **Styling**: CSS Modules / Tailwind
- **Linting**: ESLint with Next.js config

### Backend
- **Language**: Python 3
- **Libraries**: Web scraping, embedding generation
- **No formal package manager** -- uses pip with venv

## Project Structure

```
agi-house-agents-hack/
├── frontend/
│   ├── package.json         # Next.js + LiveKit dependencies
│   ├── tsconfig.json        # TypeScript configuration
│   ├── .eslintrc.json       # ESLint config
│   ├── app/                 # Next.js App Router pages
│   ├── components/          # React components
│   └── public/              # Static assets
├── src/
│   ├── main.py              # Backend entry point
│   ├── generate_embeddings.py  # Embedding generation logic
│   └── scrape_website.py    # Web scraping logic
├── .env                     # Environment variables (gitignored)
└── .github/workflows/
    └── claude.yml           # Claude Code Actions workflow
```

## Development Commands

### Frontend
```bash
cd frontend
npm install
npm run dev               # Next.js dev server (http://localhost:3000)
npm run build
npm run lint
```

### Backend (uv)
```bash
uv sync                          # Install/sync Python dependencies
uv run python src/main.py        # Run backend agent
uv add <package>                  # Add new dependency
```

### Code Quality (ruff)
```bash
uv run ruff format .
uv run ruff check .
uv run ruff check --fix .
```


## Environment & Config

- `.env` file at project root for API keys (LiveKit, AI service keys)
- Frontend config in `frontend/tsconfig.json` and `frontend/.eslintrc.json`
- Never commit `.env` or API keys

## Code Style & Standards

- Frontend: TypeScript strict mode, ESLint with Next.js rules
- Backend: Standard Python conventions
- No shared formatter configured

## Architecture Notes

- Frontend connects to LiveKit for real-time WebRTC communication
- Backend agents handle AI tasks (embedding generation, web scraping)
- Agents and frontend communicate through the LiveKit infrastructure
- Built as a hackathon prototype -- not production-hardened

## Troubleshooting

- LiveKit connection issues: Verify LiveKit API keys in `.env`
- Frontend build errors: Run `npm install` in the `frontend/` directory
- Python import errors: Ensure venv is activated and dependencies installed
