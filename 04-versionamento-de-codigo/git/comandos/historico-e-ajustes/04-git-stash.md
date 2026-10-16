# `git stash`

O `git stash` permite guardar temporariamente alterações que ainda não foram commitadas. Assim, você pode mudar de tarefa sem precisar registrar um commit com um trabalho que ainda não está pronto.

É útil quando você está desenvolvendo uma funcionalidade e precisa interromper o trabalho para resolver outra tarefa.

## 1. Entendendo o conceito

Imagine que você está montando um quebra-cabeça e precisa liberar a mesa para fazer outra atividade. Em vez de desmontar o que já fez, você guarda as peças para continuar depois.

O `git stash` funciona de forma semelhante: ele guarda temporariamente determinadas alterações e deixa o diretório de trabalho limpo para você continuar trabalhando.

## 2. Como funciona

A sintaxe básica é:

```bash
git stash
```

Por padrão, o comando guarda alterações em arquivos rastreados pelo Git, incluindo modificações no diretório de trabalho e no staging. Arquivos novos ainda não rastreados não são incluídos por padrão.

### Principais comandos

| **Comando** | **O que faz** |
|---|---|
| `git stash` | Guarda temporariamente as alterações rastreadas. |
| `git stash -u` | Inclui também arquivos novos ainda não rastreados. |
| `git stash list` | Lista os registros guardados. |
| `git stash apply` | Recupera alterações sem remover o registro do stash. |
| `git stash pop` | Recupera alterações e remove o registro se a aplicação for bem-sucedida. |
| `git stash drop` | Remove um registro específico. |
| `git stash clear` | Remove todos os registros guardados. |

## 3. Exemplos práticos

### Exemplo 1 — Guardar as alterações

Imagine que você modificou um arquivo, mas precisa mudar de tarefa antes de terminar.

```bash
git stash
```

Para verificar o estado do repositório:

```bash
git status
```

Se não houver outras alterações pendentes, o diretório de trabalho ficará limpo.

### Exemplo 2 — Guardar arquivos novos também

Se você criou um arquivo que ainda não foi rastreado pelo Git, utilize:

```bash
git stash -u
```

A opção `-u` inclui arquivos não rastreados no stash, além das alterações rastreadas.

### Exemplo 3 — Consultar os registros guardados

```bash
git stash list
```

Exemplo de saída ilustrativa:

```text
stash@{0}: WIP on main: a1b2c3d Ajusta formulário
stash@{1}: WIP on main: e4f5g6h Cria tela inicial
```

Cada registro recebe uma referência, como `stash@{0}`. Normalmente, o registro mais recente aparece nessa posição.

### Exemplo 4 — Recuperar as alterações

Para recuperar as alterações sem remover o registro:

```bash
git stash apply
```

Para recuperar as alterações e remover o registro caso a aplicação seja bem-sucedida:

```bash
git stash pop
```

Se quiser recuperar um registro específico, informe sua referência:

```bash
git stash apply stash@{1}
```

### Exemplo 5 — Remover um registro

Para remover um registro específico:

```bash
git stash drop stash@{0}
```

Para remover todos os registros guardados:

```bash
git stash clear
```

**Atenção:** esses comandos removem registros do stash. Confira a lista antes de utilizá-los para evitar perder alterações que ainda deseja recuperar.

## 4. Representação visual

O fluxo abaixo mostra como o stash permite interromper e retomar um trabalho.

```text
Alterações em andamento
          |
          v
     git stash
          |
          v
Diretório de trabalho limpo
          |
          v
   Realizar outra tarefa
          |
          v
    git stash pop
          |
          v
Retomar as alterações guardadas
```

O stash não cria um commit comum na branch. Ele armazena temporariamente as alterações para que você possa recuperá-las depois.

## 5. E se ocorrer um conflito?

Se os arquivos tiverem mudado desde que o stash foi criado, o Git pode encontrar conflitos ao tentar recuperar as alterações.

Nesse caso, será necessário resolver os conflitos nos arquivos afetados. Depois, confira o resultado com:

```bash
git status
```

Não presuma que a recuperação foi concluída corretamente sem verificar o estado do repositório.

## 6. Cuidados importantes

- O `git stash` não cria um commit comum na branch.
- Arquivos novos não rastreados precisam da opção `-u` para serem incluídos.
- O `apply` mantém o registro guardado; o `pop` normalmente o remove quando a aplicação funciona.
- Antes de usar `drop` ou `clear`, confira se você ainda precisa das alterações armazenadas.
- A recuperação pode gerar conflitos se o projeto tiver mudado desde a criação do stash.

## Referências

- [Documentação oficial do Git — git stash](https://git-scm.com/docs/git-stash)
- [Pro Git — Guardando alterações temporariamente](https://git-scm.com/book/pt-br/v2/Ferramentas-do-Git-Stashing-e-Limpeza)
