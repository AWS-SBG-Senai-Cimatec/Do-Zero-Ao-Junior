## 2. 🔀 `git-switch` e `git-checkout` — Transição Moderna e Legada

Utilizado para alternar o seu ambiente de trabalho de uma branch para outra.

### 💻 Lista de Comandos Práticos e Saídas

```bash
# Transição moderna: Muda para a branch especificada
git switch nome-da-branch
```

* **Saída esperada:**
  ```text
  Switched to branch 'nome-da-branch'
  ```

---

```bash
# Cria a branch e faz a transição imediata para ela
git switch -c nome-da-nova-branch
```

* **Saída esperada:**
  ```text
  Switched to a new branch 'nome-da-nova-branch'
  ```

---

```bash
# Forma tradicional/legada de trocar de branch
git checkout nome-da-branch
```

* **Saída esperada:**
  ```text
  Switched to branch 'nome-da-branch'
  ```

---

```bash
# Forma tradicional/legada de criar e entrar em uma nova branch
git checkout -b nome-da-nova-branch
```

* **Saída esperada:**
  ```text
  Switched to a new branch 'nome-da-nova-branch'
  ```

---

> **OBS.:** Recomenda-se utilizar o `git switch`, pois é o comando moderno e focado exclusivamente nessa finalidade.

---

### 🔍 Explicação Palavra a Palavra

* **`switch`**: Significa **alternar** ou **trocar**. É o comando moderno e recomendado para navegação entre branches.
* **`-c`** *(create)*: Cria a branch informada e já alterna a sua sessão de trabalho para dentro dela.
* **`checkout`**: Comando clássico que significa **registrar saída/entrada**. Embora ainda funcione, hoje prefere-se o `switch` por ter foco exclusivo no fluxo de branches.
* **`-b`** *(branch)*: Parâmetro usado exclusivamente no `checkout` antigo para criar uma branch antes de trocar.
