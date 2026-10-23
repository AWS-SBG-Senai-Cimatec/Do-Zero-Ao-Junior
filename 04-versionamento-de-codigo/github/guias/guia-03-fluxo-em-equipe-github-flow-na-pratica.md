# Guia 03 — Fluxo em equipe: GitHub Flow na prática

## 1. Objetivo

Neste guia, você vai aprender a utilizar o **GitHub Flow**, um fluxo de trabalho que organiza a colaboração entre desenvolvedores usando branches, commits e Pull Requests (PRs).

Ao final, você será capaz de:
- Criar uma branch para trabalhar em uma tarefa.
- Realizar alterações e registrá-las com commits.
- Enviar suas alterações para o GitHub.
- Abrir um Pull Request para revisão.
- Integrar as alterações à branch principal com segurança.

## 2. O que é GitHub Flow?

O GitHub Flow é um fluxo de trabalho simples que permite que várias pessoas contribuam para um mesmo projeto sem precisar realizar todas as alterações diretamente na branch principal.

Cada tarefa é desenvolvida em uma branch separada. Quando o trabalho estiver pronto, o desenvolvedor abre um Pull Request para que as alterações sejam revisadas antes de serem integradas ao projeto.

### Como funciona?

1. **Issue:** identificar a tarefa que será realizada.
2. **Branch:** criar uma branch específica para a tarefa.
3. **Alterações:** desenvolver a funcionalidade ou correção.
4. **Commit:** registrar as alterações.
5. **Push:** enviar a branch para o GitHub.
6. **Pull Request:** solicitar a revisão das alterações.
7. **Review e testes:** corrigir problemas apontados, se necessário.
8. **Merge:** integrar as alterações à branch principal.
9. **Limpeza:** excluir a branch utilizada, quando apropriado.

> **Atenção:** a branch principal (`main`) deve permanecer estável. Evite desenvolver diretamente nela.

## 3. Antes de começar

Você precisa ter:
- Git instalado e configurado.
- Uma conta no GitHub.
- Acesso ao repositório em que vai trabalhar.
- O repositório clonado na sua máquina.
- Conhecimentos básicos de `git status`, `git add`, `git commit`, `git push` e `git pull`.

Confira o estado do repositório:

```bash
git status
```

Verifique a branch atual:

```bash
git branch
```

Se estiver na branch `main`, atualize-a antes de começar:

```bash
git switch main
git pull origin main
```

**Importante:** se você tiver alterações não commitadas, confira o estado do repositório antes de trocar de branch para evitar perder seu trabalho.

## 4. Passo a passo: trabalhando com GitHub Flow

### Passo 1 — Identifique a tarefa

Antes de programar, entenda o que precisa ser feito. Em projetos colaborativos, isso geralmente é descrito em uma Issue.

Exemplo:

- Issue: `#15 — Corrigir validação do formulário`
- Objetivo: impedir que o formulário seja enviado com campos obrigatórios vazios.

Leia a descrição da Issue e verifique se outra pessoa já está trabalhando nela.

### Passo 2 — Crie uma branch

Crie uma branch com um nome que descreva a tarefa:

```bash
git switch -c feat/15-validacao-formulario
```

Nesse exemplo:
- `feat` indica uma nova funcionalidade.
- `15` identifica a Issue.
- `validacao-formulario` descreve a tarefa.

Outros prefixos comuns:

| Prefixo | Uso |
|---|---|
| `feat/` | Nova funcionalidade |
| `fix/` | Correção de um problema |
| `docs/` | Alterações na documentação |
| `refactor/` | Reorganização do código sem mudar seu comportamento esperado |

A convenção de nomes pode variar. Siga o padrão definido pela equipe.

### Passo 3 — Faça as alterações

Trabalhe somente na branch criada para a tarefa.

Depois de modificar os arquivos, confira o que mudou:

```bash
git status
git diff
```

- `git status` mostra os arquivos modificados.
- `git diff` mostra as diferenças nas alterações ainda não preparadas para commit.

Revise o resultado para evitar enviar mudanças desnecessárias.

### Passo 4 — Registre um commit

Selecione os arquivos que deseja incluir:

```bash
git add caminho/do/arquivo
```

Se todas as alterações forem relevantes para a tarefa, você também pode utilizar:

```bash
git add .
```

Em seguida, crie um commit com uma mensagem clara:

```bash
git commit -m "fix: valida campos obrigatorios do formulario"
```

Uma boa mensagem explica o que foi alterado. Evite mensagens vagas como `alterações`, `teste` ou `atualização`.

### Passo 5 — Envie a branch para o GitHub

Envie sua branch para o repositório remoto:

```bash
git push -u origin feat/15-validacao-formulario
```

O parâmetro `-u` configura o acompanhamento da branch remota para facilitar os próximos envios.

Depois do primeiro envio, normalmente basta executar:

```bash
git push
```

