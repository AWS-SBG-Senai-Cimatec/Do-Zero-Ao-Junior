# 03. 🔍 git-status — Inspeção do Estado do Repositório

## 📖 Visão Geral

O `git status` é a ferramenta de diagnóstico do Git. Ele exibe o estado atual dos arquivos no seu diretório de trabalho (*working directory*) e na área de preparação ([staging area](./04-git-add.md)), mostrando quais arquivos foram modificados, criados ou excluídos.

---

## 📋 Sintaxe Oficial

```bash
git status [flags]
```

---

## 🚩 Tabela de Flags Úteis

| Flag | Descrição | Na Prática |
| :--- | :--- | :--- |
| `-s` / `--short` | Exibe a saída de forma resumida e compacta. | Ótimo para verificar rapidamente múltiplos arquivos alterados. |
| `-b` / `--branch` | Mostra a [branch](../ramificacao/README.md) atual e o status do rastreamento remoto junto da versão curta. | Usado junto com `-s` (`git status -sb`). |
| `-u no` | Oculta arquivos não rastreados (*untracked files*) da listagem. | Limpa a saída quando há muitos arquivos temporários na pasta. |

---

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Exibe o status completo com instruções detalhadas do Git
git status

# Exibe o status resumido com indicação da branch atual
git status -sb
```

### 🖥️ Saída Esperada no Terminal

```console
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        script.js
```

> 💡 **O que significa essa saída?**  
> O Git indica que o arquivo `index.html` está pronto para o commit ([staging area](./04-git-add.md)) e que o arquivo `script.js` é novo e ainda não está sendo rastreado (*untracked*).

---

## 💡 Boas Práticas

- ✅ **Verificação Prévia:** Execute `git status` antes de preparar ([git add](./04-git-add.md)) e salvar ([git commit](./05-git-commit.md)) alterações.
- ❌ **Evite Commits Cegos:** Não faça commits sem verificar o status para não salvar configurações locais ou arquivos indesejados.
---