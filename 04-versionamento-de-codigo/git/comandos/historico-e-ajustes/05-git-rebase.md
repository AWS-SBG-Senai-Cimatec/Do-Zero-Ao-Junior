# `git rebase`

O `git rebase` é um comando utilizado para reaplicar commits sobre uma nova base. Ele permite reorganizar o histórico de uma branch, deixando a sequência de alterações mais linear.

É útil quando você está trabalhando em uma branch separada e deseja incorporar os commits mais recentes de outra branch ao seu trabalho.

## 1. Entendendo o conceito

Imagine que você está escrevendo um relatório e outra pessoa atualiza a versão principal enquanto você trabalha em uma cópia. Em vez de manter seu trabalho baseado em uma versão antiga, você reaplica suas alterações sobre a versão atualizada.

O `git rebase` funciona de maneira semelhante: ele reaplica os commits da sua branch sobre outro ponto do histórico.

## 2. Como funciona

A sintaxe básica é:

```bash
git rebase <branch>
```

O Git identifica os commits exclusivos da branch atual e tenta reaplicá-los sobre a branch indicada.

Por exemplo:

```bash
git rebase main
```

Esse comando reaplica os commits da branch atual sobre a versão mais recente de `main` disponível no seu repositório local.

**Importante:** se quiser obter as atualizações mais recentes do repositório remoto, primeiro você precisa atualizar suas referências, por exemplo, com `git fetch`.

## 3. Exemplo prático

Imagine que você criou uma branch chamada `minha-feature` a partir de `main`. Enquanto desenvolvia, novos commits foram adicionados à `main`.

Antes do rebase, o histórico pode ser representado assim:

```text
A --- B --- C  (main)
       \
        D --- E  (minha-feature)
```

A branch `minha-feature` possui os commits `D` e `E`, enquanto `main` avançou até `C`.

Execute:

```bash
git switch minha-feature
git rebase main
```

Depois do rebase, o histórico fica semelhante a este:

```text
A --- B --- C  (main)
             \
              D' --- E'  (minha-feature)
```

Os commits `D'` e `E'` representam as alterações reaplicadas. Eles recebem novos identificadores porque o rebase cria novos commits.

## 4. E se ocorrer um conflito?

Um conflito acontece quando o Git não consegue reaplicar automaticamente alguma alteração, geralmente porque houve mudanças incompatíveis nos mesmos trechos de um arquivo.

Nesse caso, siga estes passos:

**1.** Verifique quais arquivos apresentam conflitos.

```bash
git status
```

**2.** Abra os arquivos indicados, resolva os conflitos e salve as alterações.

**3.** Marque os arquivos como resolvidos.

```bash
git add <arquivo>
```

**4.** Continue o rebase.

```bash
git rebase --continue
```

Se quiser cancelar a operação em andamento e retornar ao estado anterior ao rebase:

```bash
git rebase --abort
```

## 5. `git rebase` ou `git merge`?

| **Comando** | **Principal diferença** |
|---|---|
| `git rebase` | Reaplica commits sobre uma nova base, criando um histórico linear quando a operação é concluída sem interrupções adicionais. |
| `git merge` | Integra históricos de branches diferentes e pode criar um commit de merge. |

O rebase não é necessariamente melhor que o merge. A escolha depende do fluxo de trabalho e das regras do projeto.

## 6. Cuidados importantes

- O rebase pode alterar os identificadores dos commits reaplicados.
- Evite fazer rebase de commits que outras pessoas já utilizam em uma branch compartilhada.
- Antes de iniciar, confira o estado do repositório com `git status`.
- Se houver trabalho importante ainda não commitado, salve-o ou guarde-o temporariamente antes de começar.
- Em caso de dúvida durante um conflito, use `git status` para identificar o próximo passo.

## Referências

- [Documentação oficial do Git — git rebase](https://git-scm.com/docs/git-rebase)
- [Pro Git — Fazendo o rebase](https://git-scm.com/book/pt-br/v2/Branches-no-Git-Rebase)
