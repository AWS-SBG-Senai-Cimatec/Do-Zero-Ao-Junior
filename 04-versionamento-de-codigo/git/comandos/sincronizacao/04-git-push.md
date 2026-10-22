# Publicando Commits (`git push`)

---

## 💡 Analogia: Enviando a Sua Carta para o Mundo

Agora é o inverso. Você escreveu cartas incríveis na sua mesa (fez commits locais) e quer que o mundo inteiro veja. O `git push` é o momento em que você coloca essas cartas no malote e **envia para a agência central na nuvem** (GitHub), para que sua equipe possa ler.

---

## 📌 O que é o `git push`?

É o comando responsável por enviar o histórico dos seus commits locais para o repositório remoto.

<img width="534" height="272" alt="image" src="https://github.com/user-attachments/assets/6c9a26df-a680-4223-8b40-347a4aad6887" />

---

## 🛠️ Principais Comandos, Opções e Cuidados

### 1. `git push -u origin <branch>`
* **O que faz:** Envia a sua branch atual para o remoto e o parâmetro `-u` (upstream) faz uma **amarração permanente**. A partir desse comando, nas próximas vezes que você quiser enviar ou receber atualizações nessa branch, basta digitar apenas `git push` ou `git pull` sem precisar especificar o nome da branch de novo.
* **Exemplo:**
  ```bash
  git push -u origin minha-feature
  ```
* **Saída esperada:**
  ```
  Enumerating objects: 5, done.
  Counting objects: 100% (5/5), done.
  Compressing objects: 100% (3/3), done.
  Writing objects: 100% (3/3), 340 bytes | 340.00 KiB/s, done.
  Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
  remote: 
  remote: Create a pull request for 'minha-feature' on GitHub by visiting:
  remote:      https://github.com/usuario/seu-repositorio/pull/new/minha-feature
  remote:
  To https://github.com/usuario/seu-repositorio.git
   * [new branch]      minha-feature -> minha-feature
  Branch 'minha-feature' set up to track remote branch 'minha-feature' from 'origin'.
  ```

### 2. `git push origin --delete <branch>`
* **O que faz:** Apaga uma branch lá no repositório remoto (na nuvem). Útil quando você já terminou uma tarefa, o código foi aprovado e integrado, e você quer faxinar o GitHub.
* **Exemplo:**
  ```bash
  git push origin --delete branch-antiga
  ```
* **Saída esperada:**
  ```
  To https://github.com/usuario/seu-repositorio.git
   - [deleted]         branch-antiga
  ```

### 3. `git push --force-with-lease` (O Super Poder Seguro)
* **O que faz:** Às vezes você reescreve o histórico local (com um `amend` ou `rebase`), e o GitHub rejeita o seu `push` porque a linha do tempo diverge. O comando `--force` normal apagaria o trabalho de outros colegas sem dó. Já o `--force-with-lease` é a versão **inteligente e segura**: ele só sobrescreve o remoto se **ninguém mais mexeu** na branch enquanto você estava trabalhando nela.
* **Exemplo:**
  ```bash
  git push --force-with-lease origin minha-branch
  ```
* **Saída esperada:**
  ```
  To https://github.com/usuario/seu-repositorio.git
     a1b2c3d..e4f5g6h  minha-branch -> minha-branch
  ```
