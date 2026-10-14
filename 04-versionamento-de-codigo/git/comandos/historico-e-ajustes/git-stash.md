# `git stash`

O `git stash` permite guardar temporariamente alterações que ainda não foram commitadas, deixando o diretório de trabalho limpo para você realizar outra tarefa sem precisar criar um commit.

É útil quando você está trabalhando em uma funcionalidade e precisa mudar de contexto rapidamente, sem perder o progresso atual.

## Como funciona

```bash
git stash
```

O comando guarda as alterações rastreadas que estão no diretório de trabalho e no staging. Por padrão, arquivos novos que ainda não foram rastreados pelo Git não são incluídos.

## Principais comandos

| **Comando** | **O que faz** |
|---|---|
| `git stash` | Guarda temporariamente as alterações rastreadas. |
| `git stash list` | Lista as alterações guardadas. |
| `git stash apply` | Recupera as alterações sem remover o registro do stash. |
| `git stash pop` | Recupera as alterações e remove o registro do stash se a aplicação for bem-sucedida. |
| `git stash drop` | Remove um registro do stash. |
| `git stash clear` | Remove todos os registros do stash. |

## Exemplos práticos

### 1. Guardar as alterações

```bash
git stash
```

Salva temporariamente as alterações rastreadas para que você possa trabalhar em outra tarefa com o diretório limpo.

Para incluir também arquivos novos ainda não rastreados, utilize:

```bash
git stash -u
```

### 2. Consultar os registros guardados

```bash
git stash list
```

Exibe os registros armazenados. Eles costumam aparecer como `stash@{0}`, `stash@{1}` e assim por diante.

### 3. Recuperar as alterações

Para recuperar as alterações sem remover o registro:

```bash
git stash apply
```

Para recuperar as alterações e remover o registro quando a aplicação for bem-sucedida:

```bash
git stash pop
```

### 4. Recuperar um registro específico

```bash
git stash apply stash@{1}
```

Aplica as alterações do registro indicado. Substitua `stash@{1}` pelo registro desejado.

### 5. Remover um registro

```bash
git stash drop stash@{0}
```

Remove o registro indicado do stash. Tenha cuidado, pois as alterações guardadas nesse registro deixam de estar disponíveis por esse mecanismo.

## Cuidados importantes

- O `git stash` não cria um commit.
- Por padrão, arquivos novos não rastreados não são incluídos; use `git stash -u` quando necessário.
- Ao recuperar alterações, podem ocorrer conflitos se os arquivos tiverem mudado desde que o stash foi criado.
- Antes de remover registros, confira o conteúdo e a lista com `git stash list`.

## Referências

- [Documentação oficial do Git — git stash](https://git-scm.com/docs/git-stash)
- [Pro Git — Guardando alterações temporariamente](https://git-scm.com/book/pt-br/v2/Ferramentas-do-Git-Stashing-e-Limpeza)
