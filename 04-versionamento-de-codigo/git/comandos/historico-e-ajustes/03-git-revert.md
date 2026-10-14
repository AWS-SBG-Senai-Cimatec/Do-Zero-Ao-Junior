# `git revert`

O `git revert` é utilizado para desfazer as alterações introduzidas por um commit, criando um **novo commit** que aplica as mudanças inversas.

Diferentemente do `git reset`, ele não remove o commit anterior do histórico. Por isso, costuma ser uma opção mais segura para desfazer mudanças em branches compartilhadas.

## Como funciona

```bash
git revert <commit>
```

O comando recebe como referência o commit que você deseja desfazer. O Git cria um novo commit com as alterações necessárias para revertê-lo.

## Exemplos práticos

### 1. Desfazer o último commit

```bash
git revert HEAD
```

Cria um novo commit que desfaz as alterações introduzidas pelo commit mais recente.

### 2. Desfazer um commit específico

```bash
git revert a1b2c3d
```

Substitua `a1b2c3d` pelo identificador do commit que deseja reverter. O histórico original é preservado, e um novo commit registra a reversão.

### 3. Reverter sem criar o commit imediatamente

```bash
git revert --no-commit HEAD
```

Aplica as alterações inversas sem criar o commit automaticamente, permitindo revisar as modificações antes de registrá-las.

## E se ocorrer um conflito?

Pode acontecer de as alterações feitas depois do commit dificultarem a reversão. Nesse caso, o Git pode solicitar que você resolva os conflitos antes de continuar.

Após corrigir os arquivos, utilize:

```bash
git add <arquivo>
git revert --continue
```

Se quiser cancelar uma reversão que ainda está em andamento, utilize:

```bash
git revert --abort
```

## `git revert` ou `git reset`?

| **Comando** | **Principal diferença** |
|---|---|
| `git revert` | Cria um novo commit para desfazer alterações, preservando o histórico existente. |
| `git reset` | Move a referência da branch para outro commit e pode alterar o staging e os arquivos locais. |

**Dica:** prefira `git revert` quando precisar desfazer um commit que já foi compartilhado com outras pessoas, pois ele evita reescrever o histórico existente.

## Referências

- [Documentação oficial do Git — git revert](https://git-scm.com/docs/git-revert)
- [Pro Git — Desfazendo coisas](https://git-scm.com/book/pt-br/v2/Noções-Básicas-do-Git-Desfazendo-Coisas)
