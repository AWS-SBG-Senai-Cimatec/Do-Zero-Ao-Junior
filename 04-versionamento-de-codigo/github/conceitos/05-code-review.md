# Code Review

> **Objetivo:** entender por que a revisão de código existe, conhecer os três tipos de revisão do GitHub, aprender a sugerir alterações diretamente no código e adotar uma comunicação profissional e empática.

---

## Ambientação 

Depois que o código é escrito e a Pull Request é aberta, ele ainda não está pronto para entrar na `main`. Antes, outra pessoa da equipe precisa olhar o que foi feito. Esse processo é chamado de **code review** (revisão de código).

No GitHub, a revisão acontece dentro da própria Pull Request: quem revisa lê as alterações, comenta, sugere mudanças e, no fim, da um parecer formal. Como vimos no arquivo [04 - Organizations](04-github-organizations.md), as **Branch Protection Rules** podem exigir um número mínimo de aprovações antes do merge, e é o code review que gera essas aprovações.

---

## 1. A cultura de revisão de código

Revisar código não é "caçar erros da pessoa". É uma prática da equipe, com três objetivos:

| Objetivo | O que significa na prática |
| --- | --- |
| **Qualidade técnica** | Garantir que o código está claro, funciona e segue os padrões do projeto |
| **Segurança** | Perceber falhas, como senhas no código ou entradas sem validação, antes de chegarem à produção |
| **Aprendizado mútuo** | Quem revisa aprende com a solução do outro, e quem é revisado aprende com as observações |

> A revisão é sobre o **código**, nunca sobre a **pessoa**. Em vez de "você fez isso errado", prefira "esse trecho pode gerar um erro quando a lista vier vazia".

---

## 2. Tipos de revisão

Ao finalizar a revisão, o GitHub pede que você escolha um dos três tipos (aba **Files changed → Review changes**):

| Tipo | Quando usar | Efeito na Pull Request |
| --- | --- | --- |
| **Approve** | O código está bom e pode ser mesclado | Conta como aprovação para as regras de proteção da branch |
| **Request changes** | Existe algo que precisa ser corrigido antes do merge | Pode bloquear o merge até a pessoa corrigir e a revisão ser refeita |
| **Comment** | Observações ou dúvidas, sem aprovar nem bloquear | Não altera a situação da Pull Request |


---

## 3. Comentários em linha e a tag `suggestion`

Na aba **Files changed**, ao passar o mouse sobre o número de uma linha, aparece um botão **+** para comentar naquele ponto exato do código. Dá para selecionar várias linhas para comentar um bloco inteiro.

Quando a correção é pequena e você já sabe qual é, em vez de só descrever, é possível **sugerir o código pronto**. Basta usar o botão de sugestão (ícone de ±) ou escrever um bloco com a tag `suggestion`:

````markdown
```suggestion
total = sum(precos) / len(precos) if precos else 0
```
````

O bloco substitui as linhas selecionadas. Quem recebe a sugestão vê o "antes e depois" e pode aceitar com um clique em **Commit suggestion**, e o GitHub cria o commit automaticamente.

> **Dica:** para aceitar várias sugestões de uma vez, use **Add suggestion to batch** em cada uma e depois **Commit suggestions**. Assim você gera um único commit.

---

## 4. Boas práticas e etiqueta

### Para quem revisa

- Leia primeiro a descrição da Pull Request e a Issue ligada a ela, para entender o objetivo.
- Seja **específico**: aponte a linha, explique o motivo e, se possível, sugira a solução.
- Faça **perguntas** quando não tiver certeza ("O que acontece se o usuário não existir?").
- Reconheça o que está bom. Elogiar uma boa solução também faz parte da revisão.
- Diferencie o que **bloqueia** do que é só **preferência** (por exemplo, prefixando com `nit:` para detalhes menores).
- Revise com rapidez razoável: uma PR parada atrasa a equipe inteira.

### Para quem é revisado

- Mantenha a PR **pequena e focada**, pois é muito mais fácil revisar 100 linhas do que 1.000.
- Descreva o que mudou e por quê, e vincule a Issue com `Closes #XX`.
- Não leve para o lado pessoal: o comentário é sobre o código.
- Responda a todos os comentários, seja corrigindo ou explicando por que manteve a decisão.

### Comparando comunicações

| Menos adequado | Mais adequado |
| --- | --- |
| "Isso está horrível." | "Esse bloco ficou longo. Que tal separar em duas funções?" |
| "Por que fez assim?" | "Qual foi o motivo de usar um laço aqui? Pensei que `map` deixaria mais legível." |
| "Errado." | "Acho que esse cálculo falha quando o valor é zero. Pode conferir?" |

---

## 5. Exemplo prático

Imagine que uma pessoa abriu uma Pull Request com a seguinte função:

```python
def media(precos):
    return sum(precos) / len(precos)
```

1. Na aba **Files changed**, clique no **+** da linha do `return`.
2. Escreva o comentário com empatia e uma sugestão:

````markdown
Se a lista vier vazia, essa linha gera um erro de divisão por zero. 
Uma possibilidade:

```suggestion
    return sum(precos) / len(precos) if precos else 0
```
````

3. Clique em **Start a review** e finalize em **Review changes → Request changes**.
4. A pessoa autora aceita a sugestão com **Commit suggestion**, e você volta, confere e marca **Approve**.

---

## Referências

- [GitHub Docs: Sobre revisões de Pull Request](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews)
- [GitHub Docs: Revisando alterações em uma Pull Request](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request)
- [GitHub Docs: Incorporando feedback com sugestões](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/incorporating-feedback-in-your-pull-request)

---

[← Anterior: 04 - Organizations](04-github-organizations.md) | [Próximo: 06 - Estratégias de Versionamento →](../06-estrategias-versionamento/estrategias-versionamento.md)
