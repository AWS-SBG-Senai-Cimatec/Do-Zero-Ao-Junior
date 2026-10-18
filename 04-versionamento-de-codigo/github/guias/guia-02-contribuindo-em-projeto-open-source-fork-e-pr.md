# Guia 02 — Contribuindo em projetos Open Source: Fork e Pull Request

## 🎯 Objetivo

Aprender o fluxo de contribuição para projetos Open Source no GitHub, desde a criação de um fork até a abertura de um Pull Request (PR).

Ao final deste guia, você será capaz de:

- Entender a diferença entre repositório original e fork.
- Clonar seu fork para o computador.
- Configurar o repositório original como `upstream`.
- Criar uma branch para suas alterações.
- Realizar commits e enviar alterações ao seu fork.
- Abrir um Pull Request para propor suas mudanças ao projeto original.

## 📋 Pré-requisitos

Antes de começar, tenha:

- Uma conta no [GitHub](https://github.com/).
- Git instalado e configurado no computador.
- Conhecimentos básicos de terminal, commits e branches.
- Acesso a um repositório público no qual você deseja praticar.

Confira a instalação do Git:

```bash
git --version
```

## 1. Entendendo o fluxo de contribuição

Open Source é um modelo de desenvolvimento no qual o código-fonte de um projeto pode ser disponibilizado para estudo, uso ou contribuição, conforme sua licença.

Em muitos projetos, colaboradores externos não possuem permissão para modificar diretamente o repositório original. Por isso, o GitHub oferece o mecanismo de **Fork**.

Um fork é uma cópia de um repositório hospedada na sua conta ou em uma organização. Ele permite que você trabalhe de forma independente e proponha alterações ao projeto original por meio de um Pull Request.

### Fork, clone e branch: qual é a diferença?

| Conceito | O que significa |
|---|---|
| **Repositório original** | Projeto mantido pela comunidade ou pelos responsáveis. |
| **Fork** | Cópia do repositório hospedada em outra conta ou organização. |
| **Clone** | Cópia local de um repositório no seu computador. |
| **Branch** | Linha de desenvolvimento isolada dentro de um repositório. |
| **Commit** | Registro de um conjunto de alterações. |
| **Pull Request (PR)** | Proposta para revisar e integrar alterações em outra branch ou repositório. |

Pense no repositório original como um livro publicado. O fork é uma cópia sobre a qual você pode trabalhar, o clone é a cópia que você leva para seu computador e o Pull Request é a proposta que você apresenta ao responsável pela publicação.

### Visão geral do fluxo

```text
Repositório original
        |
        v
      Fork
        |
        v
      Clone
        |
        v
Criar uma branch
        |
        v
Editar arquivos
        |
        v
Commit + Push
        |
        v
Pull Request
        |
        v
Revisão e possível integração
```

O Pull Request não garante que as alterações serão aceitas. Os responsáveis pelo projeto podem solicitar ajustes, aprovar ou fechar a proposta.

## 2. Escolha um repositório para praticar

Para este tutorial, escolha um repositório público que aceite contribuições.

Você pode utilizar um projeto de demonstração ou um projeto real cuja documentação permita contribuições.

Antes de começar:

1. Leia o `README.md`.
2. Consulte o arquivo `CONTRIBUTING.md`, caso exista.
3. Verifique as Issues abertas e as orientações para colaboradores.
4. Confira a licença e as regras do projeto.
5. Escolha uma contribuição pequena e útil, como corrigir um erro de digitação ou melhorar uma explicação.

**Boa prática:** antes de iniciar uma mudança significativa, comente na Issue correspondente ou converse com os mantenedores para verificar se a proposta faz sentido.

## 3. Crie um fork

Na página do repositório escolhido:

1. Clique em **Fork**, na parte superior direita.
2. Selecione sua conta como destino.
3. Mantenha o nome sugerido ou escolha outro, se necessário.
4. Clique em **Create fork**.

Após a criação, você terá uma cópia do projeto na sua conta.

Por exemplo, se o original for:

```text
github.com/comunidade/projeto
```

O fork poderá ser:

```text
github.com/seu-usuario/projeto
```

Os nomes são ilustrativos; substitua-os pelos dados reais do projeto.

## 4. Clone seu fork para o computador

Abra a página do seu fork, clique em **Code**, selecione a opção HTTPS e copie a URL.

No terminal, execute:

```bash
git clone https://github.com/SEU-USUARIO/REPOSITORIO.git
```

Entre no diretório criado:

```bash
cd REPOSITORIO
```

Para conferir a situação do repositório:

```bash
git status
```

O comando `git clone` baixa o histórico e os arquivos do repositório para o computador. Já o `git status` mostra a situação atual da sua cópia local.

## 5. Configure o repositório original como upstream

Após clonar seu fork, o Git normalmente configura um remoto chamado `origin`, que aponta para o fork.

Para também acompanhar o repositório original, adicione um segundo remoto chamado `upstream`.

```bash
git remote add upstream https://github.com/PROPRIETARIO-ORIGINAL/REPOSITORIO.git
```

Substitua a URL pelo endereço HTTPS do repositório original.

Confira os remotos configurados:

```bash
git remote -v
```

A saída será semelhante a:

```text
origin    https://github.com/SEU-USUARIO/REPOSITORIO.git (fetch)
origin    https://github.com/SEU-USUARIO/REPOSITORIO.git (push)
upstream  https://github.com/PROPRIETARIO-ORIGINAL/REPOSITORIO.git (fetch)
upstream  https://github.com/PROPRIETARIO-ORIGINAL/REPOSITORIO.git (push)
```

### Qual é a função de cada remoto?

- `origin`: aponta para o seu fork. É para ele que você enviará sua branch.
- `upstream`: aponta para o repositório original. É usado para buscar atualizações do projeto.

Esses nomes são convenções comuns; eles identificam remotos configurados no seu ambiente Git.

## 6. Atualize sua branch principal e crie uma branch de trabalho

Antes de começar uma contribuição, é uma boa prática buscar as atualizações do repositório original.

```bash
git fetch upstream
```

Se a branch principal do projeto se chama `main`, atualize sua branch local:

```bash
git switch main
git merge upstream/main
```

> **Atenção:** esses comandos pressupõem que a branch principal se chama `main` e que você não tem alterações locais pendentes. Se houver mudanças não commitadas, verifique e preserve seu trabalho antes de atualizar.

Agora crie uma branch específica para sua contribuição:

```bash
git switch -c docs/corrige-documentacao
```

Use um nome que descreva a mudança. Exemplos:

- `docs/corrige-readme`
- `fix/corrige-link-quebrado`
- `feat/adiciona-exemplo`

Evite fazer suas alterações diretamente na branch `main`. Uma branch separada facilita a revisão e mantém o trabalho organizado.

## 7. Faça as alterações e revise o resultado

Edite os arquivos necessários utilizando seu editor de código.

Depois, confira o estado do repositório:

```bash
git status
```

Para visualizar as diferenças dos arquivos modificados:

```bash
git diff
```

Se você estiver corrigindo um erro de documentação, por exemplo, confira se:

- A informação está correta.
- Os comandos podem ser reproduzidos.
- Os links funcionam.
- A formatação Markdown está consistente.
- A alteração respeita as orientações do projeto.

## 8. Registre suas alterações com um commit

Adicione ao staging apenas os arquivos que fazem parte da sua contribuição.

Para adicionar um arquivo específico:

```bash
git add caminho/do/arquivo.md
```

Confira o que será incluído:

```bash
git diff --staged
```

Crie o commit:

```bash
git commit -m "docs: corrige exemplo no README"
```

A mensagem é apenas um exemplo. Adapte-a ao conteúdo real da sua alteração.

Um bom commit descreve a mudança de maneira clara e objetiva.

## 9. Envie sua branch para o fork

Envie sua branch para o remoto `origin`:

```bash
git push -u origin docs/corrige-documentacao
```

A opção `-u` configura a associação entre a branch local e a branch remota, facilitando os próximos comandos `git push` e `git pull`.

Após o envio, abra seu fork no GitHub e confira se a branch e o commit aparecem corretamente.

## 10. Abra um Pull Request

Com a branch enviada, você pode propor a integração das suas alterações ao projeto original.

1. Acesse seu fork no GitHub.
2. Abra a opção **Contribute** ou **Pull requests**, conforme a interface disponível.
3. Inicie a criação de um Pull Request.
4. Confira o repositório de destino (*base repository*) e a branch de destino (*base branch*).
5. Confira seu fork como origem (*head repository*) e sua branch como origem das alterações (*compare branch*).
6. Revise a lista de arquivos e o diff.
7. Escreva um título claro e uma descrição explicando o que mudou e por quê.
8. Clique em **Create pull request**.

Exemplo de título:

```text
docs: corrige exemplo de instalação no README
```

Exemplo de descrição:

```markdown
## Objetivo
Corrigir o exemplo de instalação apresentado na documentação.

## Alterações
- Atualização do comando de instalação.
- Revisão da explicação correspondente.

## Validação
- Comando conferido conforme as instruções do projeto.
- Links e formatação revisados.
```

Adapte a descrição à sua contribuição real. Não declare testes realizados que você não executou.

### O que acontece depois?

Os responsáveis pelo projeto podem:

- Revisar e aprovar a mudança.
- Solicitar alterações.
- Deixar comentários ou perguntas.
- Integrar o Pull Request.
- Fechar a proposta sem integrá-la.

Se forem solicitados ajustes, faça as mudanças na mesma branch e envie novos commits. Eles serão incluídos no Pull Request aberto, desde que a branch de origem continue sendo a mesma.

## 11. Mantenha seu fork atualizado

Enquanto você trabalha, o repositório original pode receber novos commits. Para buscar essas atualizações:

```bash
git fetch upstream
```

Para atualizar sua branch principal local:

```bash
git switch main
git merge upstream/main
```

Se for necessário atualizar a branch principal do seu fork no GitHub, envie as alterações para `origin`:

```bash
git push origin main
```

**Importante:** antes de atualizar ou integrar branches, confira se existem alterações locais ou commits próprios que precisam ser preservados. Em projetos com regras específicas de sincronização, siga as instruções dos mantenedores.

## 12. Problemas comuns

### `remote upstream already exists`

O remoto `upstream` já está configurado. Confira os remotos:

```bash
git remote -v
```

Se a URL estiver correta, não é necessário adicioná-lo novamente.

### `Repository not found`

Confira a URL utilizada, o nome do proprietário e o nome do repositório. Se o projeto for privado, verifique também se sua conta possui acesso.

### `Permission denied` ou falha ao fazer push

Verifique se você está enviando a branch para seu próprio fork, se a autenticação está configurada e se a URL do remoto `origin` está correta.

### O Pull Request mostra alterações que não deveriam estar ali

Confira a branch de origem, a branch de destino e o diff do Pull Request. Uma branch criada a partir de outra branch com alterações alheias pode levar commits extras para a proposta.

### Surgiram conflitos

Busque as atualizações do repositório original e avalie a forma correta de integrá-las à sua branch. Resolva os conflitos com cuidado e teste o resultado antes de enviar novas alterações.

## ✅ Checklist final

- [ ] Li as orientações do projeto.
- [ ] Criei um fork do repositório original.
- [ ] Clonei meu fork para o computador.
- [ ] Configurei e verifiquei o remoto `upstream`.
- [ ] Criei uma branch para minha contribuição.
- [ ] Revisei as alterações antes de fazer o commit.
- [ ] Enviei a branch para `origin`.
- [ ] Conferi o destino e o diff do Pull Request.
- [ ] Descrevi as alterações com clareza.

## 📚 Referências oficiais

- [GitHub Docs — Sobre forks](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks)
- [GitHub Docs — Criar um fork de um repositório](https://docs.github.com/en/pull-requests/how-tos/work-with-forks/fork-a-repo)
- [GitHub Docs — Configurar um remoto para um fork](https://docs.github.com/en/pull-requests/how-tos/work-with-forks/configuring-a-remote-repository-for-a-fork)
- [GitHub Docs — Criar um Pull Request a partir de um fork](https://docs.github.com/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request-from-a-fork)
- [GitHub Docs — Sincronizar um fork](https://docs.github.com/en/pull-requests/how-tos/work-with-forks/syncing-a-fork)

---

**Próximo passo:** no Guia 03, vamos aplicar conceitos de branches, commits e Pull Requests em um fluxo de trabalho de equipe com GitHub Flow.
