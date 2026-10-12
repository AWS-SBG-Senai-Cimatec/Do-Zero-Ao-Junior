# 05. `📸 git-commit — Registo de Snapshots no Histórico`

## 📖 Visão Geral
O `git commit` grava permanentemente o conjunto de alterações que estavam na área de preparação ([staging area](./04-git-add.md)) no histórico do repositório. Cada commit gera um identificador único (código *hash*) e funciona como um ponto de restauração no projeto.

## 📋 Sintaxe Oficial
```bash
git commit [<opções>] [--] [<caminho>...]
```

## 🚩 Tabela de Flags Úteis

| Flag | Descrição | Na Prática |
| :--- | :--- | :--- |
| `-m "<mensagem>"` | Define a mensagem descritiva do commit via terminal. | Obrigatório para descrever o que foi alterado. |
| `-a` / `--all` | Prepara ficheiros modificados rastreados e faz o commit num só passo. | Atalho para pular a etapa do `git add` em ficheiros já existentes. |
| `--amend` | Substitui o último commit realizado. | Para corrigir erros de digitação na mensagem ou incluir um ficheiro esquecido. |
| `--no-edit` | Usado com `--amend` para adicionar alterações ao commit anterior mantendo a mesma mensagem. | Para incluir pequenos ajustes sem alterar a descrição. |

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Grava um commit com mensagem clara
git commit -m "docs: adiciona guia do git-commit"

# Atalho para preparar ficheiros modificados e fazer o commit de uma vez
git commit -am "fix: corrige pequeno erro de digitacao"

# Adiciona um ficheiro esquecido ao último commit sem alterar a mensagem
git add ficheiro-esquecido.md
git commit --amend --no-edit
```

## 💡 Boas Práticas

* ✅ **O que fazer:** Siga convenções de mensagens como *Conventional Commits* (`docs:`, `feat:`, `fix:`, `refactor:`).
* ❌ **O que evitar:** Evite mensagens genéricas como `"ajustes"` ou `"update"`. Não use `--amend` em commits que já foram enviados (*push*) para o servidor remoto.
___