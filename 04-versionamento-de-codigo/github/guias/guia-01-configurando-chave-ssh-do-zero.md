# Guia 01 — Configurando uma chave SSH do zero

## 🎯 Objetivo

Aprender a configurar uma chave SSH para autenticar no GitHub sem precisar informar usuário e senha a cada operação Git que utilize SSH.

Ao final deste guia, você será capaz de:

- Entender o que são SSH e chaves pública e privada.
- Gerar uma chave SSH no computador.
- Adicionar a chave pública à sua conta do GitHub.
- Testar a conexão com o GitHub.
- Utilizar a URL SSH de um repositório.

## 📋 Pré-requisitos

Antes de começar, verifique se você possui:

- Uma conta no [GitHub](https://github.com/).
- O Git instalado no computador.
- Acesso a um terminal, como Git Bash, PowerShell ou terminal do Linux.
- Conexão com a internet.

Para verificar a instalação do Git, execute:

```bash
git --version
```

Se o comando retornar uma versão, como `git version 2.x.x`, o Git está instalado.

## 1. O que é SSH?

SSH (*Secure Shell*) é um protocolo que permite estabelecer uma conexão segura entre computadores. No GitHub, ele pode ser utilizado para autenticar operações Git, como `clone`, `fetch`, `pull` e `push`.

A autenticação utiliza um par de chaves:

- **Chave privada:** fica armazenada no seu computador e não deve ser compartilhada.
- **Chave pública:** pode ser cadastrada na sua conta do GitHub.

Uma analogia: imagine que a chave pública funciona como um cadeado que você entrega ao GitHub, enquanto a chave privada é a chave que fica guardada com você. A conexão é validada sem que você precise enviar sua chave privada ao GitHub.

> ⚠️ **Importante:** nunca compartilhe sua chave privada. A chave pública é a que deve ser cadastrada no GitHub.

## 2. Verifique se já existem chaves SSH

Antes de gerar uma nova chave, confira se o computador já possui alguma.

No terminal, execute:

```bash
ls -al ~/.ssh
```

Esse comando lista os arquivos do diretório `.ssh`.

Procure arquivos com nomes como:

- `id_ed25519` — chave privada.
- `id_ed25519.pub` — chave pública.

Também podem existir chaves com outros nomes, como `id_rsa` e `id_rsa.pub`.

Se já existir uma chave que você deseja utilizar, não é necessário gerar outra automaticamente. Verifique se ela corresponde à sua conta e se você possui a chave privada.

Se não houver uma chave adequada, prossiga para a próxima etapa.

**No Windows:** o comando pode ser executado no Git Bash ou no PowerShell quando o OpenSSH estiver disponível.

## 3. Gere um novo par de chaves SSH

Recomenda-se utilizar o algoritmo Ed25519 quando ele for suportado pelo ambiente.

Execute:

```bash
ssh-keygen -t ed25519 -C "seu-email@example.com"
```

Substitua `seu-email@example.com` pelo e-mail associado à sua conta do GitHub.

O terminal solicitará o local para salvar a chave:

```text
Enter file in which to save the key:
```

Pressione `Enter` para aceitar o caminho padrão, caso você não tenha uma chave com esse nome.

Em seguida, será solicitada uma *passphrase*, que funciona como uma proteção adicional para a chave privada.

Você pode definir uma passphrase segura. Ao digitá-la, os caracteres podem não aparecer no terminal; isso é normal.

Ao finalizar, normalmente serão criados dois arquivos:

```text
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
```

O primeiro é a chave privada. O segundo é a chave pública.

## 4. Inicie o agente SSH e adicione a chave

O agente SSH ajuda a disponibilizar a chave para autenticação sem exigir que você digite a passphrase repetidamente.

No Git Bash ou em um terminal Linux com OpenSSH, execute:

```bash
eval "$(ssh-agent -s)"
```

Depois, adicione a chave privada ao agente:

```bash
ssh-add ~/.ssh/id_ed25519
```

Se você salvou a chave com outro nome ou em outro caminho, ajuste o comando.

> **Observação sobre o Windows:** a inicialização do agente SSH pode variar conforme o terminal e a configuração do OpenSSH. No PowerShell, o serviço `ssh-agent` pode precisar estar habilitado antes de utilizar `ssh-add`.

## 5. Copie a chave pública

Agora, você precisa copiar a chave pública para cadastrá-la no GitHub.

No Git Bash ou Linux, execute:

```bash
cat ~/.ssh/id_ed25519.pub
```

O terminal exibirá uma linha que começa, normalmente, com `ssh-ed25519`.

Copie a linha completa, do início ao fim.

No PowerShell do Windows, você também pode utilizar:

```powershell
Get-Content "$HOME\.ssh\id_ed25519.pub"
```

**Atenção:** copie somente o arquivo terminado em `.pub`. Nunca copie ou envie o conteúdo de `id_ed25519`, que é a chave privada.

## 6. Cadastre a chave pública no GitHub

Siga estas etapas:

1. Entre na sua conta do [GitHub](https://github.com/).
2. Clique na sua foto de perfil e abra **Settings**.
3. No menu lateral, selecione **SSH and GPG keys**.
4. Clique em **New SSH key**.
5. Em **Title**, informe um nome que identifique o computador, como `Notebook pessoal`.
6. Em **Key type**, selecione `Authentication Key`.
7. Cole a chave pública no campo **Key**.
8. Clique em **Add SSH key** e confirme sua identidade, se solicitado.

Pronto! A chave pública foi cadastrada na sua conta.

## 7. Teste a conexão com o GitHub

No terminal, execute:

```bash
ssh -T git@github.com
```

Na primeira conexão, pode aparecer uma mensagem perguntando se você confia na autenticidade do servidor.

Antes de aceitar, confira a impressão digital (*fingerprint*) apresentada com as impressões digitais oficiais publicadas pelo GitHub:

https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints

Se a impressão digital corresponder, confirme a conexão.

Uma autenticação bem-sucedida apresenta uma mensagem semelhante a:

```text
Hi SEU-USUARIO! You've successfully authenticated, but GitHub does not provide shell access.
```

O texto informa que a autenticação funcionou. A mensagem sobre *shell access* é esperada: o GitHub permite operações Git autenticadas, mas não oferece um terminal interativo comum por essa conexão.

## 8. Utilize a URL SSH de um repositório

Para clonar um repositório usando SSH:

1. Abra a página do repositório no GitHub.
2. Clique em **Code**.
3. Selecione a opção **SSH**.
4. Copie a URL apresentada.

Uma URL SSH tem este formato:

```text
git@github.com:USUARIO/REPOSITORIO.git
```

Utilize-a no comando:

```bash
git clone git@github.com:USUARIO/REPOSITORIO.git
```

Substitua `USUARIO/REPOSITORIO` pelos dados do projeto desejado.

**Importante:** a autenticação SSH não concede automaticamente permissão de escrita. Para enviar alterações a um repositório, sua conta precisa ter acesso adequado.

## 9. Problemas comuns

### `Permission denied (publickey)`

Possíveis causas:

- A chave pública não foi cadastrada na conta correta.
- O agente SSH não está carregando a chave privada.
- A chave utilizada não corresponde à chave pública cadastrada.

Verifique o agente:

```bash
ssh-add -l
```

Se nenhuma identidade estiver carregada, adicione sua chave com `ssh-add`.

### `Could not open a connection to your authentication agent`

O agente SSH não está iniciado ou não está acessível no terminal atual.

Inicie-o conforme o ambiente utilizado e tente adicionar a chave novamente.

### A conexão funciona, mas não consigo fazer `push`

A autenticação pode estar correta, mas você pode não ter permissão de escrita no repositório.

Confira se você está utilizando a URL correta, se possui acesso ao projeto e se está trabalhando na branch apropriada.

### Cadastrei a chave na conta errada

Confira a conta GitHub em que a chave foi cadastrada. Se necessário, remova a chave dessa conta e cadastre a chave pública na conta correta.

## ✅ Checklist final

- [ ] Verifiquei se já existia uma chave SSH adequada.
- [ ] GereI um par de chaves, se necessário.
- [ ] Mantive a chave privada protegida.
- [ ] Adicionei a chave pública à conta do GitHub.
- [ ] Testei a conexão com `ssh -T git@github.com`.
- [ ] Entendi como clonar um repositório usando SSH.

## 📚 Referências oficiais

- [GitHub Docs — Conectar-se ao GitHub com SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- [GitHub Docs — Gerar uma nova chave SSH e adicioná-la ao agente SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- [GitHub Docs — Adicionar uma nova chave SSH à sua conta do GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
- [GitHub Docs — Testar sua conexão SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)

---

**Próximo passo:** depois de validar este guia, avance para o Guia 02, que demonstrará o fluxo de contribuição em projetos open source usando Fork, branches, `upstream` e Pull Requests.
