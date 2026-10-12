# 04. `➕ git-add — Preparação de Alterações (Staging Area)`

## 📖 Visão Geral
O `git add` move as alterações feitas nos seus ficheiros do diretório de trabalho para a área de preparação (staging area). É aqui que é selecionado exatamente o que deseja incluir no próximo [commit](./05-git-commit.md).

## 📋 Sintaxe Oficial
```bash
git add <caminho-do-arquivo> | . | -p
```

## 🚩 Tabela de Flags Úteis

| Flag / Parâmetro | Descrição | Na Prática |
| :--- | :--- | :--- |
| `<ficheiro>` | Prepara um ficheiro específico. | Quando alterou vários ficheiros, mas quer guardar apenas um. |
| `. (ponto)` | Prepara todas as alterações do diretório atual e subpastas. | Para adicionar rapidamente todo o trabalho feito. |
| `-p` / `--patch` | Abre um modo interativo para escolher trechos específicos do ficheiro (*hunks*). | Para revisar linha por linha antes de colocar na staging area. |
| `-u` / `--update` | Prepara apenas ficheiros modificados e eliminados, ignorando ficheiros novos. | Útil ao refatorar código existente sem incluir rascunhos novos. |

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Prepara apenas o ficheiro 'README.md'
git add README.md

# Prepara todas as modificações da pasta atual
git add .

# Seleciona interativamente os blocos de código que deseja adicionar
git add -p
```

## 💡 Boas Práticas

* ✅ **O que fazer:** Utilize `git add -p` sempre que quiser selecionar alterações e criar commits pequenos e focados.
* ❌ **O que evitar:** Evite usar `git add .` sem conferir o [git status](./03-git-status.md) antes, prevenindo o envio de chaves de API, palavras-passe ou pastas locais de sistema.
---
