# `git restore`

O `git restore` é um comando utilizado para restaurar arquivos, descartando alterações locais ou recuperando versões anteriores do conteúdo. Ele também permite retirar arquivos da área de staging sem apagar as modificações feitas neles.

## 1. Entendendo o conceito

Imagine que você está escrevendo um trabalho e faz alterações em um parágrafo, mas depois percebe que prefere voltar à versão anterior. O `git restore` funciona de maneira semelhante: ele permite recuperar uma versão anterior do arquivo, desde que ela esteja disponível no estado de referência utilizado pelo Git.

No Git, é importante distinguir três áreas:

- **Diretório de trabalho (*working tree*):** onde você edita os arquivos.
- **Índice (*staging area*):** área intermediária em que você prepara as alterações que deseja incluir no próximo commit.
- **Repositório:** onde ficam registrados os commits e o histórico do projeto.

O índice funciona como uma bandeja de preparação: você escolhe quais alterações quer incluir no próximo registro antes de confirmar o commit.

## 2. Como funciona

A sintaxe básica é:

```bash
git restore <arquivo>
```

Esse comando restaura o arquivo no diretório de trabalho de acordo com o conteúdo do índice. Por padrão, as alterações locais nesse arquivo que não estejam representadas no índice são descartadas.

### Principais usos

| Comando | O que acontece |
|---|---|
| `git restore arquivo.txt` | Restaura o arquivo de acordo com o índice, descartando alterações locais que não estejam nele. |
| `git restore --staged arquivo.txt` | Retira o arquivo do staging, mantendo suas alterações no diretório de trabalho. |
| `git restore --source=<commit> -- arquivo.txt` | Restaura o arquivo usando o conteúdo de um commit específico. |

**Atenção:** o comando pode descartar alterações locais. Antes de executá-lo, confira o estado do repositório e, se necessário, salve seu trabalho.

## 3. Exemplos práticos

### Exemplo 1 — Descartar alterações locais

Imagine que você modificou `arquivo.txt`, mas deseja recuperar a versão que está no índice.

```bash
git restore arquivo.txt
```

Confira o estado do repositório antes e depois:

```bash
git status
git restore arquivo.txt
git status
```

Se o arquivo não tiver outras alterações pendentes, ele deixará de aparecer como modificado.

### Exemplo 2 — Retirar um arquivo do staging

Você executou `git add arquivo.txt`, mas decidiu que ainda precisa revisar o arquivo antes de incluí-lo no próximo commit.

```bash
git restore --staged arquivo.txt
```

O arquivo deixa de estar preparado para o próximo commit, mas suas modificações continuam no diretório de trabalho.

Para conferir:

```bash
git status
```

### Exemplo 3 — Recuperar um arquivo de um commit anterior

Você quer recuperar o conteúdo de `arquivo.txt` como estava em um commit específico.

```bash
git restore --source=a1b2c3d -- arquivo.txt
```

Nesse exemplo, `a1b2c3d` é apenas um identificador ilustrativo. Substitua-o pelo hash real do commit desejado.

O conteúdo desse commit será colocado no diretório de trabalho. A alteração ainda não será registrada em um novo commit automaticamente.

## 4. O que é o hash de um commit?

O hash é um identificador gerado pelo Git para identificar um commit. Ele é representado por uma sequência de caracteres hexadecimais, formada pelos números de `0` a `9` e pelas letras de `a` a `f`.

Pense nele como o código de identificação de uma versão registrada do projeto. Com esse identificador, você consegue referenciar um ponto específico do histórico.

### Como descobrir o hash?

Para visualizar os commits de forma resumida, utilize:

```bash
git log --oneline
```

Exemplo de saída ilustrativa:

```text
a1b2c3d Corrige validação do formulário
e4f5g6h Adiciona tela de cadastro
i7j8k9l Cria estrutura inicial
```

Os identificadores mostrados são exemplos. No seu repositório, os hashes e as mensagens serão diferentes.

Para usar um commit no `git restore`, copie o identificador correspondente e informe-o em `--source`.

## 5. Representação visual

O fluxo abaixo mostra a diferença entre retirar um arquivo do staging e descartar alterações locais.

```text
RETIRAR DO STAGING

Índice (staging)
      |
      | git restore --staged arquivo.txt
      v
Diretório de trabalho
(continua com as modificações)


DESCARTAR ALTERAÇÕES LOCAIS

Índice (staging)
      |
      | git restore arquivo.txt
      v
Diretório de trabalho
(volta ao conteúdo do índice)
```

## 6. Cuidados importantes

- `git restore` não cria um novo commit.
- `git restore --staged` retira as alterações do staging, mas não as apaga do diretório de trabalho.
- `git restore <arquivo>` pode descartar modificações locais que ainda não foram salvas em um commit.
- Ao utilizar `--source`, confira se o commit informado contém a versão do arquivo que você deseja recuperar.
- Se estiver em dúvida, execute `git status` antes de restaurar o arquivo.

## Referências

- [Documentação oficial do Git — git restore](https://git-scm.com/docs/git-restore)
- [Pro Git — Desfazendo coisas](https://git-scm.com/book/pt-br/v2/Noções-Básicas-do-Git-Desfazendo-Coisas)
