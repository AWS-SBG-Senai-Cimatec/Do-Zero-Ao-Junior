# 04. ➕ git-add — Preparação de Alterações (Staging Area)

## 📖 Visão Geral

O `git add` move as alterações feitas nos seus arquivos do diretório de trabalho para a área de preparação ([staging area](./04-git-add.md)). É aqui que você seleciona exatamente o que deseja incluir no próximo [commit](./05-git-commit.md).

---

## 📋 Sintaxe Oficial

```bash
git add [flags] [<caminho>]
```

---

## 🚩 Tabela de Flags Úteis

| Flag / Parâmetro | Descrição | Na Prática |
| :--- | :--- | :--- |
| `<arquivo>` | Prepara um arquivo específico. | Quando alterou vários arquivos, mas quer salvar apenas um. |
| `. (ponto)` | Prepara todas as alterações do diretório atual e subpastas. | Para adicionar rapidamente todo o trabalho feito. |
| `-p` / `--patch` | Abre um modo interativo para escolher trechos específicos do arquivo (*hunks*). | Para revisar linha por linha antes de colocar na staging area. |
| `-u` / `--update` | Prepara apenas arquivos modificados e excluídos, ignorando arquivos novos. | Útil ao refatorar código existente sem incluir rascunhos novos. |

---

## 💻 Exemplos Práticos do Dia a Dia

```bash
# Prepara apenas o arquivo 'README.md'
git add README.md

# Prepara todas as modificações da pasta atual
git add .

# Seleciona interativamente os blocos de código que deseja adicionar
git add -p
```

### 🖥️ Saída Esperada no Terminal

```console
$ git add README.md
(nenhuma mensagem é exibida em caso de sucesso)
```

> 💡 **O que significa essa saída?**  
> O comando `git add` é silencioso por padrão quando executado com sucesso. As alterações foram movidas para a *staging area* e estão prontas para serem salvas. É possível confirmar rodando `git status`.

---

## 💡 Boas Práticas

- ✅ **Commits Atômicos:** Utilize `git add -p` sempre que quiser selecionar alterações específicas e criar commits pequenos e focados.
- ❌ **Verificação Prévia:** Evite usar `git add .` sem conferir o [git status](./03-git-status.md) antes, prevenindo o envio acidental de chaves de API, senhas ou arquivos de configuração do sistema.
---