# 03. `🔍 git-status — Inspeção do Estado do Repositório`

## 📖 Visão Geral
O `git status` é a ferramenta de diagnóstico do Git. Ele exibe o estado atual dos ficheiros no seu diretório de trabalho (*working directory*) e na área de preparação ([staging area](./04-git-add.md)), mostrando quais ficheiros foram modificados, criados ou eliminados.

## 📋 Sintaxe Oficial
```bash
git status [-s | --short] [-b | --branch]
```

## 🚩 Tabela de Flags Úteis

| Flag | Descrição | Na Prática |
| :--- | :--- | :--- |
| `-s` / `--short` | Exibe a saída de forma resumida e compacta. | Ótimo para verificar rapidamente múltiplos ficheiros alterados. |
| `-b` / `--branch` | Mostra a [branch](../ramificacao/README.md) atual e o status do rastreamento remoto junto da versão curta. | Usado junto com `-s` (`git status -sb`). |
| `-u no` | Oculta ficheiros não rastreados (*untracked files*) da listagem. | Limpa a saída quando há muitos ficheiros temporários na pasta. |

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Exibe o status completo com instruções detalhadas do Git
git status

# Exibe o status resumido com indicação da branch atual
git status -sb
```

## 💡 Boas Práticas

* ✅ **O que fazer:** Execute `git status` antes de preparar ([git add](./04-git-add.md)) e guardar ([git commit](./05-git-commit.md)) alterações.
* ❌ **O que evitar:** Não faça commits sem verificar o status para não guardar configurações locais ou algo indesejado.
---