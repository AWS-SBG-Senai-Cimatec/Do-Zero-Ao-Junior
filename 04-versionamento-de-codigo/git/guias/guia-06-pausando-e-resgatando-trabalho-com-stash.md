# Guia 06: Pausando e Resgatando Trabalho com Git Stash

> 💡 **Analogia da Gaveta Espacial:** Imagine que você está montando um quebra-cabeça na sua mesa de trabalho, mas precisa usá-la imediatamente para assinar um documento urgente. Em vez de desfazer o quebra-cabeça ou jogar tudo no chão, você pega uma gaveta especial, guarda todas as peças exatamente no estado em que estão, limpa a mesa, resolve o problema urgente e depois devolve as peças para a mesa no mesmo lugar. O `git stash` é essa gaveta!

---

## 📌 Entendendo o Contexto

No cotidiano do desenvolvimento, é extremamente comum estar no meio de uma tarefa quando surge uma prioridade crítica: um bug em produção que precisa de correção imediata ou um pedido urgente de colega para revisar outra branch.

Se você tentar mudar de branch (`git checkout` ou `git switch`) com alterações incompletas ou com código que nem sequer compila/funciona, o Git pode impedir a troca para não sobrescrever seu trabalho, ou carregar essas alterações indesejadas para a nova branch.

O **`git stash`** resolve isso permitindo **guardar temporariamente suas alterações não salvas** (sem a necessidade de fazer um commit "sujo" de rascunho) e deixando seu diretório de trabalho completamente limpo.

---

## 🚀 Passo a Passo Prático

### Passo 1: Guardando o Trabalho Incompleto (`git stash push`)

Quando precisar interromper o que está fazendo, guarde seu progresso atual atribuindo uma mensagem descritiva para facilitar a identificação depois.

```bash
# Guardando as alterações no stash com uma descrição clara
git stash push -m "wip: implementação da tela de perfil incompleta"
```

#### 🔍 O que acontece:
* Suas modificações nos arquivos editados somem do diretório de trabalho (*working directory*).
* O estado do seu projeto volta exatamente ao último *commit* realizado.
* Seu diretório fica limpo para você mudar de branch com segurança.

---

### Passo 2: Mudando de Contexto e Resolvendo a Urgência

Com a mesa limpa, você pode trocar de branch e realizar a correção necessária sem interferências.

```bash
# 1. Muda para a branch principal
git switch main

# 2. Cria a branch para a correção urgente
git checkout -b fix/bug-login-urgente

# 3. Faz a correção, adiciona e realiza o commit
git add .
git commit -m "fix: corrige erro critico de autenticacao no login"

# 4. Envia/integra a solução
git switch main
git merge fix/bug-login-urgente
```

---

### Passo 3: Voltando e Resgatando o Trabalho (`git stash pop`)

Após resolver a emergência, é hora de voltar para a sua branch de funcionalidade e resgatar o trabalho que estava guardado na "gaveta".

```bash
# 1. Retorna para sua branch original
git switch feature/tela-perfil

# 2. Restaura as alterações e as remove da gaveta (stash)
git stash pop
```

#### 🔍 Opções para resgatar o trabalho:
* **`git stash pop`**: Aplica as alterações salvas de volta ao seu código e **remove** o registro da lista do stash.
* **`git stash apply`**: Aplica as alterações salvas de volta, mas **mantém** uma cópia salva na lista do stash por segurança.

---

## 🛠️ Comandos Essenciais para Gerenciar a Gaveta (Stash)

| Comando | Descrição / Objetivo |
| :--- | :--- |
| **`git stash list`** | Lista todos os rascunhos guardados no stash (ex: `stash@{0}`, `stash@{1}`). |
| **`git stash pop`** | Restaura o rascunho mais recente e o remove do stash. |
| **`git stash apply stash@{N}`** | Restaura um stash específico da lista sem removê-lo. |
| **`git stash drop stash@{N}`** | Descarta/apaga um stash específico que não será mais utilizado. |
| **`git stash clear`** | Limpa **todos** os rascunhos armazenados na lista do stash. |

---

## ⚠️ Boas Práticas

1. **Sempre use `-m "descrição"`:** Salvar com `git stash push -m "sua mensagem"` evita que você fique perdido sem saber o que cada `stash@{N}` contém quando a lista crescer.
2. **Arquivos Não Rastreados (*Untracked*):** Por padrão, arquivos novos criados que ainda não foram adicionados com `git add` não são guardados pelo stash simples. Para incluí-los, use:
   ```bash
   git stash push -u -m "wip: inclui novos arquivos criados"
   ```
