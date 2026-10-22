# 🚀 Capítulo 03: Desvendando o Pull Request (PR)

Seja muito bem-vindo(a) ao coração do trabalho colaborativo no Git e GitHub! 

Se você já trabalhou em equipe — seja num projeto da faculdade, na montagem de um móvel ou no planejamento de uma festa —, sabe que em algum momento todo mundo precisa juntar as peças para ver o resultado final. No mundo do código, a ferramenta mágica que faz isso com segurança e organização pelo github chama-se **Pull Request**.

Neste capítulo, vamos entender o que é essa solicitação, como ela funciona na prática e um truque super útil para automatizar a organização do seu projeto. Vamos lá?

---

## 💡 1. Afinal, o que é um Pull Request?

Imagine que o projeto principal da sua equipe é um **Sistema de Login** publicado (a branch principal, como a `main`). 

Você teve uma ideia incrível: adicionar uma nova função de recuperação de conta. Em vez de pegar a caneta e escrever direto no código oficial — o que seria arriscado se você errasse algum comando e quebrasse o código —, você:

1. Tira uma cópia do código (cria uma **branch de funcionalidade**, ex: `feature/recuperação-de-conta`).
2. Escreve e testa sua receita nessa cópia (faz os seus **commits**).
3. Levanta a mão e diz para os donos do código: *"Ei, pessoal! Escrevi essa funcionalidade. Vocês podem revisar para ver se está tudo certo e colocar no código oficial?"*

Essa **"levantada de mão"** é o **Pull Request**! 

> 📌 **Em resumo:** Um **Pull Request (PR)** é uma solicitação formal que você faz aos mantenedores de um repositório para **mesclar (merge)** as alterações da sua ramificação (*branch*) para a ramificação principal.

---

## 🛠️ 2. Como Funciona o Fluxo de um PR?

Quando você abre um PR na plataforma (como o GitHub, GitLab ou Bitbucket), uma tela de "supervisão" é criada. Essa tela ajuda todo mundo a entender o que mudou.

Vamos entender os três pilares dessa tela:

### A. O Confronto: Base vs. Compare
Para o Git saber o que juntar, você precisa definir duas coisas:
* **Base Branch (Onde vai entrar):** A branch de destino oficial (geralmente `main`).
* **Compare Branch (De onde vem):** A sua branch com as novidades (ex: `feature/login-page`).

```text
[ Compare: feature/login-page ]  --->  ENVIAR PARA  --->  [ Base: main ]
```

### B. Histórico de Commits
O PR lista todas as "estações" da sua viagem. Cada **commit** que você fez enquanto trabalhava naquela branch aparece em uma linha do tempo organizada. Se você fez 3 atualizações na sua funcionalidade, todas as 3 estarão visíveis lá.

### C. Visualizador de Diffs (Diferenças)
Esta é a parte favorita dos revisores de código! O visualizador de **diff** mostra exatamente o que foi alterado linha por linha:
* 🟢 **Linhas verdes (+):** Código novo adicionado.
* 🔴 **Linhas vermelhas (-):** Código antigo removido ou modificado.

---

## 🧠 Hora de Praticar! (Quiz Rápido)

Antes de passarmos para o próximo tópico, teste seu conhecimento:

**Cenário:** Você criou a branch `fix/corrigir-header` a partir da `main`. Fez as correções necessárias e agora quer mandar de volta para a `main`.

1. Qual deve ser a sua **Base branch** no PR?
2. Qual deve ser a sua **Compare branch** no PR?

<details>
<summary>👉 Clique aqui para ver a resposta!</summary>

1. **Base branch:** `main` (é o destino final de onde o projeto vive).
2. **Compare branch:** `fix/corrigir-header` (é a sua branch de trabalho que traz as correções).

*Se acertou, parabéns! Se errou, não tem problema — a analogia do sistema de recupração ajuda a memorizar: a **Base** é o código oficial!*
</details>

---

## 🤖 3. Mágica do Automático: Fechando Issues com Palavras-Chave

Você sabia que o GitHub pode trabalhar como seu assistente pessoal? 

Normalmente, antes de criar um PR, nós temos uma **Issue** (uma tarefa, bug ou cartão de trabalho cadastrado). Quando terminamos o código do PR, queremos marcar essa Issue como concluída.

Em vez de ir manualmente até a Issue e clicar em "Close", você pode fazer isso **automaticamente** apenas escrevendo uma palavra de comando no corpo (descrição) do seu PR!

### Como funciona?
Basta usar uma **palavra-chave** seguida do símbolo `#` e o **número da Issue**.

#### Exemplo prático:
Se você está resolvendo a Issue de número `#123` (Bug no login) e a Issue `#45` (Ajuste no botão), na descrição do seu PR você escreve:

```markdown
Este PR corrige a validação de e-mail e ajusta o layout do botão.

Closes #123
Fixes #45
```

✨ **A Mágica:** Assim que o mantenedor aprovar e fizer o **Merge** (mesclagem) do seu PR, o GitHub vai **fechar automaticamente** as Issues `#123` e `#45` para você!

### Lista de Palavras-Chave Aceitas:
* `close`, `closes`, `closed`
* `fix`, `fixes`, `fixed`
* `resolve`, `resolves`, `resolved`

---

## 📋 Checklist do PR Perfeito

Antes de clicar no botão "Create Pull Request", passe por este checklist rápido para garantir que seu PR seja aprovado de primeira:

- [ ] **Título claro:** O título descreve resumidamente o que foi feito? *(Ex: "Adiciona validação de CPF na tela de cadastro")*
- [ ] **Descrição informativa:** Expliquei o *porquê* da mudança e o que foi alterado?
- [ ] **Vinculação de Issues:** Adicionei o `Fixes #numero` na descrição?
- [ ] **Revisão própria:** Eu olhei o *Diff* das minhas alterações para garantir que não deixei nenhum arquivo desnecessário ou código de teste para trás?

---

## 💬 Reflexão Final

Um **Pull Request** não é apenas uma entrega de código; é uma **conversa**. É o momento em que a equipe se reúne para trocar ideias, dar sugestões e garantir que o projeto continue saudável. Não tenha medo dos comentários de revisão (Code Review) — eles são a melhor oportunidade para aprender e evoluir!

---
*Pronto para colocar as mãos na massa? Crie sua branch, faça suas alterações e abra seu primeiro PR!*