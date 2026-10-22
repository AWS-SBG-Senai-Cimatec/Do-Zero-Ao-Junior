# 🧪 Laboratório Prático: Guia 06 - Pausando e Resgatando Trabalho com Git Stash

> 📌 **Cenário:** Troca urgente de contexto: você está no meio de uma implementação que ainda não funciona e precisa corrigir um bug urgente em outra ramificação sem perder seu progresso.
>
> 🔹 **Guardar trabalho incompleto:** `git stash push -m "descrição"`  
> 🔹 **Resgatar o trabalho:** `git stash pop`

---

## 🎯 Pré-requisitos

* Git instalado no seu computador.
* Conhecimentos básicos de `git checkout`, `git switch`, `git branch` e `git commit`.

---

## 🚀 Roteiro Hands-on: Passo a Passo

### 📦 Passo 1: Preparando o Repositório de Teste

Abra o terminal e execute o bloco abaixo para criar o repositório de teste e um commit inicial na branch `main`:

```bash
# 1. Cria a pasta do laboratório e entra nela
mkdir lab-git-stash && cd lab-git-stash

# 2. Inicializa o repositório Git na branch main
git init -b main

# 3. Cria um arquivo base do projeto e realiza o commit inicial
echo "console.log('Sistema Online');" > app.js
git add app.js
git commit -m "docs: commit inicial do projeto"
```

> 🔍 **Verificação:** Execute `git log --oneline`. Você deve ver o commit inicial na branch `main`.

---

### 🚧 Passo 2: Simulando o Trabalho Incompleto que Não Funciona

Agora crie uma nova ramificação (*branch*) e comece uma alteração que ficará incompleta:

```bash
# 1. Cria e muda para a branch da nova funcionalidade
git checkout -b feature/autenticacao

# 2. Modifica o arquivo app.js simulando uma implementação incompleta
echo "console.log('Nova funcionalidade de login em andamento...');" >> app.js
```

> 🔍 **Verificação:** Execute `git status`. Observe que o arquivo `app.js` está modificado (*modified*), mas o código ainda não funciona e não deve ser commitado.

---

### 🚨 Passo 3: Guardando o Trabalho Incompleto (`git stash push`)

Surgiu um bug urgente em outra ramificação! Para não perder o progresso nem fazer um commit de código quebrado, guarde o trabalho no stash:

```bash
# Guardando as alterações no stash com uma descrição clara
git stash push -m "wip: implementacao do login incompleta"
```

> 🔍 **Verificação:** Execute `git status`. O diretório estará limpo (`working tree clean`), permitindo trocar de branch com segurança.

---

### 🛠️ Passo 4: Corrigindo o Bug em Outra Ramificação

Com a mesa limpa, mude de contexto para resolver a emergência:

```bash
# 1. Volta para a branch main
git switch main

# 2. Cria a branch para a correção urgente do bug
git checkout -b fix/bug-urgente

# 3. Realiza a correção no arquivo
echo "console.log('Bug critico corrigido!');" >> app.js
git add app.js
git commit -m "fix: resolve erro critico de execucao"

# 4. Integra a correção na main
git switch main
git merge fix/bug-urgente
```

> 🔍 **Verificação:** Execute `git log --oneline` na `main` para ver a correção aplicada.

---

### 🎁 Passo 5: Voltando e Resgatando o Trabalho (`git stash pop`)

Após resolver a emergência, volte para a sua ramificação original e resgate o trabalho que estava guardado:

```bash
# 1. Retorna para a branch da sua funcionalidade
git switch feature/autenticacao

# 2. Resgata as alterações salvas e remove do stash
git stash pop
```

> 🔍 **Verificação:** Execute `git status`. O arquivo `app.js` voltou ao estado modificado exatamente como você o deixou antes da emergência!

---

## 🛠️ Comandos de Apoio e Gerenciamento

| Comando | Descrição / Objetivo |
| :--- | :--- |
| `git stash list` | Lista todos os rascunhos salvos no stash. |
| `git stash pop` | Restaura o trabalho mais recente e o remove da lista. |
| `git stash apply` | Restaura o trabalho mas o mantém salvo no stash. |
| `git stash clear` | Limpa todos os rascunhos armazenados. |
