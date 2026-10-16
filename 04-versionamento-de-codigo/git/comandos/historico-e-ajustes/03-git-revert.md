# `git revert`

O `git revert` é utilizado para desfazer as alterações introduzidas por um commit, criando um novo commit com as mudanças inversas.

É especialmente útil quando você precisa desfazer uma alteração sem apagar o registro do commit original no histórico do projeto.

## 1. Entendendo o conceito

Imagine que você registrou uma mudança no seu caderno de projeto, mas depois percebeu que ela estava incorreta. Em vez de apagar o registro anterior, você faz uma nova anotação corrigindo o que foi feito.

O `git revert` funciona de maneira semelhante: ele cria um novo commit para desfazer as alterações de outro commit, preservando o histórico original.

## 2. Como funciona

A sintaxe básica é:

```bash
git revert <commit>
```

O argumento `<commit>` identifica o commit cujas alterações você deseja desfazer.

Para consultar o histórico e encontrar o identificador do commit, utilize:

```bash
git log --oneline
```

Exemplo de saída ilustrativa:

```text
a1b2c3d Corrige validação do formulário
e4f5g6h Adiciona tela de cadastro
i7j8k9l Cria estrutura inicial
```

Os identificadores acima são fictícios. No seu repositório, utilize o hash real do commit desejado.

## 3. Exemplos práticos

### Exemplo 1 — Desfazer o último commit

```bash
git revert HEAD
```

O Git prepara a reversão do commit mais recente e, normalmente, cria um novo commit para registrar as alterações inversas.

Se necessário, o Git abrirá um editor para confirmar a mensagem do novo commit.

### Exemplo 2 — Desfazer um commit específico

```bash
git revert a1b2c3d
```

Substitua `a1b2c3d` pelo hash do commit que deseja reverter.

O Git tentará desfazer as alterações introduzidas por esse commit sem remover o registro original do histórico.

### Exemplo 3 — Preparar a reversão sem criar o commit imediatamente

```bash
git revert --no-commit HEAD
```

Aplica as alterações inversas sem criar o commit automaticamente. Assim, você pode revisar o resultado antes de registrá-lo.

Para conferir as alterações, utilize:

```bash
git status
git diff
```

Quando estiver tudo certo, você poderá preparar e registrar as alterações:

```bash
git add .
git commit -m "Reverte alterações anteriores"
```

## 4. Representação visual

O diagrama abaixo mostra a diferença entre o histórico antes e depois de uma reversão.

```text
ANTES

A ---- B ---- C
             |
       Commit incorreto


DEPOIS DO git revert C

A ---- B ---- C ---- D
                    |
              Novo commit
              que desfaz C
```

O commit `C` continua no histórico. O novo commit `D` registra as alterações necessárias para desfazer o efeito de `C`.

## 5. E se ocorrer um conflito?

Um conflito pode acontecer quando alterações posteriores dificultam a aplicação da reversão.

Nesse caso, o Git solicitará que você resolva os conflitos nos arquivos afetados.

Depois de corrigir os arquivos, utilize:

```bash
git add <arquivo>
git revert --continue
```

Se quiser cancelar uma reversão que ainda está em andamento:

```bash
git revert --abort
```

## 6. `git revert` ou `git reset`?

| **Comando** | **Principal diferença** |
|---|---|
| `git revert` | Cria um novo commit para desfazer alterações, preservando os commits anteriores no histórico. |
| `git reset` | Move a referência da branch para outro commit e pode modificar o staging e os arquivos locais. |

**Dica:** quando precisar desfazer um commit que já foi compartilhado com outras pessoas, o `git revert` costuma ser a opção mais segura, pois não exige reescrever o histórico compartilhado.

## 7. Cuidados importantes

- O `git revert` não apaga o commit original.
- A reversão pode gerar conflitos que precisam ser resolvidos manualmente.
- Revise as alterações antes de confirmar a reversão.
- Reverter um commit não significa necessariamente restaurar todo o projeto ao estado anterior: outras mudanças posteriores podem continuar presentes.

## Referências

- [Documentação oficial do Git — git revert](https://git-scm.com/docs/git-revert)
- [Pro Git — Desfazendo coisas](https://git-scm.com/book/pt-br/v2/Noções-Básicas-do-Git-Desfazendo-Coisas)
