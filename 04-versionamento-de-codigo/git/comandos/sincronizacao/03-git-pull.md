# Baixando e Integrando Código Remoto (`git pull`)

---

## 💡 Analogia: Buscando a Carta e Lendo Junto com o seu Trabalho

Diferente do `fetch` (que só olha), o `git pull` é o ato de ir à agência, **pegar a carta, trazer para dentro de casa e colar o conteúdo dela no meio dos seus cadernos**. 

Ele faz duas coisas em uma cajadada só: baixa as atualizações (`git fetch`) e tenta juntar (*merge*) com o que você está fazendo no momento.

---

## 📌 O que é o `git pull`?

É o comando mais usado no dia a dia para sincronizar o seu trabalho com o dos seus colegas. Ele garante que você tenha a versão mais recente do projeto antes de continuar programando.

<img width="580" height="188" alt="image" src="https://github.com/user-attachments/assets/0a225a1a-c79a-4995-92e9-715919816ecc" />

---

## 🛠️ Principais Comandos e Estratégias


### 1. `git pull` (Padrão)
* **O que faz:** Baixa as alterações do remoto e cria um **commit de merge** automático caso haja divergências no histórico. Isso pode deixar o histórico cheio de bifurcações ("linhas cruzadas").
* **Exemplo:**
  ```bash
  git pull
  ```
* **Saída esperada:**
  ```text
  remote: Enumerating objects: 4, done.
  remote: Counting objects: 100% (4/4), done.
  remote: Compressing objects: 100% (2/2), done.
  Unpacking objects: 100% (2/2), 650 bytes | 650.00 KiB/s, done.
  From https://github.com/usuario/seu-repositorio
     f5g6h7i..j8k9l0m  main       -> origin/main
  Merge made by the 'ort' strategy.
   README.md | 2 +-
   1 file changed, 1 insertion(+), 1 deletion(-)
  ```

### 2. `git pull --rebase` (Linha do Tempo Limpa)
* **O que faz:** Em vez de criar um commit de merge feio, o `--rebase` pega os seus commits locais, "levanta" eles temporariamente, coloca os commits novos do seu colega por baixo, e depois reaplica os seus commits um por um no topo. O resultado é uma **linha do tempo reta e limpa**, sem nós.
* **Exemplo:**
  ```bash
  git pull --rebase
  ```
* **Saída esperada:**
  ```text
  From https://github.com/usuario/seu-repositorio
     j8k9l0m..m1n2o3p  main       -> origin/main
  First, rewinding head to replay your work on top of it...
  Applying: Adiciona explicacao sobre rebase
  ```
