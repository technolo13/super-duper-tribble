# Copilot / AI Agent Instructions

Purpose: short, actionable guidance to help AI coding agents become productive quickly in this repository.

## What to read first ✅
- `README.md`, `CONTRIBUTING.md`, `docs/` — high-level goals and architecture notes.
- `.github/workflows/` — exact build/test/lint commands used in CI.
- Top-level manifests: `package.json` / `Makefile` / `pyproject.toml` / `go.mod` / `pom.xml` etc.
- `Dockerfile`, `docker-compose.yml`, `infra/`, `deploy/` — deployment/integration points.

## Quick discovery checklist 🔍
1. Identify primary language and package manager from manifest files (e.g., `package.json`, `pyproject.toml`, `go.mod`).
2. Locate main runtime entrypoints: `src/`, `cmd/`, `apps/`, `server`, `index.*`.
3. Find tests and CI hooks: `tests/`, `__tests__/`, `.github/workflows/*`.
4. Search for configuration examples: `.env.example`, `config/`, `values.yaml`.

> Tip: If CI uses specific commands (e.g., `npm run ci`, `make test-all`), use those exact commands rather than guessing.

## How to run/build/test (fill concrete commands) 🔧
- Unit tests: replace with CI command, e.g., `npm test` or `make test`.
- Linting: e.g., `npm run lint` / `flake8` / `golangci-lint run`.
- Local dev: e.g., `npm start`, `docker-compose up`, or `go run ./cmd/service`.

(Contributors: please replace these placeholders with the exact commands the repo uses.)

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
