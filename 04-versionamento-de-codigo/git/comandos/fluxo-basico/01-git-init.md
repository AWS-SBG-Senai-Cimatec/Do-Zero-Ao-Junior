# 01. 🚀 git-init — Inicialização de Repositórios Locais

## 📖 Visão Geral

O comando `git init` é o ponto de partida de qualquer projeto no Git. Ele transforma uma pasta comum do seu computador em um repositório local rastreado, criando a pasta oculta `.git` onde todo o histórico de [commits](./05-git-commit.md) e [branches](../ramificacao/README.md) será armazenado.

---

## 📋 Sintaxe Oficial

```bash
git init [flags] [<diretorio>]
```

---

## 🚩 Tabela de Flags Úteis

| Flag | Descrição | Na Prática |
| :--- | :--- | :--- |
| `-b <nome>` | Define o nome da [branch](../ramificacao/README.md) inicial padrão. | Usado para iniciar diretamente com a branch `main`. |
| `--quiet` / `-q` | Silencia a saída do comando (sem mensagens informativas). | Utilizado em scripts de automação. |

---

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Inicializa o repositório na pasta atual definindo 'main' como a branch principal
git init -b main

# Cria uma nova pasta 'meu-projeto' e já a inicializa como repositório Git
git init -b main meu-projeto
```

### 🖥️ Saída Esperada no Terminal

```console
Initialized empty Git repository in C:/Users/usuario/projetos/meu-projeto/.git/
```

> 💡 **O que significa essa saída?**  
> O Git confirma que criou com sucesso a pasta oculta `.git`. A partir deste momento, a pasta passa a ser monitorada pelo versionamento.

---

## 💡 Boas Práticas

- ✅ **Padrão de Branch:** Sempre utilize `-b main` para seguir a convenção moderna de mercado em vez do nome antigo (`master`).
- ✅ **Navegação Prévia:** Sempre navegue (`cd`) até o diretório exato do projeto antes de inicializá-lo.

---

> ⚠️ **ATENÇÃO — Execução do `git init` dentro de um repositório existente:**
>
> Executar `git init` na raiz de um projeto que já é um repositório Git apenas **reinicializa** as configurações, sem apagar o histórico de commits.
>
> ❌ **O PROBLEMA: `git init` dentro de uma subpasta**
> Caso execute o comando por engano dentro de uma subpasta do projeto, será criado um repositório aninhado (subrepositório não vinculado), o que impede o repositório principal de rastrear os arquivos corretamente.
>
> ✏️ **Como corrigir:**
> 1. Vá até a subpasta onde executou o comando incorretamente.
> 2. Apague a pasta oculta `.git` criada nessa subpasta:
>    * **Windows (PowerShell):** `Remove-Item -Recurse -Force .git`
>    * **Linux / macOS / Git Bash:** `rm -rf .git`
> 3. Volte à raiz do projeto e verifique o estado com `git status`.
---