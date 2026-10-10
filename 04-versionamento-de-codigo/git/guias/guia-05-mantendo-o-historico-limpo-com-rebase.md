# Guia 05: Mantendo o Histórico Limpo com Rebase

> 💡 **Analogia da Linha do Tempo:** Imagine que o histórico do seu projeto é a edição de um livro. O `git merge` junta dois capítulos criando um parágrafo que diz *"E aqui estas duas histórias se juntaram"*. Já o `git rebase` faz com que parecido que você escreveu os novos capítulos logo após a última versão do livro, mantendo uma leitura contínua, limpa e fluida.

---

## 📌 Entendendo o Contexto

No trabalho em equipe usando Git, é normal criar uma *branch* (ramificação) para trabalhar em uma nova funcionalidade (*feature*). No entanto, enquanto você desenvolve sua tarefa por alguns dias, a equipe continua aprovando e integrando outros códigos na linha principal (`main`).

Quando chega o momento de enviar o seu trabalho para a aprovação (via *Pull Request*), você se depara com dois cenários:
1. Sua *branch* ficou **desatualizada** em relação à `main`.
2. Seu histórico local está cheio de *commits* de rascunho (ex: *"ajuste rápido"*, *"testando algo"*, *"agora vai"*).

O objetivo deste guia é te ensinar a usar o **`git rebase`** para resolver esses dois problemas: sincronizar seu trabalho sem poluir a linha do tempo e organizar seus *commits* rascunho em uma entrega profissional.

---

## Passo 1: Sincronizando com a branch principal (`git rebase main`)

### O Problema: Histórico em Linha Dupla ou "Nó de Cadarço"
Se usarmos o `git merge main` para atualizar nossa *branch*, o Git cria um *commit de merge* apenas para unir as pontas. Fazer isso repetidas vezes transforma o histórico de *commits* em um emaranhado de linhas cruzadas.

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/f09cc29a-34a4-41ee-85a5-da5b91e783b6" />


### A Solução: Rebase
O `git rebase main` pega todos os *commits* que você fez na sua *branch*, remove-os temporariamente, atualiza sua base com o estado mais recente da `main` e, por fim, reaplica as suas alterações uma a uma no topo.

```bash
# 1. Garanta que está na sua branch de funcionalidade
git checkout feature/sua-feature

# 2. Reaplica seus commits no topo da main atualizada
git rebase main
```

![Terminal executando git rebase main ou histórico linear resultante](placeholder-imagem-02-depois-do-rebase.png)

### 🔍 Entendendo o que acontece por trás dos panos:
* **Base Reorganizada:** A sua *branch* passa a "fingir" que foi criada **hoje**, a partir da versão mais atual da `main`.
* **Histórico Linear:** Não há commits extras de mesclagem (`Merge branch 'main' into...`).

---

## Passo 2: Agrupando commits rascunho (`git rebase -i`)

> 💡 **Analogia da Mochila de Viagem:** Quando você está arrumando as malas no quarto, joga as roupas de qualquer jeito (commits de rascunho). Mas na hora de fechar a mala para viajar, você dobra tudo e organiza em compartimentos limpos (*squash*).

### O Cenário
Você realizou vários commits pequenos enquanto desenvolvia:

![Lista de commits bagunçados no log](placeholder-imagem-03-commits-baguncados.png)

Antes de abrir o *Pull Request*, queremos consolidar esses 3 commits rascunhos em apenas **1 commit semântico e organizado**.

### Comandos para iniciar o Rebase Interativo:

```bash
# Inicia o rebase interativo olhando para os últimos 3 commits
git rebase -i HEAD~3
```

### 🛠️ No Editor do Terminal

Ao executar o comando, o Git abre o seu editor de texto com a lista de commits:

```text
pick a1b2c3d feat: adiciona estrutura da tela de login
pick e4f5g6h wip: ajusta estilos do botao
pick i7j8k9l fix: corrige alinhamento do formulario
```

Para juntar os commits secundários no primeiro:
1. Mantenha o primeiro commit como **`pick`** (ou `p`).
2. Mude os commits seguintes para **`squash`** (ou `s`).

![Editor de texto configurado com os comandos pick e squash](placeholder-imagem-04-editor-rebase-interativo.png)

Após salvar e fechar o editor, defina a mensagem final do commit consolidado:

```text
feat: implementa tela de login completa com estilos e validações
```

![Resultado final no terminal com git log mostrando commit único e limpo](placeholder-imagem-05-historico-consolidado.png)

---

## 🛑 A Regra de Ouro do Rebase

> ⚠️ **Atenção Máxima:** **NUNCA faça rebase em branches públicas/compartilhadas!**
> 
> Como o `git rebase` **reescreve os hashes** dos commits, se você fizer rebase em uma branch que outros desenvolvedores já baixaram (`push`), você irá quebrar o repositório deles.
> 
> **Regra prática:** Use o `rebase` apenas na sua *branch* local **antes** de fazer o `push` para o servidor ou abrir o *Pull Request*.
