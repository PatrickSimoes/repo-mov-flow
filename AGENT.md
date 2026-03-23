# AGENT - MOV FLOW

Este repositório é o **repositório pai** do projeto MOV FLOW.

## Objetivo

Organizar um app full stack usando dois repositórios Git separados como submódulos:

- `frontend-mov-flow` (front-end)
- `api-mov-flow` (back-end / API)

## Estrutura

```text
repo-mov-flow/
├── frontend-mov-flow/   # submódulo Git
├── api-mov-flow/        # submódulo Git
└── .gitmodules
```

## Repositórios vinculados

- Frontend: `git@github.com:PatrickSimoes/frontend-mov-flow.git`
- API: `git@github.com:PatrickSimoes/api-mov-flow.git`

## Regras de trabalho

1. Este repositório não concentra código de negócio principal; ele orquestra os módulos.
2. Alterações de código devem ser feitas dentro de cada submódulo.
3. O repositório pai versiona apenas:
   - arquivo `.gitmodules`
   - ponteiros (commits) dos submódulos

## Comandos principais

Clonar com submódulos:

```bash
git clone --recurse-submodules git@github.com:PatrickSimoes/repo-mov-flow.git
```

Inicializar submódulos (após clone já existente):

```bash
git submodule update --init --recursive
```

Atualizar submódulos para os últimos commits das branches rastreadas:

```bash
git submodule update --remote --recursive
```

Salvar no repo pai novos ponteiros de submódulo:

```bash
git add .gitmodules frontend-mov-flow api-mov-flow
git commit -m "Update submodule pointers"
git push
```

## Resumo

`repo-mov-flow` é um mono-repo de orquestração com dois repositórios Git independentes (frontend e API), formando o app full stack MOV FLOW.
