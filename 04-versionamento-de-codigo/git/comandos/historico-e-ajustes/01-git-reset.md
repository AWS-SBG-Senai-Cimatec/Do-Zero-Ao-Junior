# `git reset`

O `git reset` é utilizado para voltar a branch para um ponto anterior do histórico e, dependendo da opção escolhida, modificar o estado dos arquivos e da área de staging.

É útil quando você precisa corrigir um commit local ou retirar arquivos do staging. Porém, é importante entender cada opção, pois algumas podem descartar alterações.

## Como funciona

```bash
git reset [opção] <commit>
```

O comando recebe um commit como referência. Por exemplo, `HEAD~1` representa o commit imediatamente anterior ao atual.

## Principais opções

| **Opção** | **O que acontece** |
|---|---|
| `--soft` | Move a branch para o commit escolhido e mantém as alterações no staging. |
| `--mixed` | Move a branch e retira as alterações do staging, mas mantém as modificações nos arquivos. É a opção padrão. |
| `--hard` | Move a branch e restaura os arquivos e o staging para o estado do commit escolhido. Alterações locais podem ser perdidas. |

## Exemplos práticos

### **1. Voltar um commit mantendo o staging**

```bash
git reset --soft HEAD~1
```

A branch volta um commit, mas as alterações continuam preparadas para um novo commit. Isso é útil quando você deseja corrigir a mensagem ou reorganizar um commit recente.

### **2. Voltar um commit mantendo as alterações nos arquivos**

```bash
git reset HEAD~1
```

Como `--mixed` é a opção padrão, o último commit deixa de ser a ponta da branch, e suas alterações permanecem nos arquivos, fora do staging.

### **3. Voltar um commit descartando as alterações**

```bash
git reset --hard HEAD~1
```

A branch volta um commit e os arquivos e o staging são restaurados para esse estado. Alterações não commitadas podem ser perdidas, por isso use essa opção com cuidado.

## Qual opção escolher?

- **`--soft`:** quando você quer refazer um commit e manter as alterações preparadas.
- **`--mixed`:** quando quer refazer um commit e revisar as alterações antes de adicioná-las novamente.
- **`--hard`:** quando deseja descartar alterações e retornar ao estado de um commit, após confirmar que não precisa delas.

Antes de executar o comando, confira o estado do repositório:

```bash
git status
git log --oneline -5
```

**Atenção:** o `git reset` pode reescrever o histórico da branch. Evite utilizá-lo em commits que outras pessoas já estão usando em uma branch compartilhada. Para desfazer um commit sem reescrever o histórico, considere o `git revert`.

## Referências

- [Documentação oficial do Git — git reset](https://git-scm.com/docs/git-reset)
- [Pro Git — Desfazendo coisas](https://git-scm.com/book/pt-br/v2/Noções-Básicas-do-Git-Desfazendo-Coisas)
