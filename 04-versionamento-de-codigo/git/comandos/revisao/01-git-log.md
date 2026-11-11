# 📜 git-log — Visualização do Histórico de Commits

## 📖 Visão Geral
O comando `git log` é utilizado para consultar a linha do tempo de alterações salvas no repositório. Ele exibe a lista de [commits](../fluxo-basico/05-git-commit.md) do mais recente para o mais antigo, mostrando o autor, a data e a mensagem explicativa de cada ponto da história.

## 📋 Sintaxe Oficial
```bash
git log [<opcoes>]
```

## 🚩 Tabela de Flags Úteis

| Flag | Descrição | Na Prática |
| :--- | :--- | :--- |
| `--oneline` | Exibe cada [commit](../fluxo-basico/05-git-commit.md) numa única linha resumida com o hash curto. | Ideal para ter uma visão rápida e limpa do histórico. |
| `-n <numero>` | Limita a exibição aos últimos `<numero>` commits. | Para consultar apenas as últimas alterações feitas. |
| `--graph` | Desenha um gráfico em texto exibindo o fluxo e fusões de [branches](../ramificacao/README.md). | Essencial para entender o histórico em equipas com várias branches. |
| `--author="<nome>"` | Filtra a listagem exibindo apenas commits criados por um autor específico. | Para auditar as contribuições de um colega de equipa. |

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Exibe o histórico de forma resumida (uma linha por commit)
git log --oneline

# Exibe os últimos 3 commits realizados no repositório
git log -n 3

# Exibe o histórico em formato gráfico exibindo ramificações
git log --graph --oneline

# Exibe apenas os commits feitos por um autor
git log --author="Joao"
```

## 💡 Boas Práticas

* ✅ **O que fazer:** Utilize `git log --oneline` no dia a dia para economizar espaço no terminal.
* ❌ **O que evitar:** Evite rodar `git log` simples em repositórios grandes sem filtros ou paginação, pois a lista extensa pode dificultar a navegação.
---