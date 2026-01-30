# Repository Guidelines

## Project Structure & Module Organization
- Root Python entrypoint: `main.py` (CLI + workflow orchestration).
- Core modules: `paper.py`, `recommender.py`, `llm.py`, `construct_email.py`.
- Assets: `assets/` (images, logos, screenshots).
- Automation: GitHub Actions in `.github/workflows/` (`main.yml`, `test.yml`, `keep-alive.yml`).
- Containerization: `Dockerfile`, `docker-compose.yml`.

## Build, Test, and Development Commands
- Local run (recommended): `uv run main.py`  
  Runs the workflow using dependencies from `pyproject.toml`.
- Docker run: `docker compose up --build`  
  Builds the image and starts the cron-driven container.
- GitHub Actions: trigger `.github/workflows/test.yml` or `main.yml` in the GitHub UI  
  Useful for validating the scheduled workflow behavior.

## Coding Style & Naming Conventions
- Language: Python 3.11+ (see `pyproject.toml`).
- Indentation: 4 spaces (match existing files like `main.py`).
- Naming: snake_case for functions/variables; PascalCase for classes.
- Formatting: no enforced formatter/linter in repo—keep changes consistent with adjacent code.

## Testing Guidelines
- No dedicated unit test suite in this repository.
- Validate changes by running `uv run main.py` locally or the GitHub Actions test workflow.
- If you add tests, place them under a new `tests/` directory and document how to run them.

## Commit & Pull Request Guidelines
- Commit style follows conventional-ish prefixes (`feat:`, `fix:`, `chore:`) in recent history.
- PRs should target the `dev` branch (per README).
- Include: clear description, rationale, and any behavior changes. Add screenshots/log snippets for email output or workflow changes when relevant.

## Configuration & Secrets
- Required secrets/vars are documented in `README.md` (e.g., `ZOTERO_ID`, `ZOTERO_KEY`, SMTP settings).
- Do not commit secrets. Prefer `.env` locally and GitHub Actions secrets/variables in CI.
