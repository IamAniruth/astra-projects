# Setup and installation from scratch

Status: optional appendix retained from the initial planning draft; commands have not been run. The requested deliverable is the [PI/sprint documentation](../PI/README.md). S01/S07 must first confirm which optional product infrastructure is needed. Nothing here installs or modifies Astra; its existing runtime and locked profiles are reused through the [Astra integration plan](11-astra-llm-feature-mapping.md).

## 1. Prerequisites

Install Git, an editor, Docker Desktop with the required virtualization/WSL support on Windows, and a supported Node.js LTS release. Proposed starting baseline: Node.js 24 LTS, after checking current support and selected tool compatibility. Do not choose an obsolete runtime just because a framework accepts its minimum version.

Install pnpm through its documented installation method and record the exact resolved version. Existing LLM installation can be reused; first identify the runner, model name/digest, RAM, GPU, and commercial-use terms. An LLM is not needed for the initial UI and API setup: use a deterministic development mock until S08.

Verify in PowerShell:

```powershell
git --version
node --version
npm --version
pnpm --version
docker version
docker compose version
```

A GPU is not required for React/Next.js development. Model capacity is not estimated until measured.

## 2. Create application source separately from these plans

From the project planning folder, create a future `application` directory. Stop and inspect if it already contains code. This document does not authorize overwriting an existing application.

```powershell
New-Item -ItemType Directory -Path application
Set-Location application
New-Item -ItemType Directory -Path apps, packages, infra, tests
```

Create a private root `package.json` with a chosen name and `packageManager` pinned to the exact pnpm version from step 1. Create `pnpm-workspace.yaml`:

```yaml
packages:
  - 'apps/*'
  - 'packages/*'
```

Scaffold only once:

```powershell
pnpm create vite@latest apps/web --template react-ts
pnpm create next-app@latest apps/api
```

For Next.js choose TypeScript, ESLint, App Router, and a src directory. UI styling options in the API scaffold are unnecessary. Keep its generated minimal layout/page if present; actual business endpoints live under `src/app/api`. Inspect generated project instructions before editing.

The use of `latest` is limited to first-time scaffolding. Record installed versions, commit one workspace lockfile, and pin runtime/package-manager versions. Future installations use `pnpm install --frozen-lockfile`.

Create `apps/worker` and the shared package manifests manually as described in the architecture. Mark Node packages as ESM if using ESM imports and use a compatible TypeScript module strategy. Do not mix unresolved workspace imports with production Node execution.

## 3. Add dependencies as modules are introduced

Run from the application root, after the relevant package manifests exist:

```powershell
pnpm --dir apps/web add react-router-dom @tanstack/react-query react-hook-form @hookform/resolvers zod i18next react-i18next
pnpm --dir apps/api add better-auth zod
pnpm --dir packages/db add drizzle-orm pg
pnpm --dir packages/db add -D drizzle-kit @types/pg
pnpm --dir packages/domain add decimal.js
pnpm --dir packages/contracts add zod
pnpm --dir apps/worker add bullmq ioredis dotenv
pnpm --dir apps/worker add -D typescript tsx @types/node
pnpm add -Dw vitest @playwright/test
```

Add Testing Library to the frontend when component testing begins. Add provider SDKs, document parsing, and PDF dependencies only after their adapters are selected. The API-side enqueue/dispatcher package also needs BullMQ when introduced in S07.

Review versions and package install scripts rather than assuming these names form a tested release set. After adding dependencies, run `pnpm install` at the workspace root and resolve duplicate/nested lockfiles before committing.

## 4. Local database and queue

Copy the supplied examples into the future application:

```powershell
Copy-Item -LiteralPath '../templates/compose.dev.yaml' -Destination 'infra/compose.dev.yaml'
Copy-Item -LiteralPath '../templates/.env.infra.example' -Destination 'infra/.env'
Copy-Item -LiteralPath '../templates/.env.api.example' -Destination 'apps/api/.env.local'
Copy-Item -LiteralPath '../templates/.env.worker.example' -Destination 'apps/worker/.env'
```

