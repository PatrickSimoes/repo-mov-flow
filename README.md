# MOV FLOW

Repositorio pai do projeto MOV FLOW, organizado com submodulos Git.

## Objetivo

Orquestrar uma aplicacao full stack para operacao logistica e financeira multi-tenant:

- `frontend-mov-flow`: interface web (Vue 3 + Vuetify)
- `api-mov-flow`: API backend (NestJS + TypeORM + PostgreSQL)

## Estrutura

```text
repo-mov-flow/
|-- frontend-mov-flow/   # submodulo Git
|-- api-mov-flow/        # submodulo Git
`-- .gitmodules
```

## Repositorios vinculados

- Frontend: `git@github.com:PatrickSimoes/frontend-mov-flow.git`
- API: `git@github.com:PatrickSimoes/api-mov-flow.git`

## Pre-requisitos

- Git 2.40+
- Node.js 22+
- npm 10+
- Docker + Docker Compose (para banco local da API)

## Como clonar

```bash
git clone --recurse-submodules git@github.com:PatrickSimoes/repo-mov-flow.git
cd repo-mov-flow
```

Se voce ja clonou sem submodulos:

```bash
git submodule update --init --recursive
```

## Como subir localmente

1. API

```bash
cd api-mov-flow
cp example.env .env
docker compose up -d
npm install
npm run migration:run
npm run start:dev
```

2. Frontend

```bash
cd ../frontend-mov-flow
npm install
npm run dev
```

## Fluxo de trabalho com submodulos

- Alteracoes de codigo devem ser feitas dentro de `frontend-mov-flow` ou `api-mov-flow`.
- O repositorio pai versiona:
  - `.gitmodules`
  - ponteiros (commits) dos submodulos

Para atualizar ponteiros no repo pai:

```bash
git add .gitmodules frontend-mov-flow api-mov-flow
git commit -m "Update submodule pointers"
git push
```

## Observacoes

- Este repositorio nao concentra logica de negocio.
- Documentacao tecnica detalhada fica dentro de cada submodulo.
