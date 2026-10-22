# 02. 📥 git-clone — Clonagem de Repositórios Remotos

## 📖 Visão Geral

O `git clone` é utilizado para baixar uma cópia completa de um repositório remoto para o seu computador. Ele cria a pasta do projeto, baixa o histórico de [commits](./05-git-commit.md) e configura o endereço remoto (*origin*) automaticamente.

---

## 📋 Sintaxe Oficial

```bash
git clone [flags] <repositorio> [<diretorio>]
```

---

## 🚩 Tabela de Flags Úteis

| Flag | Descrição | Na Prática |
| :--- | :--- | :--- |
| `--depth <n>` | Limita o download aos últimos `n` commits (clone raso). | Ideal para baixar repositórios grandes de forma rápida. |
| `--branch <nome>` / `-b` | Clona e faz checkout diretamente na [branch](../ramificacao/README.md) especificada. | Quando precisa trabalhar direto em uma branch específica. |
| `--single-branch` | Baixa apenas o histórico da branch informada, ignorando as demais. | Economiza espaço de armazenamento local. |

---

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Clona um repositório completo para a sua máquina
git clone [https://github.com/usuario/repositorio.git](https://github.com/usuario/repositorio.git)

# Clona baixando apenas o commit mais recente (clone rápido)
git clone --depth 1 [https://github.com/usuario/repositorio.git](https://github.com/usuario/repositorio.git)

# Clona alternando diretamente para a branch 'desenvolvimento'
git clone --branch desenvolvimento [https://github.com/usuario/repositorio.git](https://github.com/usuario/repositorio.git)
```

### 🖥️ Saída Esperada no Terminal

```console
Cloning into 'repositorio'...
remote: Enumerating objects: 42, done.
remote: Counting objects: 100% (42/42), done.
remote: Compressing objects: 100% (30/30), done.
remote: Total 42 (delta 12), reused 38 (delta 8), pack-reused 0
Receiving objects: 100% (42/42), 15.80 KiB | 2.26 MiB/s, done.
Resolving deltas: 100% (12/12), done.
```

> 💡 **O que significa essa saída?**  
> O Git conecta ao servidor remoto, baixa os arquivos e objetos compactados, descompacta tudo no diretório local e seleciona a branch padrão para você começar a trabalhar.

---

## 💡 Boas Práticas

- ✅ **Verificação de Fork:** Verifique sempre se está clonando o seu **fork** pessoal quando for contribuir com repositórios em equipe.
- ❌ **Evite Repositórios Aninhados:** Evite clonar repositórios dentro de pastas que já estão sendo monitoradas por outro repositório Git.
---