Replace placeholder passwords/secrets locally and keep DB URLs consistent. Add `.env`, `.env.*` (except examples), local document folders, generated artifacts, and logs to `.gitignore`.

```powershell
docker compose --env-file infra/.env -f infra/compose.dev.yaml up -d
docker compose --env-file infra/.env -f infra/compose.dev.yaml ps
```

The example exposes database/Redis ports only on localhost and is for development. It does not include production authentication, backup configuration, or hardened networking. Do not run destructive volume-reset commands against shared data.

## 5. Database and environment wiring

Create Drizzle schemas and `drizzle.config.ts` in `packages/db`. Load an explicitly chosen development environment file for CLI operations; Next.js loads its own `.env.local`, while the worker and migration CLI need deliberate environment loading. Do not assume a root environment file is loaded everywhere.

Create package scripts `db:generate`, `db:migrate`, and `db:seed` in `packages/db`, mapped to the selected Drizzle version and a seed script. Generate and review migrations before applying them. Seed two fictional companies with overlapping SKUs for isolation tests. Never seed real customer data by default.

After the scripts and schema exist:

```powershell
pnpm --dir packages/db db:generate
pnpm --dir packages/db db:migrate
pnpm --dir packages/db db:seed
```

These are project-defined scripts to implement, not built-in commands already available in this planning folder.

## 6. Browser-to-API proxy and authentication

Add the following server configuration to the generated Vite config while preserving its React plugin:

```typescript
server: {
  port: 5173,
  strictPort: true,
  proxy: {
    '/api': { target: 'http://localhost:3000', changeOrigin: false }
  }
}
```

Use relative `/api` calls in React. Configure the auth library's trusted public development origin as `http://localhost:5173`, mount its route handler under `/api/auth`, and verify cookies, session lookup, verification links, and reset links through that origin. In production use the actual HTTPS origin. Do not treat CORS configuration as a replacement for CSRF protection.

## 7. Start development

Create the worker `src/index.ts` and its `dev` script, then start separate terminal sessions:

```powershell
pnpm --dir apps/api dev
```

```powershell
pnpm --dir apps/web dev
```

```powershell
pnpm --dir apps/worker dev
```

S01 implements `GET /api/v1/health/live`. S03 adds readiness checks without exposing secrets. Open the UI at localhost:5173 and check the API through the same origin. Start the worker only after S07; earlier scaffolding can contain an explicit placeholder with no background processing.

## 8. Integrate the existing Astra service

During S01 inspect Astra's current gateway manifest and selected checkpoint profile. During S08 replace the product's deterministic mock with the private Astra adapter. Resolve credentials and tenant identity server-side, validate actual request/response schemas, and retain source/contract/model versions. Add a narrowly scoped authenticated wrapper only where the required library functionality lacks an existing gateway operation.

The product talks to an explicitly configured private Astra gateway, not the unauthenticated local UI API. Verify structured extraction, source validation, timeout, unavailable model, tenant mismatch and budget behavior. The reference does not establish a capable quotation checkpoint or production deployment; those remain S08/S17/S18 gates. Do not recreate the stopped Astra Compose sprint as an assumed prerequisite. External paid-provider fallback is disabled in this plan.

## 9. Developer completion check

A clean checkout must install from the lockfile, start development infrastructure, apply migrations, seed fictional data, and run the UI/API. Check lint, type checking, meaningful unit/integration tests, and production builds through scripts created in S01. S07 adds queue recovery; S08 adds model evaluation.

Production deployment follows [operations](08-deployment-and-operations.md). Running these local commands is not a production installation.

## Troubleshooting

| Symptom | Check |
|---|---|
| Docker unavailable | Desktop service, virtualization/WSL prerequisites, and current installation guidance |
| Database connection refused | Container health, localhost port, DB name and URL; never print full credentials into shared logs |
| Session missing | Public origin, cookie attributes, proxy headers, trusted origins, and auth route mounting |
| Worker cannot reach model | Host versus container networking and the configured private URL |
| Slow AI jobs | Model size, available memory, input length, concurrency, and queue backlog |
| Schema drift | Migration history and reviewed changes; do not reset a shared DB to hide drift |

