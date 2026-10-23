# GitHub Flavored Markdown

> **Objetivo:** dominar a sintaxe do GitHub Flavored Markdown (GFM) para escrever READMEs, Issues, Pull Requests e documentações claros, organizados e com boa aparência.

---

## Para ambientar

O **Markdown** é uma linguagem de marcação simples: você escreve texto comum com alguns símbolos, e ele é convertido em títulos, listas, tabelas e muito mais. O **GitHub Flavored Markdown (GFM)** é a versão usada pelo GitHub, que acrescenta recursos como tabelas, listas de tarefas e alertas.

Ele funciona em arquivos `.md`, descrições e comentários de Issues e Pull Requests, Discussions e Wikis. Tudo escrito nos módulos anteriores, e arquivos desta trilha, usa GFM.

---

## 1. Texto básico

### Títulos

Use `#` para criar títulos. Quanto mais `#`, menor o nível:

# Título 1
## Título 2
### Título 3

```markdown
# Título 1
## Título 2
### Título 3
```

### Ênfase

| Você escreve | Resultado |
| --- | --- |
| `**negrito**` | **negrito** |
| `*itálico*` ou `_itálico_` | *itálico* |
| `***negrito e itálico***` | ***negrito e itálico*** |
| `~~tachado~~` | ~~tachado~~ |
| `` `código em linha` `` | `código em linha` |

### Links e imagens

```markdown
[texto do link](https://github.com)
![texto alternativo](caminho/da/imagem.png)
```

### Citações e linha divisória

```markdown
> Isto é uma citação.

---
```

> **Dica:** sempre preencha o **texto alternativo** das imagens. Ele ajuda a acessibilidade e aparece se a imagem não carregar.

---

## 2. Listas

```markdown
- Item sem ordem
- Outro item
  - Subitem (dois espaços de recuo)

1. Primeiro passo
2. Segundo passo
3. Terceiro passo
```

Resultado:

- Item sem ordem
- Outro item
  - Subitem

1. Primeiro passo
2. Segundo passo
3. Terceiro passo

---

## 3. Tabelas

Use `|` para separar as colunas e uma linha de hífens para separar o cabeçalho:

```markdown
| Comando | Função |
| ------- | ------ |
| `git add` | Adiciona arquivos à área de preparação |
| `git commit` | Registra um snapshot do projeto |
```

| Comando | Função |
| ------- | ------ |
| `git add` | Adiciona arquivos à área de preparação |
| `git commit` | Registra um snapshot do projeto |

Para alinhar o texto, use dois-pontos na linha divisória: `:---` (esquerda), `:---:` (centro) e `---:` (direita).

Exemplo:

```markdown
| Nome | Idade | Cidade |
| :--- | :---: | ---: |
| Ana | 28 | Salvador |
| Bruno | 35 | Recife |
```

| Nome | Idade | Cidade |
| :--- | :---: | ---: |
| Ana | 28 | Salvador |
| Bruno | 35 | Recife |

---

## 4. Caixas de seleção (task lists)

As **task lists** criam listas de tarefas com caixas marcáveis:

```markdown
- [x] Criar a branch
- [x] Escrever o artigo
- [ ] Abrir a Pull Request
- [ ] Receber aprovação do revisor
```

Resultado:

- [ ] Criar a branch
- [ ] Escrever o artigo
- [ ] Abrir a Pull Request
- [ ] Receber aprovação do revisor

Em Issues e Pull Requests do GitHub, as caixas são **interativas**: você pode marcar e desmarcar direto na página, sem precisar editar o texto. O GitHub também mostra o progresso da lista, por exemplo, "2 of 4 tasks".

---

## 5. Blocos de código com realce de sintaxe

Para blocos de código, use três crases (```) e informe a linguagem logo depois. O GitHub aplica as cores correspondentes (*syntax highlighting*):

````markdown
```python
def saudacao(nome):
    return f"Olá, {nome}!"
```
````

Resultado:

```python
def saudacao(nome):
    return f"Olá, {nome}!"
```

Algumas linguagens comuns: `bash`, `python`, `javascript`, `json`, `yaml`, `markdown`, `diff`.

> Para mostrar um bloco de código **dentro** de outro (como nos exemplos deste arquivo), use quatro crases (````) por fora e três por dentro.

---

## 6. Alertas visuais

O GitHub tem alertas nativos, que são citações com um destaque colorido e um ícone. Eles começam com um marcador entre colchetes, na primeira linha da citação:

```markdown
> [!NOTE]
> Informação útil que o leitor deve conhecer, mesmo ao ler por cima.

> [!TIP]
> Conselho para fazer algo de forma melhor ou mais fácil.

> [!IMPORTANT]
> Informação essencial para alcançar o objetivo.

> [!WARNING]
> Conteúdo crítico, que exige atenção por causa de riscos.

> [!CAUTION]
> Avisa sobre consequências negativas de uma ação.
```

| Alerta | Quando usar |
| --- | --- |
| `[!NOTE]` | Informação complementar |
| `[!TIP]` | Dicas e atalhos |
| `[!IMPORTANT]` | Algo indispensável para o sucesso |
| `[!WARNING]` | Riscos que merecem atenção |
| `[!CAUTION]` | Ações com consequências negativas ou irreversíveis |

> **Dica:** não exagere nos alertas. Se tudo é destaque, nada se destaca. Use no máximo alguns por página.

---

## 7. Recursos extras do GitHub

| Recurso | Como escrever | O que faz |
| --- | --- | --- |
| **Menção** | `@usuario` | Notifica a pessoa |
| **Referência a Issue/PR** | `#12` | Cria um link para a Issue ou Pull Request |
| **Fechar Issue** | `Closes #12` | Fecha a Issue quando a PR é mesclada |
| **Emoji** | `:rocket:` | 🚀 |
| **Diagrama** | bloco ` ```mermaid ` | Renderiza fluxogramas e outros diagramas |
| **Seção recolhível** | `<details><summary>...</summary>...</details>` | Esconde conteúdo longo |

---

## 8. Exemplo prático

Um modelo de descrição de Pull Request usando vários recursos:

````markdown
## O que foi feito

Adiciona o artigo sobre code review em `recursos/`.

## Checklist

- [x] Segui o padrão de Conventional Commits
- [x] Conteúdo em pt-BR
- [ ] Revisão do trainee designado

> [!NOTE]
> O diagrama foi feito com Mermaid.

Closes #12
````

---

## Referências

- [GitHub Docs: Sintaxe básica de escrita e formatação](https://docs.github.com/pt/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [GitHub Docs: Sobre listas de tarefas](https://docs.github.com/pt/get-started/writing-on-github/working-with-advanced-formatting/about-task-lists)
- [GitHub Docs: Criando e destacando blocos de código](https://docs.github.com/pt/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks)
- [GitHub Flavored Markdown Spec](https://github.github.com/gfm/)

---

[← Anterior: 06 - Estratégias de Versionamento](../06-estrategias-versionamento/estrategias-versionamento.md)
