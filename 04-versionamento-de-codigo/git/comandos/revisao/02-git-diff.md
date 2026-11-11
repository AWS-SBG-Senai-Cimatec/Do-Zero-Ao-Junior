# ⚖️ 02. `git-diff — Comparação de Código e Alterações`

## 📖 Visão Geral
O `git diff` é a ferramenta de comparação visual do Git. Ele exibe exatamente quais linhas foram adicionadas (`+`) ou removidas (`-`) entre o seu diretório de trabalho, a área de preparação ([staging area](../fluxo-basico/04-git-add.md)) ou entre diferentes [branches](../ramificacao/README.md).

## 📋 Sintaxe Oficial
```bash
git diff [<opcoes>] [<commit>] [<ficheiro>]
```

## 🚩 Tabela de Flags Úteis

| Flag / Parâmetro | Descrição | Na Prática |
| :--- | :--- | :--- |
| `--staged` / `--cached` | Compara as alterações na [staging area](../fluxo-basico/04-git-add.md) com o último [commit](../fluxo-basico/05-git-commit.md). | Para revisar o que vai ser guardado antes de executar o commit. |
| `--stat` | Exibe apenas um resumo estatístico com ficheiros alterados e número de linhas. | Útil para checar o volume de mudanças sem ver o código completo. |
| `<branch1> <branch2>` | Compara o código completo entre duas [branches](../ramificacao/README.md). | Para inspecionar as diferenças antes de fazer um *merge*. |
| `-- <caminho>` | Limita a comparação a um ficheiro ou pasta específica. | Quando quer ver a diferença de apenas um ficheiro. |

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Compara alterações não preparadas do working directory com o último commit
git diff

# Compara o que já está na staging area (git add) com o último commit
git diff --staged

# Exibe apenas o resumo de linhas alteradas por ficheiro
git diff --stat

# Compara as diferenças entre a branch 'main' e a branch 'dev'
git diff main dev
```

## 💡 Boas Práticas

* ✅ **O que fazer:** Execute `git diff --staged` antes de dar commit para garantir que não deixou nenhum código temporário ou de teste para trás.
* ❌ **O que evitar:** Não envie alterações sem conferir o `diff`, prevenindo a inclusão acidental de linhas em branco ou comentários desnecessários.
---