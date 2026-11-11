# `git reset`

O `git reset` é utilizado para mover a referência da branch para outro commit. Dependendo da opção escolhida, ele também pode modificar o índice (*staging area*) e o diretório de trabalho.

É útil quando você deseja corrigir um commit local, reorganizar alterações ou voltar para um ponto anterior do histórico.

## 1. Entendendo o conceito

Imagine que o histórico do Git é como um caderno em que cada commit registra uma etapa do seu projeto. O `git reset` permite voltar a referência da branch para uma etapa anterior.

Entretanto, voltar a referência não significa necessariamente apagar todas as alterações. O resultado depende da opção utilizada.

O Git trabalha com três elementos importantes:

- **Histórico de commits:** registra as versões salvas do projeto.
- **Índice (*staging area*):** reúne as alterações preparadas para o próximo commit.
- **Diretório de trabalho (*working tree*):** contém os arquivos que você está editando.

## 2. Como funciona

A sintaxe básica é:

```bash
git reset [opção] <commit>
```

O argumento `<commit>` indica o ponto do histórico para o qual a referência da branch será movida.

Por exemplo, `HEAD~1` representa o commit imediatamente anterior ao commit atual.

### Principais opções

| **Opção** | **O que acontece** |
|---|---|
| `--soft` | Move a referência da branch, mantendo as alterações no índice. |
| `--mixed` | Move a referência e atualiza o índice, mantendo as modificações no diretório de trabalho. É a opção padrão. |
| `--hard` | Move a referência e atualiza o índice e o diretório de trabalho para o estado do commit escolhido. Pode descartar alterações locais. |

## 3. Exemplos práticos

### Exemplo 1 — Voltar um commit mantendo as alterações no staging

```bash
git reset --soft HEAD~1
```

Imagine que você fez um commit, mas percebeu que ainda precisa ajustar alguma coisa. Com `--soft`, a referência da branch volta um commit e as alterações continuam preparadas no staging.

Para conferir o estado do repositório:

```bash
git status
```

### Exemplo 2 — Voltar um commit mantendo as alterações nos arquivos

```bash
git reset HEAD~1
```

Como `--mixed` é a opção padrão, esse comando volta a referência da branch em um commit e retira as alterações do staging, mas mantém as modificações nos arquivos.

Você poderá revisar os arquivos e decidir o que adicionar novamente:

```bash
git status
git add <arquivo>
```

### Exemplo 3 — Voltar um commit descartando alterações locais

```bash
git reset --hard HEAD~1
```

Essa opção atualiza a referência da branch, o índice e os arquivos para o estado do commit escolhido.

**Atenção:** alterações locais não commitadas podem ser perdidas. Antes de executar o comando, confira o estado do repositório e salve o que deseja preservar.

## 4. Representação visual

O diagrama abaixo resume como as opções afetam o índice e o diretório de trabalho ao voltar um commit.

```text
                  git reset
                      |
          +-----------+-----------+
          |           |           |
        --soft      --mixed      --hard
          |           |           |
      Mantém o     Atualiza o   Atualiza o
      staging      staging      staging
          |           |           |
      Mantém os    Mantém os    Atualiza os
      arquivos     arquivos     arquivos
```

As três opções movem a referência da branch para o commit escolhido. A diferença está no que acontece com o índice e os arquivos locais.

## 5. Como consultar o histórico

Antes de voltar para um commit, você pode visualizar o histórico resumido:

```bash
git log --oneline
```

Exemplo de saída ilustrativa:

```text
a1b2c3d Corrige validação do formulário
e4f5g6h Adiciona tela de cadastro
i7j8k9l Cria estrutura inicial
```

Os identificadores acima são fictícios. Para voltar a um commit específico, utilize o hash real correspondente ao histórico do seu repositório.

## 6. Cuidados importantes

- O `git reset` pode reescrever o histórico da branch.
- Evite utilizá-lo para alterar commits que já foram compartilhados com outras pessoas.
- O `--hard` pode descartar alterações locais que você ainda não salvou.
- Confira o histórico e o estado dos arquivos antes de executar o comando.
- Se quiser desfazer um commit compartilhado sem reescrever o histórico, considere o `git revert`.

## Referências

- [Documentação oficial do Git — git reset](https://git-scm.com/docs/git-reset)
- [Pro Git — Desfazendo coisas](https://git-scm.com/book/pt-br/v2/Noções-Básicas-do-Git-Desfazendo-Coisas)
