# Guia 04: Desfazendo Erros e Salvando Seu Dia

Este guia é o seu manual de sobrevivência para quando algo der errado durante o desenvolvimento com Git. Aqui você aprenderá técnicas limpas e eficientes para corrigir falhas locais sem poluir o histórico de *commits*.

---

## Caso 1: Esqueci de colocar um arquivo no último commit
### PRETEXTO: crie um repositório, crie dois arquivos quaisquer e faça commit de apenas um deles.

Um dos cenários mais comuns no dia a dia de desenvolvimento é realizar um *commit* e, logo em seguida, perceber que ficou faltando adicionar um arquivo importante. 

Por exemplo, imagine que você estruturou o projeto, fez o commit inicial contendo apenas o `arq1`, mas acabou deixando o `arq2` de fora (*untracked*).

<img width="374" height="105" alt="image" src="https://github.com/user-attachments/assets/6f282354-785c-41ad-ac4f-7d4cb670127a" />

(imagem do vs code, "U" significa untracked, ou seja, não mapeado/não conhecido pelo git)

---

### Como resolver de forma limpa com `git commit --amend`

Em vez de poluir o histórico do seu repositório criando um *commit* extra e desnecessário (com mensagens como *"ops, esqueci o arquivo"*), a melhor prática é **anexar o arquivo diretamente ao commit anterior**.

Para solucionar isso, basta executar os comandos abaixo no seu terminal:

```bash
git add arq2
git commit --amend --no-edit
```

<img width="697" height="154" alt="image" src="https://github.com/user-attachments/assets/66e11a6e-d070-4c05-bde3-bf7f28b8f655" />

---

### 🔍 Entendendo o passo a passo:

* **`git add arq2`**: Adiciona o arquivo que estava faltando (`arq2`) para dentro da *staging area* (área de preparação).
* **`git commit --amend`**: Informa ao Git que você deseja **consertar/atualizar** o último *commit* realizado, fundindo as alterações que estão na *staging area* nele.
* **`--no-edit`**: É uma flag de produtividade que diz ao Git: *"Guarde o arquivo novo no commit anterior, mas mantenha exatamente a mesma mensagem de commit que já estava lá, sem abrir o editor de texto"*.

> ⚠️ **Atenção:** Só utilize o `--amend` se você **ainda não** tiver enviado (*push*) esse commit alterado para um repositório remoto público ou compartilhado com a equipe, pois ele reescreve o histórico local.
