# 🌿 Guia Prático 02: Trabalhando com Feature Branches e Commits Atômicos

 Agora que você já sabe como inicializar um repositório, é hora de dar um passo essencial no trabalho em equipe (ou até no trabalho solo): **isolar o desenvolvimento de novas funcionalidades em branches separadas**.

Imagine que a branch `main` é a linha de produção de uma fábrica rodando perfeitamente. Você nunca iria querer testar uma peça experimental diretamente na esteira principal e arriscar parar toda a fábrica, certo? 

Em vez disso, você cria uma **mesa de testes ao lado** (a sua *feature branch*), faz todas as alterações com segurança e, quando tudo estiver perfeito e testado, traz essas novidades de volta para a esteira principal.

Vamos aprender como fazer isso de ponta a ponta!

---

## 🎬 O Cenário

Você recebeu a tarefa de criar uma nova funcionalidade no sistema: uma página de perfil para os usuários. Para manter o código da branch `main` sempre estável, você irá criar uma branch separada chamada `feat/perfil-usuario`, fará alterações em pequenos passos organizados (commits atômicos) e, no final, fará o envio dessas melhorias para a `main` e excluirá a branch temporária.

---

## 🗺️ Passo a Passo do Roteiro

### 1️⃣ Garantindo que a base está atualizada

Antes de criar qualquer branch nova, certifique-se de estar na branch principal e com o código mais recente do projeto:

```bash
# Alterna para a branch principal
git switch main

# Atualiza com as novidades mais recentes do repositório remoto (se houver)
git pull origin main
```

> 💡 **Por que isso é importante?** Criar uma branch a partir de uma versão desatualizada da `main` aumenta muito a chance de você encarar conflitos de merge (*merge conflicts*) no futuro.

---

### 2️⃣ Criando e alternando para a Feature Branch (`git switch -c`)

Para criar a nova branch e já entrar nela imediatamente, usamos o comando moderno `git switch` com a flag `-c` (*create*):

```bash
git switch -c feat/perfil-usuario
```

**Convenção de nomes para branches:**
* `feat/nome-da-feature` — para novas funcionalidades.
* `fix/nome-do-bug` — para correção de erros.
* `docs/nome-da-doc` — para alterações apenas em documentação.

Confirme em qual branch você está com o comando:

```bash
git branch
```

*(A branch atual estará destacada e com um asterisco `*` ao lado).*

---

### 3️⃣ Fazendo Commits Incrementais e Atômicos

Um **commit atômico** é aquele que cumpre **uma única tarefa específica**. Em vez de fazer 50 alterações diferentes e registrar tudo em um único commit gigante ("modificações no sistema"), divida o trabalho em pequenos blocos lógicos.

Vamos simular o desenvolvimento do perfil em duas etapas pequenas:

#### **Etapa A: Criando a estrutura HTML**
Crie ou edite o arquivo do perfil e adicione ao stage:

```bash
# Adiciona o arquivo modificado ao stage
git add perfil.html

# Cria o commit da primeira alteração
git commit -m "feat: cria estrutura basica da pagina de perfil"
```

#### **Etapa B: Adicionando a estilização CSS**
Agora faça a alteração no arquivo de estilos:

```bash
git add estilos-perfil.css
git commit -m "style: adiciona estilos visuais ao perfil do usuario"
```

---

## 🧠 Hora de Praticar! (Desafio de Fixação)

Vamos testar o seu entendimento sobre a criação e organização de branches!

**Cenário:** Você está no meio do desenvolvimento na branch `feat/perfil-usuario` e percebe que precisa corrigir um erro urgente de digitação no `README.md`. Qual é a melhor atitude alinhada às boas práticas de versionamento?

- [ ] **Opção A:** Fazer a correção do `README.md` ali mesmo na `feat/perfil-usuario`, junto com o código do perfil, e commitar tudo junto.
- [ ] **Opção B:** Salvar o trabalho atual, alternar para a `main` (ou criar uma branch `fix/correcao-readme`), fazer o commit isolado e depois voltar para a `feat/perfil-usuario`.
- [ ] **Opção C:** Deletar a branch `feat/perfil-usuario` para recomeçar do zero.

---

### 🔍 Resposta Correta:

**Resposta: Opção B!**

Manter as responsabilidades isoladas é a regra de ouro. Se você mistura correções gerais dentro de uma branch de funcionalidade específica, o histórico fica confuso e dificulta o trabalho em equipe na hora de revisar o código.

---

### 4️⃣ Voltando para a `main` para realizar a mesclagem

Com a funcionalidade pronta e testada na sua branch, é hora de integrar tudo à branch principal.

Primeiro, volte para a `main`:

```bash
git switch main
```

---

### 5️⃣ Executando o Merge (`git merge`)

Agora, traga todo o histórico de commits da branch `feat/perfil-usuario` para dentro da `main`:

```bash
git merge feat/perfil-usuario
```

Se não houver conflitos, o Git realizará o merge automaticamente (geralmente usando o modo *Fast-forward*, unindo os históricos de forma fluida).

---

### 6️⃣ Deletando a branch finalizada com segurança (`git branch -d`)

Após o merge bem-sucedido, a branch `feat/perfil-usuario` cumpriu seu papel e não é mais necessária. É uma boa prática de higiene de código deletar branches que já foram integradas:

```bash
git branch -d feat/perfil-usuario
```

> 🛡️ **Segurança do Git:** Se você tentar usar `-d` em uma branch cujas alterações ainda **não** foram mescladas, o Git vai recusar e te avisar para evitar perda de trabalho acidental!

---

## 🎯 Checklist Final do Fluxo de Feature Branch

Marque cada passo concluído ao longo do seu ciclo de desenvolvimento:

- [x] Branch principal atualizada (`git switch main` + `git pull`)
- [x] Nova branch criada com nome padronizado (`git switch -c feat/...`)
- [x] Alterações divididas em commits pequenos e atômicos
- [x] Retorno para a branch `main` (`git switch main`)
- [x] Mesclagem das novidades com sucesso (`git merge feat/...`)
- [x] Remoção da branch local finalizada (`git branch -d feat/...`)

---

## 💬 Reflexão Final

Usar *feature branches* e fazer *commits atômicos* pode parecer um pequeno detalhe burocrático no começo, mas é o segredo que separa desenvolvedores iniciantes de profissionais experientes. Esse hábito garante um histórico limpo, facilita encontrar erros no futuro e evita dores de cabeça ao trabalhar em grupo. 🚀