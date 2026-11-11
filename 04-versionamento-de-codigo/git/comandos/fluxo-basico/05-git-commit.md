# 05. 📸 git-commit — Registro de Snapshots no Histórico

## 📖 Visão Geral

O `git commit` grava permanentemente o conjunto de alterações que estavam na área de preparação ([staging area](./04-git-add.md)) no histórico do repositório. Cada commit gera um identificador único (código *hash*) e funciona como um ponto de restauração no projeto.

---

## 📋 Sintaxe Oficial

```bash
git commit [flags] [-m "<mensagem>"] [<caminho>]
```

---

## 🚩 Tabela de Flags Úteis

| Flag | Descrição | Na Prática |
| :--- | :--- | :--- |
| `-m "<mensagem>"` | Define a mensagem descritiva do commit via terminal. | Obrigatório para descrever o que foi alterado. |
| `-a` / `--all` | Prepara arquivos modificados rastreados e faz o commit em um só passo. | Atalho para pular a etapa do `git add` em arquivos já existentes. |
| `--amend` | Substitui o último commit realizado. | Para corrigir erros de digitação na mensagem ou incluir um arquivo esquecido. |
| `--no-edit` | Usado com `--amend` para adicionar alterações ao commit anterior mantendo a mesma mensagem. | Para incluir pequenos ajustes sem alterar a descrição. |

---

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Grava um commit com mensagem clara
git commit -m "docs: adiciona guia do git-commit"

# Atalho para preparar arquivos modificados e fazer o commit de uma vez
git commit -am "fix: corrige pequeno erro de digitacao"

# Adiciona um arquivo esquecido ao último commit sem alterar a mensagem
git add arquivo-esquecido.md
git commit --amend --no-edit
```

### 🖥️ Saída Esperada no Terminal

```console
[main 3b7e5d1] docs: adiciona guia do git-commit
 1 file changed, 45 insertions(+)
 create mode 100644 guia.md
```

> 💡 **O que significa essa saída?**  
> O Git confirma a criação do commit na branch `main` exibindo o hash reduzido (`3b7e5d1`), a mensagem inserida e o resumo das alterações de arquivos e linhas afetadas.

---

## 💡 Boas Práticas

- ✅ **Mensagens Padronizadas:** Siga convenções de mensagens como *Conventional Commits* (`docs:`, `feat:`, `fix:`, `refactor:`).
- ❌ **Evite Mensagens Genéricas:** Evite mensagens vagas como `"ajustes"` ou `"update"`. Não use `--amend` em commits que já foram enviados (*push*) para o repositório remoto.
---