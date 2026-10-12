# 01. `🚀 git-init — Inicialização de Repositórios Locais`

## 📖 Visão Geral
O comando `git init` é o ponto de partida de qualquer projeto no Git. Ele transforma uma pasta comum do seu computador em um repositório local rastreado, criando a pasta oculta `.git` onde todo o histórico de [commits](./05-git-commit.md) e [branches](../ramificacao/README.md) será armazenado.

## 📋 Sintaxe Oficial
```bash
git init [-b <nome-da-branch>] [<diretorio>]
```

## 🚩 Tabela de Flags Úteis

| Flag | Descrição | Na Prática |
| :- | :- | :- |
| `-b <nome>` | Define o nome da [branch](../ramificacao/README.md) inicial padrão. | Usado para iniciar diretamente com a branch `main`. |
| `--quiet` / `-q` | Silencia a saída do comando (sem mensagens informativas). | Utilizado em scripts de automação. |

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Inicializa o repositório na pasta atual definindo 'main' como a branch principal
git init -b main

# Cria uma nova pasta 'meu-projeto' e já a inicializa como repositório Git
git init -b main meu-projeto
```

## 💡 Boas Práticas

* ✅ **O que fazer:** Sempre utilize `-b main` para seguir o padrão moderno das empresas em vez do nome legado (`master`).
* ❌ **O que evitar:** Nunca rode `git init` dentro de uma pasta que já é um repositório Git ou na pasta raiz do sistema para evitar perda de dados e lentidão no computador (ex: dentro de `C:\Users\SeuNome`).
---