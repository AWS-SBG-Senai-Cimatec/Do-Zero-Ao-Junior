# 🤝 Guia de Contribuição — Trilha Do Zero ao Júnior

Agradecemos imensamente pelo seu interesse em contribuir com a **Trilha Do Zero ao Júnior**! Este projeto é construído a muitas mãos pelo time de **Conteúdo e Serviços do AWS Student Builder Group SENAI CIMATEC** e por toda a comunidade de tecnologia.

Seja você um membro do time interno ou um colaborador externo da comunidade, este guia ajudará a manter a qualidade, padronização e relevância de todos os materiais.

---

## 📌 Sumário

- [🤝 Guia de Contribuição — Trilha Do Zero ao Júnior](#-guia-de-contribuição--trilha-do-zero-ao-júnior)
  - [📌 Sumário](#-sumário)
  - [💡 Visão Geral e Formas de Contribuir](#-visão-geral-e-formas-de-contribuir)
  - [👥 Fluxo para o Time Interno (Sprints)](#-fluxo-para-o-time-interno-sprints)
  - [🌍 Fluxo para a Comunidade Externa](#-fluxo-para-a-comunidade-externa)
  - [🛠️ Padrões de Desenvolvimento e Git](#️-padrões-de-desenvolvimento-e-git)
    - [Nomenclatura de Branches](#nomenclatura-de-branches)
    - [Padrão de Commits (Conventional Commits)](#padrão-de-commits-conventional-commits)
  - [✍️ Diretrizes de Conteúdo e Escrita](#️-diretrizes-de-conteúdo-e-escrita)
  - [📂 Como Organizar Arquivos e Assets](#-como-organizar-arquivos-e-assets)
  - [🏆 Reconhecimento de Colaboradores](#-reconhecimento-de-colaboradores)
  - [📜 Código de Conduta](#-código-de-conduta)

---

## 💡 Visão Geral e Formas de Contribuir

Você pode contribuir de diversas maneiras:
* 📝 **Melhorando documentações existentes**: Correções ortográficas, clareza de explicações e formatação.
* 💡 **Adicionando novos conteúdos ou exemplos práticos**: Pequenos trechos de código explicados, analogias didáticas e exercícios propostos.
* 🎨 **Criando recursos visuais**: Diagramas de fluxo, infográficos e esquemas de arquitetura salvos na pasta `assets/`.
* 🐛 **Reportando inconsistências**: Encontrou um link quebrado ou uma informação desatualizada? Abra uma issue!
* 💬 **Participando no Discord**: Ajudando iniciantes a tirar dúvidas sobre os exercícios e conteúdos propostos.

---

## 👥 Fluxo para o Time Interno (Sprints)

Os integrantes do **AWS Student Builder Group** seguem o fluxo de sprints gerenciado no **GitHub Projects**:

1. **Atribuição**: O integrante assume a Issue correspondente ao tópico da sprint (utilizando o template `estudo-do-time.md`).
2. **Ciclo de Estudo**: Durante a semana, estuda o tópico a fundo através de fontes confiáveis e documentações oficiais.
3. **Desenvolvimento do Material**: Produz o conteúdo no diretório correspondente (ex: `01-fundamentos/`) mantendo a linguagem didática e acessível.
4. **Pull Request & Review**: Cria o PR apontando para a branch `main`. O PR deve ser revisado por pelo menos outro membro do time antes do merge.
5. **Conclusão**: Após aprovado e mesclado, a Issue no GitHub Projects é movida para *Done*.

---

## 🌍 Fluxo para a Comunidade Externa

Colaboradores externos são super bem-vindos! Para submeter sua contribuição:

1. **Fork do Repositório**: Faça um fork do projeto para a sua conta no GitHub.
2. **Clone Local**:
   ```bash
   git clone https://github.com/SEU-USUARIO/do-zero-ao-junior.git
   cd do-zero-ao-junior
   ```
3. **Crie uma Branch**:
   ```bash
   git switch -c feat/01-exercicios-condicionais
   ```
4. **Faça as Alterações**: Edite ou crie os arquivos necessários seguindo as diretrizes de escrita.
5. **Commit e Push**:
   ```bash
   git add .
   git commit -m "docs(01-fundamentos): adiciona exercicios de estruturas condicionais"
   git push origin feat/01-exercicios-condicionais
   ```
6. **Abra um Pull Request**: No GitHub, abra um PR apontando para o repositório principal. Descreva detalhadamente o que foi feito usando o nosso template de PR.

---

## 🛠️ Padrões de Desenvolvimento e Git

### Nomenclatura de Branches

Procure nomear branches com prefixos descritivos em minúsculas:

- `feat/modulo-nome-do-recurso` (para novos conteúdos, capítulos ou exercícios)
- `fix/modulo-correcao` (para correções de código, erros conceituais ou digitação)
- `docs/modulo-atualizacao` (para melhorias puramente textuais ou de formatação)
- `refactor/modulo-reorganizacao` (para reestruturação de textos ou pastas)

*Exemplos:* `feat/03-queries-join`, `fix/06-diagrama-dns-link`, `docs/readme-atualiza-cronograma`.

### Padrão de Commits (Conventional Commits)

Utilizamos o padrão do [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/):

- `feat:` Nova funcionalidade, novo tópico ou novo exercício.
- `fix:` Correção de bug em código, erro conceitual ou correção ortográfica.
- `docs:` Alterações em documentações, READMEs ou guias.
- `style:` Ajustes puramente de formatação (espaçamento, markdown lint) sem alteração de sentido.
- `chore:` Tarefas de manutenção do repositório, configuração ou organização interna.

*Exemplos:*
```bash
git commit -m "feat(01-fundamentos): cria secao sobre arrays e lacos de repeticao"
git commit -m "fix(08-apis): corrige exemplo de requisicao POST com json"
git commit -m "docs: atualiza guia de contribuicao com novas instrucoes"
```

---

## ✍️ Diretrizes de Conteúdo e Escrita

Para que o projeto atinja seu público (pessoas que estão começando do zero), respeite os seguintes princípios:

1. **Didática Acessível**: Evite jargões sem explicação prévia. Ao citar termos em inglês (ex: *payload*, *runtime*, *scope*), explique o que significam na prática.
2. **Exemplos do Mundo Real**: Prefira analogias simples e exemplos contextualizados em vez de exemplos puramente abstratos (`foo`, `bar`).
3. **Código Limpo e Comentado**: Todo trecho de código deve ser autoexplicativo, bem formatado e com comentários guiando cada linha importante.
4. **Markdown Válido**: Utilize títulos hierárquicos corretos (`#`, `##`, `###`), listas, tabelas e blocos de código com a sintaxe destacada (ex: ````markdown ```javascript ... ``` ````).
5. **Citação de Fontes**: Sempre cite documentações oficiais, livros ou artigos de referência confiáveis ao final do módulo.

---

## 📂 Como Organizar Arquivos e Assets

- **Textos e Documentações**: Ficam sempre dentro da pasta do respectivo módulo (ex: `01-fundamentos/README.md`).
- **Imagens e Diagramas**:
  - Salve imagens em formato `.png`, `.jpg` ou `.svg` na pasta `assets/<modulo>/` correspondente.
  - *Exemplo de caminho*: `assets/01-fundamentos/diagrama-fluxo-condicional.png`.
  - Faça referência no Markdown utilizando caminhos relativos:
    ```markdown
    ![Fluxograma de Decisão](../assets/01-fundamentos/diagrama-fluxo-condicional.png)
    ```

---

## 🏆 Reconhecimento de Colaboradores

A colaboração com a comunidade é um pilar genuíno do projeto:
- Todo colaborador terá seu nome reconhecido publicamente no repositório.
- Contribuições consistentes e de alto impacto poderão resultar em convites formais para atuar junto à diretoria do **AWS Student Builder Group SENAI CIMATEC**.

---

## 📜 Código de Conduta

Esperamos um ambiente acolhedor, respeitoso e inclusivo para todos os participantes, independentemente do nível de experiência, identidade de gênero, raça, orientação sexual ou formação. Dúvidas devem ser acolhidas com empatia e paciência.
