# 🚀 Guia Prático 01: Transformando uma Pasta Comum em um Repositório Git

Imagine que você está começando a construir uma casa. Antes de erguer as paredes, você precisa preparar o terreno e organizar a caixa de ferramentas, certo? É exatamente isso que faremos aqui!

Seja muito bem-vindo(a) a este guia prático! Com ele vamos dar o primeiro passo fundamental na vida de qualquer pessoa que escreve código: **transformar uma pasta qualquer do seu computador em um repositório versionado pelo Git**.

Ao final deste guia, sua pasta estará organizada, identificada e com o histórico do seu primeiro commit registrado de forma profissional.

---

## 🎬 O Cenário

Você acabou de criar uma pasta no seu computador para um novo projeto (seja um site, uma API ou até um script de automação). No momento, ela é apenas uma pasta comum do seu sistema operacional. Nosso objetivo é dar "superpoderes" a ela, ativando o rastreamento do Git!

---

## 🗺️ Passo a Passo do Roteiro

### 1️⃣ Navegando até a pasta do projeto

Abra o seu terminal (Bash, Zsh ou PowerShell) e navegue até o diretório onde o seu projeto está instalado.

```bash
cd caminho/para/sua-pasta-do-projeto
```

> 💡 **Dica rápida:** Você pode digitar `cd ` (com um espaço no final) e arrastar a pasta do seu gerenciador de arquivos diretamente para dentro da janela do terminal!

---

### 2️⃣ Inicializando o repositório (`git init`)

Agora vamos oficializar a criação do repositório. Para evitar problemas antigos de nomenclatura de branches padrão (como o antigo `master`), já vamos definir nossa branch principal como **`main`**:

```bash
git init -b main
```

**O que acontece bastidores?**  
O Git cria uma pasta oculta chamada `.git`. É ali que toda a "mágica" de histórico, ramificações e commits vai ficar salva.

---

### 3️⃣ Verificando suas credenciais (`git config`)

Antes de registrar qualquer alteração, o Git precisa saber **quem é você**. Afinal, todo commit leva a assinatura do autor.

Confirme ou configure seu nome e e-mail no escopo deste repositório local:

```bash
# Verificar configurações atuais
git config user.name
git config user.email

# Se precisar definir localmente para este projeto:
git config user.name "Seu Nome"
git config user.email "seu.email@exemplo.com"
```

---

### 4️⃣ Criando os arquivos essenciais (`README.md` e `.gitignore`)

Todo repositório profissional precisa de dois arquivos essenciais logo no nascimento:

1. **`README.md`**: O cartão de visitas do seu projeto (explica o que o projeto faz).
2. **`.gitignore`**: A "lista de bloqueio" informando ao Git quais arquivos e pastas ele deve **ignorar** (ex: senhas, pasta `node_modules/`, arquivos do sistema como `.DS_Store`).

Vamos criar esses dois arquivos usando o terminal:

```bash
# Cria o README com um título inicial
echo "# Meu Novo Projeto" > README.md

# Cria um .gitignore inicial ignorando arquivos temporários ou de dependências
echo "node_modules/" > .gitignore
echo ".env" >> .gitignore
```

---

## 🧠 Hora de Praticar! (Desafio de Fixação)

Vamos testar o que você aprendeu sobre os arquivos iniciais e o fluxo de trabalho.

**Pergunta:** Suponha que você acabou de criar um arquivo chamado `.env` contendo as senhas do seu banco de dados local. Qual é o momento e a ação correta a se fazer para garantir que esse arquivo nunca vá parar no GitHub?

* \[ \] **Opção A:** Fazer o commit primeiro e depois colocar `.env` no arquivo `.gitignore`.
* \[ \] **Opção B:** Adicionar a linha `.env` dentro do arquivo `.gitignore` **antes** de executar `git add .`.
* \[ \] **Opção C:** Executar `git init` novamente para apagar o histórico de senhas.

---

### 🔍 Resposta Correta:

**Resposta: Opção B!**  
O arquivo `.gitignore` só impede que arquivos sejam rastreados **antes** que eles entrem na staging area ou no histórico de commits. Se você fizer o commit antes de ignorar, o arquivo já ficará gravado no histórico!

---

### 5️⃣ Inspecionando o estado (`git status`)

O comando `git status` é o seu **melhor amigo**. Use-o sem moderação para saber o que o Git está enxergando no momento:

```bash
git status
```

Você verá que o Git encontrou dois arquivos "não rastreados" (*untracked files*): `README.md` e `.gitignore`.

---

### 6️⃣ Adicionando ao Stage (`git add`)

Vamos preparar nossos arquivos para o envio. Pense no **Stage** como uma caixa de papelão onde você coloca as coisas antes de fechar a tampa com uma fita adesiva (o commit).

```bash
git add .
```

O ponto (`.`) instrui o Git a adicionar todas as modificações atuais da pasta.

---

### 7️⃣ O Primeiro Commit com Conventional Commits

Agora vamos "fechar a caixa"! Vamos registrar este momento no histórico usando o padrão internacional **Conventional Commits** (onde usamos prefixos como `feat:`, `fix:`, `docs:`, `chore:` etc.).

Como estamos iniciando a estrutura do projeto, usaremos o prefixo `chore:` ou `feat:`:

```bash
git commit -m "chore: inicializa repositorio com README e gitignore"
```

---

### 8️⃣ Validando a conquista (`git log --oneline`)

Parabéns! Você acabou de realizar seu primeiro commit. Que tal dar uma olhada no seu histórico novinho em folha?

```bash
git log --oneline
```

Sua saída será algo parecido com isto:

```text
a1b2c3d (HEAD -> main) chore: inicializa repositorio com README e gitignore
```

---

## 🎯 Checklist Final do Primeiro Repositório

Antes de passar para o próximo passo (como conectar a um repositório remoto no GitHub), certifique-se de ter cumprido todas as etapas:

* [x] Pasta inicializada com `git init -b main`
* [x] Identidade de autor configurada (`user.name` e `user.email`)
* [x] `README.md` e `.gitignore` criados
* [x] Arquivos adicionados ao stage com `git add .`
* [x] Primeiro commit realizado no padrão *Conventional Commits*
* [x] Histórico confirmado com `git log --oneline`

Seu ambiente está totalmente limpo, organizado e pronto para você começar a programar com segurança! 🚀