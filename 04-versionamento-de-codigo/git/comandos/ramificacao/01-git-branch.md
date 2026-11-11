## 1. 📂 `git-branch` — Listando, Criando e Excluindo Branches

Gerencia a criação e a visualização das suas linhas de trabalho paralelas.

### 💻 Lista de Comandos Práticos e Saídas

```
# Lista apenas as branches presentes no seu computador (importante para saber em qual branch está trabalhando)
git branch

```

* **Saída esperada:**

  ```
    main
    develop
  * minha-feature
  
  ```

  *(O asterisco `*` e o texto em destaque indicam a branch em que você está posicionado no momento).*

```
# Lista todas as branches (locais e guardadas na nuvem)
git branch -a

```

* **Saída esperada:**

  ```
    main
    develop
  * minha-feature
    remotes/origin/HEAD -> origin/main
    remotes/origin/main
    remotes/origin/develop
    remotes/origin/minha-feature
  
  ```

```
# Cria uma nova branch com o nome informado
git branch minha-nova-feature

```

* **Saída esperada:**

  *(Sem saída de texto no terminal em caso de sucesso).*

```
# Renomeia a branch em que você está trabalhando no momento
git branch -m novo-nome-da-branch

```

* **Saída esperada:**

  *(Sem saída de texto no terminal em caso de sucesso; o nome da branch atual é atualizado imediatamente).*

```
# Deleta uma branch com segurança (impede se houver código não salvo)
git branch -d nome-da-branch

```

* **Saída esperada:**

  ```
  Deleted branch nome-da-branch (was a1b2c3d).
  
  ```

  *(Caso existam alterações pendentes que ainda não foram mescladas, o Git exibirá um erro bloqueando a exclusão).*

```
# Força a exclusão imediata de uma branch
git branch -D nome-da-branch

```

* **Saída esperada:**

  ```
  Deleted branch nome-da-branch (was a1b2c3d).
  
  ```

### 🔍 Explicação Palavra a Palavra

* **`git`**: Executável da ferramenta que gerencia a versão do projeto.

* **`branch`**: Palavra-chave em inglês para **linha de desenvolvimento** ou **ramificação**.

* **`-a`** *(all)*: Exibe **todas** as branches, incluindo as cópias sincronizadas do GitHub.

* **`-m`** *(move/modify)*: Muta ou move o nome da branch atual para um novo nome.

* **`-d`** *(delete)*: Opção de exclusão **segura**. O Git valida se o conteúdo já foi integrado antes de apagar.

* **`-D`** *(Delete forçado)*: Exclui a branch sem checar pendências. Usado para descartar experimentos com falha.
