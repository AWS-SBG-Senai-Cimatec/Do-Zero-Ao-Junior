# Guia 04: Criando um Perfil e README de Destaque

> **Objetivo:** transformar o seu perfil do GitHub em um portfólio profissional, capaz de causar boa impressão em recrutadores de tecnologia.

---

## Cenário

Você está se candidatando a um estágio. A pessoa que recruta recebe o seu currículo, procura o seu nome no GitHub e, em poucos segundos, decide se vale a pena olhar mais a fundo. O que ela vê primeiro é o **perfil**.

O GitHub permite exibir um **README especial** no topo do seu perfil. É a sua vitrine: uma página que apresenta quem você é, o que sabe fazer e como falar com você.

---

## Passo a passo

### 1. Criar o repositório especial

1. Clique em **+ → New repository**.
2. No campo **Repository name**, use **exatamente o seu username**. Por exemplo, se o seu usuário é `robson-dev`, o repositório será `robson-dev/robson-dev`.
3. Deixe o repositório como **Public**.
4. Marque a opção **Add a README file** e clique em **Create repository**.

> Quando o nome do repositório é igual ao seu username, o GitHub mostra uma mensagem informando que se trata de um repositório especial. Se ela não aparecer, confira se digitou o nome corretamente.

### 2. Adicionar um README.md público

O arquivo `README.md` desse repositório passa a ser exibido automaticamente na página do seu perfil. Edite-o pelo ícone de lápis ou clone o repositório e edite no seu editor.

```bash
git clone https://github.com/seu-usuario/seu-usuario.git
cd seu-usuario
```

### 3. Incluir as seções essenciais

| Seção | O que colocar |
| --- | --- |
| **Apresentação pessoal** | Nome, curso ou área, cidade e uma frase sobre o que você busca |
| **Tecnologias em foco** | Apenas o que você estuda ou usa de fato (linguagens, frameworks, ferramentas) |
| **Projetos** | 3 a 5 projetos com **link** e **impacto real**: o problema que resolvem e o que você aprendeu |
| **Estatísticas dinâmicas** | Cards que mostram atividade ou linguagens mais usadas (opcional) |
| **Contato** | LinkedIn, e-mail e, se quiser, um site pessoal |

### 4. O que evitar

- **Poluição visual:** excesso de GIFs, cores, animações e emojis que atrapalham a leitura.
- **Badges de tecnologias que você nunca usou:** isso se desfaz na primeira pergunta técnica de uma entrevista.
- **Projetos sem explicação:** um link solto, sem contexto, não diz nada ao leitor.
- **Informações pessoais sensíveis:** endereço, telefone pessoal e dados que você não gostaria de ver públicos.

> **Dica:** peça a um colega que abra o seu perfil e diga, em 10 segundos, o que entendeu sobre você. Se ele não conseguir, o README precisa ficar mais direto.

---

## Exemplo prático

Um modelo enxuto, para você adaptar:

````markdown
# Olá, eu sou o Robson 

Estudante de Engenharia de Software no SENAI CIMATEC, em busca de estágio em desenvolvimento back-end.

## 🛠️ Tecnologias em foco

![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white)
![Git](https://img.shields.io/badge/-Git-F05032?logo=git&logoColor=white)
![AWS](https://img.shields.io/badge/-AWS-232F3E?logo=amazonaws&logoColor=white)

## 🚀 Projetos

- **[controle-de-gastos](https://github.com/robson-dev/controle-de-gastos):** API em Python que ajudou minha turma a organizar as despesas do evento do curso.
- **[trilha-do-zero-ao-junior](https://github.com/robson-dev/trilha):** conteúdos sobre Git e GitHub produzidos em equipe no AWS Student Builder Group.

## 📊 Estatísticas

![Estatísticas do GitHub](https://github-readme-stats.vercel.app/api?username=robson-dev&show_icons=true)

## 📫 Contato

- [LinkedIn](https://www.linkedin.com/in/seu-perfil)
- seu.email@exemplo.com
````

Depois de salvar, abra `github.com/seu-usuario` e confira como o perfil ficou, inclusive no celular.

---

## Referências

- [GitHub Docs: Gerenciando o README do seu perfil](https://docs.github.com/pt/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme)
- [GitHub Docs: Sobre o seu perfil](https://docs.github.com/pt/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/about-your-profile)
- [GitHub Readme Stats](https://github.com/anuraghazra/github-readme-stats)
