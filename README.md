# 🧠 Copilot Codespaces Prompt: Scaffold `drone1` Autonomous Agent Orchestrator Monorepo Backend

You are a backend engineer using GitHub Codespaces with Copilot.

---

## Objective

**Scaffold a scalable Turborepo monorepo for the `drone1` Autonomous Agent Orchestrator backend** using pnpm, TypeScript, and Fastify. The monorepo will house modular, service-oriented packages for agent orchestration, goal decomposition, role management, execution, feedback, and observability.

---

## 🔧 Tech Stack

- **Monorepo Manager:** Turborepo
- **Package Manager:** pnpm
- **Language:** TypeScript
- **Runtime:** Node.js (LTS)
- **Web Framework:** Fastify (preferred); fallback: Express
- **Message Broker:** NATS (pluggable with Kafka)
- **Databases:**
  - PostgreSQL (objectives, goals, agents)
  - Neo4j (dependency graphs)
  - Redis (queues, ephemeral state)
  - MinIO/S3 (agent artifacts)
- **API Layer:** REST (OpenAPI docs), extensible to GraphQL
- **Auth:** OAuth2.0 + JWT (scoped RBAC)
- **Testing:** Vitest or Jest
- **Dev Tools:** ESLint, Prettier, Husky, Commitlint
- **Observability:** Prometheus, Grafana, Loki

---

## 📦 Folder Structure

Set up the following Turborepo workspace structure:

```
drone1/
├── apps/
│   └── api-gateway/           # Entry point for all requests
├── packages/
│   ├── common/                # Shared types, utils, interfaces
│   ├── goal-engine/           # Objective intake, parsing, goal decomposition
│   ├── activation-compiler/   # Activation package builder
│   ├── swarm-orchestrator/    # Agent deployment, status
│   ├── execution-runtime/     # Task execution, agent coordination
│   ├── resource-allocator/    # Resource scheduling
│   ├── role-registry/         # Role definitions, policies
│   ├── performance-monitor/   # Metrics and anomaly detection
│   ├── feedback-loop/         # Learning loop, curriculum updates
│   └── dependency-graph/      # Neo4j dependency management
├── .github/
│   └── workflows/
│       └── ci.yml             # CI pipeline
├── package.json
├── pnpm-workspace.yaml
├── turbo.json
└── tsconfig.json
```

---

## 🧱 Bootstrap Tasks

1. **Initialize Monorepo**
   - Use `pnpm init`
   - Create `pnpm-workspace.yaml` with `apps/*` and `packages/*`

2. **Add Turborepo**
   - Install `turbo` as a dev dependency
   - Create `turbo.json` with pipelines for `build`, `dev`, `lint`, `test`

3. **TypeScript Config**
   - Root `tsconfig.json`, extended by each app/package

4. **Scaffold Each Workspace**
   - Each: `src/`, `tests/`, `index.ts`
   - Fastify server with sample route
   - Typed schemas, example handlers
   - Dockerfile for each service
   - Local `dev` script

5. **Shared Package**
   - `common`: Types (`Agent`, `Goal`, etc), interfaces, NATS client, env loaders

6. **CI Setup**
   - `.github/workflows/ci.yml`: Install, lint, build, test all workspaces

7. **Docker + K8s**
   - Dockerfile per service (multi-stage)
   - `docker-compose.yaml` for local dev
   - Optional: Helm charts for K8s

---

## ✅ Example Service Endpoints

- `goal-engine`:
  - `POST /objectives`
  - `POST /parseGoal`
  - `POST /decomposeGoal`
- `activation-compiler`:
  - `POST /createActivationPackage`
- `swarm-orchestrator`:
  - `POST /deployAgent`
  - `GET /swarmStatus`
- ...and so on for each package

---

## 📈 Observability

- Integrate Prometheus client in all services (Fastify plugin)
- Log via Pino (stdout; ready for Loki/Grafana)

---

## 🚀 Final Goals

- Dev mode: `pnpm dev --filter goal-engine`
- Deploy all services locally with Docker Compose
- Support end-to-end agent orchestration and feedback lifecycle

---

**Start by scaffolding the Turborepo monorepo and creating the `goal-engine` and `api-gateway` services. Use this prompt as your implementation guide.**
