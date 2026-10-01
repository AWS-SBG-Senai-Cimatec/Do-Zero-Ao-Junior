# 🌿 Módulo 04: Versionamento de Código com Git

> **Trilha Do Zero ao Júnior — AWS Student Builder Group SENAI CIMATEC**

No desenvolvimento de software profissional, programar sem um sistema de controle de versão é impensável. O **Git** é a ferramenta padrão de mercado para registrar o histórico de evolução do código, permitir trabalho simultâneo e recuperar versões anteriores sem o risco de perder trabalho.

---

## 🎯 Objetivos de Aprendizagem

Ao final deste módulo, você será capaz de:
- Compreender o que é um **Sistema de Controle de Versões Distribuído (DVCS)**.
- Entender os três estados fundamentais do Git: **Working Directory**, **Staging Area (Index)** e **Repository (Commit History)**.
- Configurar sua identidade local (`user.name`, `user.email`).
- Inicializar repositórios, rastrear arquivos, criar commits significativos e verificar o histórico.
- Trabalhar com **ramificações (branches)** para isolar novas funcionalidades ou correções.
- Realizar **merges** e resolver conflitos de código com segurança.
- Utilizar comandos utilitários como `git diff`, `git stash` e `git checkout` / `git switch`.

---

## 🗺️ Ementa Detalhada do Módulo

1. **Fundamentos do Git**
   - Por que pastas com nomes tipo `projeto_final_v2_agora_vai.zip` são um problema.
   - Como o Git armazena dados: snapshots de arquivos através de hashes criptográficos (SHA-1).
   - Configuração inicial:
     ```bash
     git config --global user.name "Seu Nome"
     git config --global user.email "seu.email@exemplo.com"
     ```

2. **O Ciclo de Vida dos Arquivos**
   - Não rastreado (*Untracked*) -> Modificado (*Modified*) -> Preparado (*Staged*) -> Comitado (*Committed*).
   - Comandos fundamentais:
     - `git init`: Inicia um novo repositório local.
     - `git status`: Exibe o estado atual dos arquivos na árvore de trabalho.
     - `git add <arquivo>` ou `git add .`: Adiciona arquivos à Staging Area.
     - `git commit -m "mensagem"`: Registra a fotografia (*snapshot*) das alterações com mensagem explicativa.
     - `git log` / `git log --oneline --graph`: Inspeciona o histórico de commits.

3. **O Arquivo `.gitignore`**
   - Por que ignorar arquivos temporários, senhas, dependências pesadas (`node_modules/`, `venv/`, `.env`, builds).
   - Sintaxe e regras de padrões do `.gitignore`.

4. **Trabalhando com Branches (Ramificações)**
   - O que é uma branch: um ponteiro móvel para um commit específico.
   - Criando e alternando branches:
     ```bash
     git branch feat/minha-feature       # cria nova branch
     git switch feat/minha-feature       # alterna para a branch
     # Ou atalho moderno:
     git switch -c feat/minha-feature    # cria e alterna
     ```
   - Boas práticas: manter a branch principal (`main`) sempre estável e desenvolver novidades em branches isoladas.

5. **Fusão de Branches (Merge) e Resolução de Conflitos**
   - Fusão Fast-Forward vs. 3-way merge.
   - O que é um conflito de merge e quando ele ocorre (duas alterações concorrentes nas mesmas linhas).
   - Como inspecionar marcadores de conflito (`<<<<<<<`, `=======`, `>>>>>>>`) e resolvê-los no editor.

6. **Comandos Avançados e Utilitários Úteis**
   - `git diff`: Compara diferenças entre arquivos modificados e o último commit.
   - `git stash` e `git stash pop`: Salva temporariamente alterações inacabadas para limpar a árvore de trabalho.
   - Desfazendo alterações locais: `git restore <arquivo>`.

---


## 📚 Conteúdo

| # | Tópico | Descrição |
|---|---|---|
| 1 | [Introdução ao Versionamento](./01-introducao-ao-versionamento/README.md) | O que é versionamento de código, por que ele existe e o panorama Git vs GitHub |
| 2 | [Git — Fundamentos Locais](./02-git-fundamentos-locais/README.md) | Instalação, `git init`, estados dos arquivos, `add`, `commit`, `status`, `log` |
| 3 | [Branches e Merge](./03-branches-e-merge/README.md) | Criando branches, mesclando alterações e resolvendo conflitos |
| 4 | [.gitignore e Boas Práticas de Commit](./04-gitignore-e-boas-praticas-de-commit/README.md) | O que não versionar e como escrever bons commits |
| 5 | [Repositórios Remotos e GitHub](./05-repositorios-remotos-e-github/README.md) | `remote`, `clone`, `push`, `pull` e o papel do GitHub |
| 6 | [Fork, Pull Request e Code Review](./06-fork-pull-request-e-code-review/README.md) | Colaborando em projetos através de fork, PR e revisão de código |

## 🗺️ Como estudar este tópico

A ordem da tabela acima é a ordem recomendada de leitura — os conceitos são construídos de forma incremental, do uso local do Git até a colaboração em repositórios remotos.

---

⬅️ [Voltar para o roadmap completo](../README.md)

---

## 📚 Materiais e Leituras Recomendadas

- 🌐**Recomendações do AWS SBG**: [Materiais Recomendados)](https://awssbgcimateclanding.vercel.app/) — Principais materiais de estudo e conteúdos da AWS SBG SENAI CIMATEC. 
- 📖 **Livro Gratuito**: [Pro Git Book (Scott Chacon e Ben Straub)](https://git-scm.com/book/pt-br/v2) — A "bíblia" oficial do Git em português.
- 🌐 **Interativo**: [Learn Git Branching](https://learngitbranching.js.org/?locale=pt_BR) — O melhor jogo visual interativo para aprender branches e merges.
- 🌐 **Guia Rápido**: [Git - Guia Prático (Roger Dudler)](https://rogerdudler.github.io/git-guide/index.pt_BR.html)

---

[⬅️ Voltar para o Roadmap Principal](../README.md)
