# MOV FLOW

Repositorio pai do projeto MOV FLOW, organizado com submodulos Git:

- `frontend-mov-flow` (Vue 3 + Vuetify)
- `api-mov-flow` (NestJS + TypeORM + PostgreSQL)

## Estrutura

```text
repo-mov-flow/
|-- frontend-mov-flow/   # submodulo Git
|-- api-mov-flow/        # submodulo Git
|-- docker-compose.prod.yml
`-- .gitmodules
```

## Pre-requisitos

- Git 2.40+
- Node.js 22+
- npm 10+
- Docker + Docker Compose

## Clone com submodulos

```bash
git clone --recurse-submodules git@github.com:PatrickSimoes/repo-mov-flow.git
cd repo-mov-flow
```

Se voce ja clonou sem submodulos:

```bash
git submodule update --init --recursive
```

## Desenvolvimento local

1. API:

```bash
cd api-mov-flow
cp example.env .env
docker compose up -d
npm install
npm run migration:run
npm run start:dev
```

2. Frontend:

```bash
cd ../frontend-mov-flow
npm install
npm run dev
```

## Publicacao (Docker Compose)

Este repositorio ja inclui um `docker-compose.prod.yml` para subir stack completa:

- PostgreSQL
- API (com migration automatica na inicializacao)
- Frontend (Nginx + proxy para API)

### 1) Preparar variaveis

```bash
cp .env.production.example .env.production
cp api-mov-flow/.env.production.example api-mov-flow/.env.production
```

Ajuste os valores de senha, JWT e dominio permitido em `CORS_ORIGINS`.
Os `DB_USER`, `DB_PASS` e `DB_NAME` do arquivo raiz devem ser iguais aos usados pela API.

### 2) Subir stack

```bash
docker compose --env-file .env.production -f docker-compose.prod.yml up -d --build
```

### 3) Validar

- Frontend: `http://localhost:${FRONTEND_PORT}` (default `8080`)
- API Health: `http://localhost:${FRONTEND_PORT}/api/v1/health`

## Fluxo com submodulos

Alteracoes de codigo devem ser feitas dentro de cada submodulo e depois refletidas no repo pai:

```bash
git add frontend-mov-flow api-mov-flow
git commit -m "chore(submodule): update pointers"
git push
```
