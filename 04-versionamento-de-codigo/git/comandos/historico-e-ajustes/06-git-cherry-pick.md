# `git cherry-pick`

O `git cherry-pick` permite aplicar as alterações introduzidas por um commit específico na branch atual, sem precisar incorporar todos os commits de outra branch.

É útil quando você deseja aproveitar uma correção ou funcionalidade que foi desenvolvida em outra branch, mas não quer trazer todo o histórico dela.

## 1. Entendendo o conceito

Imagine que um colega escreveu várias páginas de um relatório, mas você precisa apenas de uma delas para o seu próprio trabalho. Em vez de copiar o relatório inteiro, você seleciona somente a parte necessária.

O `git cherry-pick` funciona de maneira semelhante: ele seleciona um commit específico e aplica suas alterações à branch atual.

## 2. Como funciona

A sintaxe básica é:

```bash
git cherry-pick <commit>
```

O argumento `<commit>` identifica o commit cujas alterações você deseja aplicar.

Para localizar o identificador de um commit, você pode consultar o histórico:

```bash
git log --oneline
```

Exemplo de saída ilustrativa:

```text
a1b2c3d Corrige validação do formulário
e4f5g6h Adiciona tela de cadastro
i7j8k9l Cria estrutura inicial
```

Os hashes acima são exemplos. Utilize o identificador real do commit que deseja selecionar.

## 3. Exemplos práticos

### Exemplo 1 — Aplicar um commit específico

Imagine que você está na branch `minha-feature` e deseja trazer uma correção feita em outra branch.

Primeiro, confirme a branch atual:

```bash
git switch minha-feature
```

Depois, aplique o commit desejado:

```bash
git cherry-pick a1b2c3d
```

O Git aplicará as alterações desse commit na branch atual e, normalmente, criará um novo commit para registrá-las.

### Exemplo 2 — Aplicar vários commits específicos

Você também pode selecionar mais de um commit, informando seus identificadores:

```bash
git cherry-pick a1b2c3d e4f5g6h
```

Os commits serão aplicados na ordem informada. Certifique-se de que essa ordem faz sentido para as dependências entre as alterações.

### Exemplo 3 — Aplicar alterações sem criar o commit imediatamente

Se quiser aplicar as alterações e revisá-las antes de criar um commit, utilize:

```bash
git cherry-pick --no-commit a1b2c3d
```

Depois, confira o estado do repositório:

```bash
git status
git diff
```

Quando estiver satisfeito com o resultado, você poderá preparar e registrar as alterações.

## 4. Representação visual

Imagine que a branch `main` possui uma correção que você deseja aproveitar em `minha-feature`.

```text
ANTES

A --- B --- C  (main)
       \
        D --- E  (minha-feature)


APÓS git cherry-pick C

A --- B --- C  (main)
       \       \
        D --- E --- C'  (minha-feature)
```

O commit `C'` representa a aplicação das alterações de `C` na branch atual. Ele é um novo commit, com identificador próprio, mesmo que suas alterações sejam equivalentes às do commit original.

O diagrama é ilustrativo: a posição exata dos commits depende do histórico real do repositório.

## 5. E se ocorrer um conflito?

Um conflito pode acontecer quando as alterações do commit selecionado não podem ser aplicadas automaticamente ao conteúdo atual dos arquivos.

Nesse caso:

**1.** Confira os arquivos afetados.

```bash
git status
```

**2.** Resolva os conflitos manualmente nos arquivos indicados.

**3.** Marque os arquivos como resolvidos.

```bash
git add <arquivo>
```

**4.** Continue a operação.

```bash
git cherry-pick --continue
```

Se quiser cancelar a operação em andamento:

```bash
git cherry-pick --abort
```

## 6. `git cherry-pick` ou `git rebase`?

| **Comando** | **Principal diferença** |
|---|---|
| `git cherry-pick` | Seleciona um ou mais commits específicos para aplicar na branch atual. |
| `git rebase` | Reaplica uma sequência de commits sobre uma nova base. |

Use `git cherry-pick` quando precisar de alterações específicas. Considere `git rebase` quando quiser reorganizar a base de uma sequência de commits.

## 7. Cuidados importantes

- O `git cherry-pick` normalmente cria novos commits, com identificadores diferentes dos originais.
- Aplicar o mesmo commit mais de uma vez pode gerar alterações duplicadas ou conflitos.
- Antes de executar o comando, confira a branch atual e o commit selecionado.
- Se houver conflitos, resolva-os antes de continuar.
- Em projetos compartilhados, siga as convenções da equipe antes de trazer commits de outras branches.

## Referências

- [Documentação oficial do Git — git cherry-pick](https://git-scm.com/docs/git-cherry-pick)
- [Pro Git — Fundamentos do Git](https://git-scm.com/book/pt-br/v2)
