# 02. `📥 git-clone — Clonagem de Repositórios Remotos`

## 📖 Visão Geral
O `git clone` é utilizado para baixar uma cópia completa de um repositório remoto para o seu computador. Ele cria a pasta do projeto, baixa o histórico de [commits](./05-git-commit.md) e configura o endereço remoto (*origin*) automaticamente.

## 📋 Sintaxe Oficial
```bash
git clone [opções] <repositório> [<diretório>]
```

## 🚩 Tabela de Flags Úteis

| Flag | Descrição | Na Prática |
| :--- | :--- | :--- |
| `--depth <n>` | Limita o download aos últimos `n` commits (clone raso). | Ideal para baixar repositórios grandes de forma rápida. |
| `--branch <nome>` / `-b` | Clona e faz checkout diretamente na [branch](../ramificacao/README.md) especificada. | Quando precisa de trabalhar direto numa branch específica. |
| `--single-branch` | Baixa apenas o histórico da branch informada, ignorando as demais. | Economiza espaço de armazenamento local. |

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Clona um repositório completo para a sua máquina
git clone <url-do-repositorio>

# Clona baixando apenas o commit mais recente (clone rápido)
git clone --depth 1 <url-do-repositorio>

# Clona alternando diretamente para a branch 'desenvolvimento'
git clone --branch desenvolvimento <url-do-repositorio>
```

## 💡 Boas Práticas

* ✅ **O que fazer:** Verifique sempre se está clonando o seu **fork** pessoal quando for contribuir com repositórios em equipe.
* ❌ **O que evitar:** Evite clonar repositórios dentro de pastas que já estão sendo monitorizadas por outro repositório Git.
---