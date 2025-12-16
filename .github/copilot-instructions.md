# Copilot / AI Agent Instructions

Purpose: short, actionable guidance to help AI coding agents become productive quickly in this repository.

**Repo-specific findings:** This repository currently contains only `.github/copilot-instructions.md`. There is no `README.md`, `CONTRIBUTING.md`, CI workflows under `.github/workflows/`, or language manifests (`package.json`, `pyproject.toml`, `go.mod`, etc.). Agents should treat the repository as “infrastructure-light” and follow the steps below to discover or request missing information.

## What to read first ✅
- **Note:** this repo currently *does not* include `README.md`, `CONTRIBUTING.md`, `docs/`, or `.github/workflows/`. If present, those files are the primary sources for high-level goals and CI commands.
- Top-level manifests to look for (none found here): `package.json` / `Makefile` / `pyproject.toml` / `go.mod` / `pom.xml`.
- Deployment/integration files to check (none found here): `Dockerfile`, `docker-compose.yml`, `infra/`, `deploy/`.

## Quick discovery checklist 🔍
1. Identify primary language and package manager from manifest files (e.g., `package.json`, `pyproject.toml`, `go.mod`).
2. Locate main runtime entrypoints: `src/`, `cmd/`, `apps/`, `server`, `index.*`.
3. Find tests and CI hooks: `tests/`, `__tests__/`, `.github/workflows/*`.
4. Search for configuration examples: `.env.example`, `config/`, `values.yaml`.

> Tip: If CI uses specific commands (e.g., `npm run ci`, `make test-all`), use those exact commands rather than guessing.

## How to run/build/test (repo-specific) 🔧
This repository currently has no discovered build or test commands because there are no language manifests, CI workflows, or source files present. For actionable steps, an AI agent should do one of the following:

- If you have write access, open an Issue requesting canonical build/test instructions and adding a `README.md` and `.github/workflows/ci.yml` that document the commands.
- When adding CI or local scripts, follow common conventions for the primary language you choose (examples below are references—only run when the matching manifest exists):
  - Node.js: `npm install` then `npm test` and `npm run lint` (if `package.json` exists)
  - Python: `python -m venv .venv; .\.venv\Scripts\Activate; pip install -r requirements.txt; pytest` (if `pyproject.toml` or `requirements.txt` exists)
  - Go: `go test ./...` (if `go.mod` exists)
- If no manifests are present and you need confirmation, contact the repo owner or open an issue asking for the expected developer workflow.

Agents should not assume commands; instead, prefer discovering manifests or asking maintainers.

## Architecture & boundaries (how to find them) 🧭
- Inspect `README.md`/`docs/` for architecture notes.
- Follow imports from top-level entrypoints to see service boundaries (e.g., `apps/api -> services/* -> libs/*`).
- Note any code-generation steps (look for `//go:generate` or `generate` scripts, `protos/` or `openapi/`).

## Project-specific patterns & conventions ✳️
- Test naming and location: follow existing patterns (`tests/`, `*_test.go`, `*.spec.ts`).
- Error-handling style: follow exactly (e.g., returning `{success: false, error}` objects vs throwing exceptions).
- Configuration overrides: prefer `ENV` vars when present; use `.env.example` as the source of truth.

## Integration points & external dependencies 🔗
- External APIs: check `integrations/` or `clients/` and mock locations in `tests/`.
- Cloud infra: `infra/`, `terraform/`, `k8s/` directories contain deployment and secret-handling patterns.
- Credentials: do not attempt to access secrets; reference `README` or `ops` docs for how maintainers run sensitive steps.

## PR guidance & checklist ✅
- Run the exact CI/test commands from `.github/workflows` locally and ensure they pass.
- Add or update tests and small, focused docs for any behavior changes.
- Keep diffs small; match existing code style and patterns exactly.
- Update `CHANGELOG.md` or release notes if applicable.

## When merging/updating this file ✏️
- Replace placeholders above with concrete commands and file references discovered in the repo.
- Keep the file concise (20–50 lines) and focused on actionable, discoverable information.

---
Feedback: I created a scaffold with placeholders for repo-specific commands and examples. Please open the repository or grant access and I will update the file with concrete examples taken from `README.md`, `.github/workflows/`, and the primary source directories.
