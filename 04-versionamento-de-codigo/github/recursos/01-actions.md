# GitHub Actions

## O que é

O GitHub Actions é uma ferramenta integrada ao GitHub que automatiza tarefas de um repositório. Ela pode, por exemplo, executar testes e verificar o código quando alguém envia alterações ou abre um Pull Request.

As automações são definidas em arquivos YAML dentro da pasta `.github/workflows/`.

## Conceitos principais

- **Workflow:** conjunto de etapas automatizadas, descrito em um arquivo YAML.
- **Job:** grupo de etapas que executa uma parte do workflow. Um workflow pode ter vários jobs.
- **Step:** etapa individual de um job, como instalar dependências ou rodar testes.
- **Action:** componente reutilizável que realiza uma tarefa, como baixar o código do repositório.
- **Runner:** máquina que executa o job. Pode ser uma máquina hospedada pelo GitHub, como `ubuntu-latest`.

## Quando um workflow é executado

A seção `on` define os eventos que iniciam o workflow. Dois exemplos comuns são:

- `push`: quando alterações são enviadas para uma branch;
- `pull_request`: quando um Pull Request é aberto ou atualizado.

## Exemplo: verificar um projeto Node.js

Salve um arquivo como `.github/workflows/ci.yml`:

```yaml
name: Verificações

on:
  push:
    branches: [main] # Executa quando há push na branch main
  pull_request:
    branches: [main] # Executa em PRs que têm a main como destino

jobs:
  testes:
    runs-on: ubuntu-latest # Runner usado para executar o job

    steps:
      - name: Baixar o código
        uses: actions/checkout@v4 # Action que disponibiliza o repositório no runner

      - name: Configurar Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Instalar dependências
        run: npm ci

      - name: Verificar o estilo do código
        run: npm run lint

      - name: Executar testes
        run: npm test
