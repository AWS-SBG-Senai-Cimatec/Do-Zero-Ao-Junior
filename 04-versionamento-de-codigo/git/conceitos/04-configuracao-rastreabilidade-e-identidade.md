# 04. `Configuração, Rastreabilidade e Identidade`

## 📖 Visão Geral

Antes de registrar o primeiro *commit* em qualquer projeto, é fundamental configurar a sua **identidade de desenvolvedor** no Git. Cada alteração confirmada no histórico carrega dados informando quem escreveu o código e quem o aplicou.

Uma configuração correta evita problemas de auditoria, garante a atribuição justa das suas contribuições (como as métricas no perfil do GitHub) e protege a sua privacidade contra o vazamento acidental de dados pessoais ou corporativos.

---

## 🎛️ Escopos de Configuração e Precedência

O Git permite definir configurações em três níveis diferentes de escopo. Entender esses níveis é essencial para aplicar regras globais sem interferir em projetos específicos:

### 1. Sistema (`--system`)
* **Abrangência:** Aplica-se a **todos os usuários e repositórios** da máquina operacional.
* **Onde fica salvo:** No arquivo de sistema `/etc/gitconfig` (requer privilégios de administrador/root para alterar).
* **Uso típico:** Configurações padrão impostas por equipes de TI em computadores corporativos.

### 2. Global (`--global`)
* **Abrangência:** Aplica-se a **todos os repositórios do seu usuário atual** no computador.
* **Onde fica salvo:** No arquivo no seu diretório de usuário (ex: `C:\Users\Nome\.gitconfig` no Windows ou `~/.gitconfig` no Linux/macOS).
* **Uso típico:** Definir o seu nome padrão, e-mail pessoal/padrão, editor preferido e atalhos.

### 3. Local (`--local`)
* **Abrangência:** Aplica-se **exclusivamente ao repositório atual** onde você está executando o comando.
* **Onde fica salvo:** No arquivo oculto `.git/config` dentro da pasta do projeto.
* **Uso típico:** Sobrescrever seu e-mail global para usar o e-mail corporativo em um repositório da empresa.

| Escopo | Opção do Comando | Local de Armazenamento | Nível de Prioridade |
| :--- | :--- | :--- | :--- |
| **Local** | `git config --local` | `.git/config` (Dentro do projeto) | 🟢 **Mais alta** (Sobrescreve os outros) |
| **Global** | `git config --global` | `~/.gitconfig` (Pasta do usuário) | 🟡 **Média** |
| **System** | `git config --system` | `/etc/gitconfig` (Raiz do sistema) | 🔴 **Mais baixa** |

> 💡 **Regra de Precedência:** A configuração mais específica sempre vence. Se você definiu um e-mail `--global` como `nome@pessoal.com`, mas no repositório da empresa definiu `--local` como `nome@empresa.com`, o Git utilizará o e-mail da empresa para os commits desse projeto.

---

## 👤 Identidade Essencial do Desenvolvedor

Para começar a trabalhar, configure os quatro parâmetros básicos essenciais no terminal:

### 1. Definir Nome e E-mail de Autor
```bash
# Configuração para todos os repositórios da sua máquina
git config --global user.name "Seu Nome Completo"
git config --global user.email "seu.email@exemplo.com"
```

### 2. Definir o Nome da Branch Padrão
Por convenção da indústria, novos repositórios devem ser iniciados com a branch principal chamada `main` em vez do nome antigo (`master`):
```bash
git config --global init.defaultBranch main
```
> 💡 **Nota:** Uma *branch* (ramificação) é uma "linha do tempo" independente. Explicaremos os detalhes das ramificações no guia [06. Branches e Ponteiros (HEAD)](06-branches-e-ponteiros-head.md).

### 3. Configurar o Editor de Texto Padrão
Quando o Git precisar que você digite uma mensagem longa de commit ou resolva conflitos, ele abrirá o editor configurado:
```bash
# Para utilizar o IDE como editor do Git
git config --global core.editor "code --wait"
```

### 4. Inspecionar as Configurações Ativas
Para checar quais configurações estão em vigor e de onde elas vêm, utilize:
```bash
# Lista todas as configurações e a origem de cada arquivo
git config --list --show-origin

# Consulta o valor de uma chave específica
git config user.email
```

---

## 🔒 Rastreabilidade e Segurança

### Author vs. Committer: Qual é a diferença?
O Git distingue quem criou a alteração de quem a inseriu no repositório:

* **Author (Autor):** A pessoa que originalmente escreveu o código e criou a alteração (`user.name` e `user.email`).
* **Committer (Comitente):** A pessoa (ou sistema) que aplicou a alteração no repositório. O *Committer* muda quando um commit sofre um `rebase`, um `cherry-pick` ou é integrado via interface do GitHub.

### Cuidados com E-mail Corporativo vs. Pessoal e Privacidade
* **Mistura de Identidades:** Fazer commits em projetos corporativos usando seu e-mail pessoal (ou vice-versa) pode expor dados ou impedir a contabilização de métricas no GitHub.
* **Privacidade do E-mail Pessoal:** Lembre-se de que cada commit enviado para um repositório público no GitHub expõe o e-mail do autor no histórico aberto para todo o mundo.
* **Uso de E-mail de Privacidade do GitHub:** Se desejar esconder seu e-mail pessoal em projetos públicos, acesse as configurações de conta no GitHub (*Settings > Emails*) e ative a opção *"Keep my email addresses private"*. O GitHub fornecerá um e-mail anônimo no formato `ID+username@users.noreply.github.com` para usar na sua máquina:

```bash
git config --global user.email "12345678+seu-usuario@users.noreply.github.com"
```

---

## 🔗 Próximos Passos

Com o ambiente devidamente configurado e a sua identidade definida, avance para o entendimento da estrutura interna dos commits e os padrões profissionais de escrita de mensagens:

* [03. Zonas e Ciclo de Vida de Arquivos](03-zonas-e-ciclo-de-vida-de-arquivos.md)
* [05. Anatomia de um Commit e Conventional Commits](05-anatomia-de-um-commit-e-conventional-commits.md)
---