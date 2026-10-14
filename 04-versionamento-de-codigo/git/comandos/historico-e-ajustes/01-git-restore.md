# git restore

O git restore é útil quando você fez alterações em um arquivo e quer voltar à versão anterior sem mexer diretamente no histórico de commits. Ele também permite retirar arquivos da área de staging sem perder as modificações feitas.

## Como funciona

```bash
git restore <arquivo>
```

Esse comando restaura o arquivo para o conteúdo registrado no índice do Git. Em uma situação comum, isso significa descartar as alterações locais feitas desde o último `git add` ou commit, dependendo do estado do arquivo.

### Descartando alterações

Imagine que você modificou `main.c`, mas decidiu não manter as mudanças:

```bash
git restore main.c
```

O arquivo volta ao conteúdo registrado no índice. Como as alterações descartadas podem ser difíceis de recuperar, confira o estado do arquivo antes de executar o comando.

### Retirando um arquivo do staging

Se você executou `git add main.c`, mas quer continuar editando antes de criar o commit, use:

```bash
git restore --staged main.c
```

O arquivo deixa de estar preparado para o próximo commit, mas as modificações continuam no diretório de trabalho.

### Recuperando uma versão de outro commit

Também é possível usar um commit como origem da restauração:

```bash
git restore --source=abc1234 -- main.c
```

Nesse exemplo, `abc1234` representa o identificador do commit desejado. O conteúdo desse commit é recuperado no arquivo, mas a branch continua onde estava.

## Qual opção usar?

| Comando | Resultado |
|---|---|
| `git restore main.c` | Descarta alterações locais do arquivo. |
| `git restore --staged main.c` | Retira o arquivo do staging e preserva as alterações locais. |
| `git restore --source=abc1234 -- main.c` | Recupera o conteúdo do arquivo a partir de outro commit. |

Antes de restaurar arquivos, vale conferir o que foi modificado:

```bash
git status
git diff
```

**Atenção:** `git restore` não é a ferramenta indicada para desfazer um commit já compartilhado. Para isso, o `git revert` costuma ser mais apropriado, pois cria um novo commit que desfaz as alterações anteriores.

## Referências

- [Documentação oficial do Git — git restore](https://git-scm.com/docs/git-restore)
- [Pro Git — Desfazendo coisas](https://git-scm.com/book/pt-br/v2/Noções-Básicas-do-Git-Desfazendo-Coisas)
