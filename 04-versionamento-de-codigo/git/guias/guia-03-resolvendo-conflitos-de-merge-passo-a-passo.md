# ⚡ Guia Prático 03: Desmistificando e Resolvendo Conflitos de Merge

Se você desenvolve software há algum tempo, provavelmente já passou por isso ou ouviu histórias assustadoras sobre o famoso **"Merge Conflict"** (Conflito de Mesclagem).

Mas aqui vai um segredo logo de início: **conflitos de merge não são erros nem bugs no Git**. Eles são apenas a forma como o Git diz: 

> *"Ei! Duas pessoas alteraram a mesma linha do mesmo arquivo de formas diferentes. Eu não sei qual das duas opções é a correta, então preciso que você, humano, decida qual mantemos!"*

Neste guia, vamos perder o medo do conflito criando uma simulação controlada do zero, entendendo os marcadores de conflito e resolvendo tudo com total segurança.

---

## 🎬 O Cenário

Você e uma pessoa da sua equipe alteraram a mesma linha do arquivo `config.txt` em branches diferentes. Quando você tenta unir essas duas versões na branch `main`, o Git interrompe o processo e pede a sua intervenção.

---

## 🗺️ Passo a Passo do Roteiro

### 1️⃣ Criando a Simulação do Conflito do Zero

Vamos preparar o terreno criando um repositório temporário ou uma nova pasta de teste para simular o cenário de conflito perfeitamente.

```bash
# 1. Cria um arquivo base na branch main
echo "Servidor: localhost" > config.txt
git add config.txt
git commit -m "chore: cria arquivo de configuracao base"

# 2. Cria a branch A e altera o servidor para 'servidor-staging'
git switch -c feat/servidor-staging
echo "Servidor: staging.meudominio.com" > config.txt
git add config.txt
git commit -m "feat: altera servidor para ambiente de staging"

# 3. Voltar para a main e criar a branch B alterando a mesma linha para 'servidor-prod'
git switch main
git switch -c feat/servidor-prod
echo "Servidor: prod.meudominio.com" > config.txt
git add config.txt
git commit -m "feat: altera servidor para ambiente de producao"
```

Agora temos duas branches (`feat/servidor-staging` e `feat/servidor-prod`) com alterações conflitantes na mesma linha!

---

### 2️⃣ Disparando o Conflito (`git merge`)

Agora vamos tentar integrar a branch `feat/servidor-staging` dentro de `feat/servidor-prod`:

```bash
# Estando na branch feat/servidor-prod
git merge feat/servidor-staging
```

O Git exibirá um aviso chamativo no terminal:

```text
AUTO-MERGING config.txt
CONFLICT (content): Merge conflict in config.txt
Automatic merge failed; fix conflicts and then commit the result.
```

**Mantenha a calma!** O processo de merge ficou "pausado" aguardando você resolver a diferença.

---

### 3️⃣ Entendendo os Marcadores de Conflito

Ao abrir o arquivo `config.txt` no seu editor de código (VS Code, Vim, Nano, etc.), você verá algo assim:

```text
<<<<<<< HEAD
Servidor: prod.meudominio.com
=======
Servidor: staging.meudominio.com
>>>>>>> feat/servidor-staging
```

Vamos decodificar o que esses símbolos significam:

* **`<<<<<<< HEAD`**: Início do bloco com as alterações da **sua branch atual** (onde você está posicionado).
* **`=======`**: A linha divisória central. O que está acima é o código da sua branch; o que está abaixo vem da branch que está sendo mesclada.
* **`>>>>>>> feat/servidor-staging`**: Fim do bloco com as alterações da **branch que você está tentando trazer**.

---

## 🧠 Hora de Praticar! (Desafio de Fixação)

Vamos testar sua leitura dos marcadores de conflito!

**Cenário:** Você se depara com o seguinte trecho em um arquivo `app.js` durante um merge:

```text
<<<<<<< HEAD
const PORT = 3000;
=======
const PORT = 8080;
>>>>>>> feat/porta-api
```

Se o seu objetivo é manter a porta configurada pela branch `feat/porta-api` (8080), como o arquivo deve ficar no final após a sua edição manual?

* \[ \] **Opção A:**
  ```text
  <<<<<<< HEAD
  =======
  const PORT = 8080;
  >>>>>>> feat/porta-api
  ```
* \[ \] **Opção B:**
  ```text
  const PORT = 3000;
  const PORT = 8080;
  ```
* \[ \] **Opção C:**
  ```text
  const PORT = 8080;
  ```

---

### 🔍 Resposta Correta:

**Resposta: Opção C!**

Para resolver um conflito, você deve apagar **todos os marcadores** (`<<<<<<<`, `=======`, `>>>>>>>`) e deixar **apenas o código final correto** que deve permanecer no arquivo.

---

### 4️⃣ Resolvendo o Conflito Manualmente

No nosso exemplo do `config.txt`, digamos que decidimos que o endereço correto para esse ambiente é o de produção, mas queremos manter um comentário explicativo.

No seu editor, altere o arquivo para remover todos os marcadores e deixar apenas o resultado final desejado:

```text
# Servidor configurado para o ambiente principal
Servidor: prod.meudominio.com
```

Salve e feche o arquivo.

---

### 5️⃣ Concluindo o Merge Commit (`git add` e `git commit`)

Agora que o arquivo foi corrigido e salvo, informe ao Git que o conflito foi resolvido:

```bash
# 1. Adiciona o arquivo resolvido ao Stage
git add config.txt

# 2. Inspecione o status (opcional, mas recomendado)
git status
```

Você verá que o Git reconheceu a resolução do conflito. Para finalizar o merge, execute apenas `git commit` sem a flag `-m` (ou com `-m` se quiser personalizar a mensagem):

```bash
git commit -m "fix: resolve conflito de configuracao do servidor"
```

Pronto! O merge commit foi realizado com sucesso e o histórico está unificado.

---

> 🚨 **Botão de Emergência:** Se durante um merge você se sentir perdido(a) e quiser cancelar todo o processo para voltar ao estado original antes de tentar mesclar, basta rodar:
> ```bash
> git merge --abort
> ```

---

## 🎯 Checklist de Resolução de Conflito

* \[x\] Identificou o arquivo em conflito pelo aviso do `git status`
* \[x\] Abriu o arquivo e localizou os marcadores `<<<<<<<`, `=======` e `>>>>>>>`
* \[x\] Decidiu qual versão (ou combinação) deve permanecer
* \[x\] Removeu todos os marcadores de conflito do arquivo e salvou
* \[x\] Adicionou o arquivo ao stage com `git add`
* \[x\] Finalizou o processo criando o commit com `git commit`

---

## 💬 Reflexão Final

Conflitos de mesclagem são um sinal de que a colaboração está acontecendo! Com a prática, você verá que eles são tarefas rotineiras e simples de resolver. O segredo é sempre ler os marcadores com calma, conversar com sua equipe quando houver dúvida sobre qual código manter e validar o arquivo antes de salvar o commit final. 🚀