### Passo 6 — Abra um Pull Request

No GitHub:

1. Acesse o repositório.
2. Abra a opção **Pull requests**.
3. Clique em **New pull request** ou utilize a sugestão para criar um PR da branch recém-enviada.
4. Selecione `main` como base e sua branch como comparação.
5. Confira as alterações exibidas.
6. Escreva um título e uma descrição objetivos.
7. Solicite a revisão dos responsáveis pelo projeto.

Exemplo de título:

`fix: valida campos obrigatorios do formulario`

Exemplo de descrição:

```markdown
## Objetivo
Corrigir a validação dos campos obrigatórios do formulário.

## Alterações realizadas
- Adicionada validação dos campos obrigatórios.
- Ajustadas as mensagens de erro.

## Testes
- [x] Verificado o comportamento com campos preenchidos.
- [x] Verificado o comportamento com campos vazios.

Closes #15
```

A referência `Closes #15` permite associar o PR à Issue e pode fechá-la automaticamente quando o PR for integrado de forma compatível.

**Dica:** revise o PR antes de enviá-lo. Pull Requests pequenos e bem descritos costumam ser mais fáceis de revisar.

### Passo 7 — Revise e ajuste

Após abrir o PR, outras pessoas podem deixar comentários ou solicitar mudanças.

Para corrigir algo:
1. Continue trabalhando na mesma branch.
2. Faça as alterações solicitadas.
3. Crie novos commits.
4. Envie-os com `git push`.

Os novos commits aparecerão automaticamente no Pull Request aberto.

Se houver verificações automatizadas, aguarde os resultados e corrija os problemas identificados antes da integração.

### Passo 8 — Faça o merge

Quando as revisões e verificações necessárias forem concluídas, uma pessoa autorizada poderá integrar o PR à branch principal.

O GitHub oferece diferentes estratégias de merge:

- **Create a merge commit:** preserva um commit de merge.
- **Squash and merge:** reúne os commits do PR em um único commit na branch de destino.
- **Rebase and merge:** reaplica os commits sobre a branch de destino.

A estratégia depende das regras e preferências do projeto.

Não faça o merge antes das aprovações exigidas pela equipe.

### Passo 9 — Atualize a branch principal e limpe o ambiente

Depois que o PR for integrado, atualize sua branch principal local:

```bash
git switch main
git pull origin main
```

Se a branch de trabalho não for mais necessária, você poderá excluí-la localmente:

```bash
git branch -d feat/15-validacao-formulario
```

A exclusão da branch remota pode ser feita pelo próprio GitHub após o merge ou, se necessário, com:

```bash
git push origin --delete feat/15-validacao-formulario
```

Só exclua branches depois de confirmar que o trabalho foi integrado e que ela não é mais necessária.

## 5. Boas práticas para trabalhar em equipe

- Crie uma branch por tarefa, correção ou funcionalidade.
- Mantenha as alterações pequenas e relacionadas ao objetivo da Issue.
- Escreva mensagens de commit claras.
- Revise o código antes de abrir um PR.
- Descreva o objetivo, as mudanças e os testes realizados.
- Respeite as regras de aprovação e os testes automatizados do projeto.
- Comunique conflitos ou bloqueios à equipe.
- Evite alterar arquivos fora do escopo da tarefa.

## 6. Problemas comuns

| Problema | O que fazer |
|---|---|
| Estou na branch errada | Confira com `git branch` e troque de branch com cuidado. |
| O `git push` foi rejeitado | Verifique se a branch remota recebeu novas alterações e siga o fluxo de sincronização definido pela equipe. |
| Apareceram conflitos | Atualize sua branch conforme as orientações do projeto e resolva os conflitos antes de continuar. |
| O PR está com alterações indevidas | Confira a comparação de branches e corrija a branch antes do merge. |
| O PR não pode ser integrado | Verifique aprovações pendentes, verificações automatizadas e conflitos indicados pelo GitHub. |

## 7. Checklist final

- [ ] Li e entendi a Issue.
- [ ] Criei uma branch específica para a tarefa.
- [ ] Revisei as alterações realizadas.
- [ ] Criei commits com mensagens claras.
- [ ] Enviei a branch para o GitHub.
- [ ] Abri um Pull Request com descrição objetiva.
- [ ] Atendi às solicitações de revisão.
- [ ] Verifiquei as aprovações e os testes exigidos.
- [ ] O PR foi integrado à branch principal.
- [ ] Atualizei a branch principal local e limpei a branch de trabalho, quando apropriado.

## 8. Referências oficiais

- [GitHub Docs — GitHub Flow](https://docs.github.com/en/get-started/using-github/github-flow)
- [GitHub Docs — About pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
- [GitHub Docs — Merging a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/merging-a-pull-request)
- [Git Documentation — git switch](https://git-scm.com/docs/git-switch)
- [Git Documentation — git push](https://git-scm.com/docs/git-push)
