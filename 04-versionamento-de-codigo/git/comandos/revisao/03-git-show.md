# 03. `👀 git-show — Inspeção Detalhada de Commits`

## 📖 Visão Geral
O comando `git show` expande os detalhes completos de um objeto no Git (um [commit](../fluxo-basico/05-git-commit.md) específico ou uma *tag*). Ao contrário do `git log` (que lista vários commits), o `git show` foca-se em exibir os metadados e o *diff* de alterações contidas em um único ponto da história.

## 📋 Sintaxe Oficial
```bash
git show [<opcoes>] [<objeto>]
```

## 🚩 Tabela de Flags Úteis

| Flag / Parâmetro | Descrição | Na Prática |
| :--- | :--- | :--- |
| `HEAD` | Aponta para o último [commit](../fluxo-basico/05-git-commit.md) realizado na [branch](../ramificacao/README.md) atual. | Para conferir imediatamente o que foi guardado no último commit. |
| `<hash-do-commit>` | Especifica o código identificador do commit que deseja inspecionar. | Usado com o hash copiado do [git log](./01-git-log.md). |
| `--stat` | Mostra o resumo de ficheiros alterados e quantidade de linhas sem o diff completo. | Para ter uma visão geral do tamanho de um commit. |
| `--name-only` | Exibe apenas a lista com os nomes dos ficheiros que foram modificados. | Para saber quais ficheiros um commit alterou sem ver o código. |

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Exibe os detalhes e o código alterado no último commit realizado (HEAD)
git show

# Exibe as alterações de um commit específico informando o seu hash
git show 8a2f1b4

# Exibe apenas a lista de ficheiros alterados num commit
git show --name-only 8a2f1b4
```

## 💡 Boas Práticas

* ✅ **O que fazer:** Combine o `git log --oneline` para encontrar o hash do commit e o `git show <hash>` para realizar auditorias pontuais de código.
* ❌ **O que evitar:** Evite tentar adivinhar o conteúdo de um commit sem usar o `git show` para inspecionar os ficheiros modificados.
---