# Guia 05: Mantendo o Histórico Limpo com Git Rebase

Este guia ensina como utilizar o **`git rebase`** e o **`git rebase interativo`** para organizar o seu histórico de commits, garantindo um repositório limpo, linear e sem commits desnecessários de mesclagem.

---

## 💡 Entendendo o Contexto: Por que usar Rebase?

Imagine que você está escrevendo um capítulo de um livro em parceria com outra pessoa:
* **Merge tradicional:** Você pega as páginas do seu parceiro e cola no meio do seu rascunho com uma nota adesiva dizendo *"Ajuste feito em 10/10"*. O livro fica legível, mas cheio de marcas de costura (os chamados *merge commits*).
* **Rebase:** Você destaca o seu capítulo temporariamente, atualiza as páginas base com o trabalho mais recente do seu parceiro e depois reescreve o seu capítulo no topo dessa nova base. O resultado é um texto contínuo e perfeitamente linear.

---

## 🛠️ Preparando o Ambiente Prático (Laboratório)

Para praticar todos os conceitos deste guia na prática, crie um ambiente de testes local usando a **Opção B** (geração automática do repositório de treinos via terminal).

### Execução em um único comando
Abra seu terminal e cole o bloco abaixo (cole com ctrl+shift+v):

```bash
mkdir lab-git-rebase && cd lab-git-rebase && git init -b main && \
echo "# Lab Rebase" > README.md && git add . && git commit -m "docs: commit inicial" && \
git checkout -b feature/autenticacao && \
echo "function login(){}" > auth.js && git add . && git commit -m "wip: login" && \
echo "// fix" >> auth.js && git add . && git commit -m "wip: ajustes" && \
echo "function logout(){}" >> auth.js && git add . && git commit -m "feat: auth completa" && \
git checkout main && \
echo "const CONFIG = {};" > config.js && git add . && git commit -m "chore: add config" && \
git checkout feature/autenticacao
```
# Guia 05: Mantendo o Histórico Limpo com Git Rebase

## O que este comando acabou de fazer?

- Criou o repositório com a branch `main` e um commit inicial (`docs: commit inicial`).
- Criou a branch de funcionalidade `feature/autenticacao`.
- Adicionou 3 commits de rascunho/WIP na branch da feature (`wip: login`, `wip: ajustes`, `feat: auth completa`).
- Simulou uma atualização paralela na `main` (`chore: add config`).
- Deixou você posicionado na branch `feature/autenticacao`.

---

## 🔍 Step 2: Inspecionando a Divergência no Histórico

Antes de executar qualquer ação, execute o comando abaixo no terminal para visualizar o gráfico das ramificações:

**Bash**

```bash
git log --oneline --graph --all
```

**Saída esperada no terminal:**

```text
* 4a82f1b (main) chore: add config
| * 7b31c9a (HEAD -> feature/autenticacao) feat: auth completa
| * 2e15d8f wip: ajustes
| * 9f04e1d wip: login
|/
* 1a812f4 docs: commit inicial
```

<img width="705" height="187" alt="image" src="https://github.com/user-attachments/assets/426f9dfe-e99a-47e3-8a2e-08bd71538345" />


Observe que a `main` e a `feature/autenticacao` se separaram a partir do commit inicial.

---

## 🚀 Step 3: Atualizando a Branch com `git rebase main`

### O Problema

Sua branch `feature/autenticacao` está desatualizada em relação ao commit `chore: add config` da `main`.

### A Execução

Ainda na branch `feature/autenticacao`, execute:

**Bash**

```bash
git rebase main
```

**Saída esperada no terminal:**

```text
Successfully rebased and updated refs/heads/feature/autenticacao.
```

### O que aconteceu por trás dos panos?

1. O Git guardou seus 3 commits em uma área temporária.
2. Trouxe o commit `chore: add config` da `main` para a sua branch.
3. Reaplicou os seus 3 commits um a um por cima do histórico atualizado.

Confirme a nova estrutura linear rodando:

**Bash**

```bash
git log --oneline --graph
```

**Saída esperada:**

```text
* 8c52d3a (HEAD -> feature/autenticacao) feat: auth completa
* 5b41e2f wip: ajustes
* 3a04c1d wip: login
* 4a82f1b (main) chore: add config
* 1a812f4 docs: commit inicial
```

<img width="658" height="164" alt="image" src="https://github.com/user-attachments/assets/3e86f9ad-e0a4-4467-aad6-5a1db846b1bd" />

---

## 🧹 Step 4: Limpando os Commits com Rebase Interativo (`-i`)

### O Problema

Você possui commits fragmentados (`wip: login`, `wip: ajustes`) que não agregam valor ao histórico principal do projeto.

### A Execução

Abra a interface do rebase interativo para os últimos 3 commits:

**Bash**

```bash
git rebase -i HEAD~3
```

O Git abrirá o seu editor de texto padrão com o seguinte conteúdo:

**Plaintext**

```text
pick 3a04c1d wip: login
pick 5b41e2f wip: ajustes
pick 8c52d3a feat: auth completa

# Commandes:
# p, pick <commit> = usar commit
# s, squash <commit> = usar commit, mas fundir com o commit anterior
```

### Modificação no Editor

Substitua a palavra `pick` por `squash` (ou apenas `s`) nos commits que você deseja fundir no primeiro:

**Plaintext**

```text
pick 3a04c1d wip: login
squash 5b41e2f wip: ajustes
squash 8c52d3a feat: auth completa
```

Salve e feche o editor.

Em seguida, uma nova tela se abrirá para definir a mensagem final unificada. Substitua o texto antigo por uma mensagem limpa e semântica:

**Plaintext**

```text
feat: implementa modulo completo de autenticacao
```

---

## ✅ Step 5: Verificação do Resultado Final

Execute o comando de verificação:

**Bash**

```bash
git log --oneline --graph
```

**Resultado esperado:**

```text
* e91f2a4 (HEAD -> feature/autenticacao) feat: implementa modulo completo de autenticacao
* 4a82f1b (main) chore: add config
* 1a812f4 docs: commit inicial
```

O histórico agora está perfeitamente limpo, organizado e pronto para ser integrado à branch principal!

---

## 📑 Tabela de Referência de Comandos do Rebase Interativo

| Comando | Sigla | Função |
|---|---|---|
| `pick` | `p` | Mantém o commit no histórico. |
| `squash` | `s` | Funde o commit com o anterior, unindo as mensagens. |
| `fixup` | `f` | Funde o commit com o anterior, descartando a mensagem deste commit. |
| `reword` | `r` | Mantém o commit, mas abre o editor para alterar a mensagem. |
| `drop` | `d` | Remove o commit completamente do histórico. |

---

## ⚠️ Regra de Ouro do Rebase

**Nunca faça rebase em branches públicas ou compartilhadas!**

O rebase reescreve o histórico de hashes. Utilize-o apenas nas suas branches locais antes de abrir o Pull Request.
