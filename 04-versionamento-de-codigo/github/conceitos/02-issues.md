# GitHub Issues

## O que são Issues?

Issues são registros usados para acompanhar o trabalho de um repositório. Elas ajudam a equipe a documentar demandas e conversar sobre elas sem perder o histórico.

Uma Issue pode registrar:

- um **bug** que precisa ser investigado;
- uma **solicitação de recurso** (*feature request*);
- uma **discussão** ou tarefa relacionada ao projeto.

## Como descrever uma Issue

Uma boa Issue ajuda outra pessoa a entender o problema e decidir o que fazer. O título deve ser curto e específico. A descrição deve trazer informações relevantes para o caso.

Para relatar um bug, inclua:

1. **Comportamento atual:** o que aconteceu?
2. **Comportamento esperado:** o que deveria acontecer?
3. **Passos para reproduzir:** quais ações levam ao problema?
4. **Contexto:** versão do programa, sistema operacional ou outras condições relevantes.
5. **Evidências:** mensagens de erro, logs ou capturas de tela, quando disponíveis.

Evite títulos vagos como “Não funciona”. Um título como “[Bug] O botão de login não responde após preencher os campos” explica melhor o problema.

Para sugerir um recurso, descreva a necessidade e como a mudança ajudaria quem usa o projeto. Não é necessário propor uma solução técnica completa.

## Exemplo de relato de bug

**Título:** `[Bug] A busca não mostra resultados com letras maiúsculas`

**Comportamento atual:** ao buscar um nome com letras maiúsculas, a lista aparece vazia.

**Comportamento esperado:** a busca deve encontrar o item mesmo quando a capitalização for diferente.

**Passos para reproduzir:**

1. Abrir a página de busca.
2. Digitar o nome usando letras maiúsculas.
3. Confirmar a busca.

**Contexto:** versão 1.2 do aplicativo, navegador Chrome.

**Evidência:** anexar uma captura de tela ou uma mensagem de erro, se houver.

## Labels e Milestones

- **Labels** são etiquetas que ajudam a classificar e filtrar Issues. Exemplos: `bug`, `documentation`, `enhancement` e `help wanted`.
- **Milestones** agrupam Issues relacionadas a uma entrega ou objetivo, como uma versão do projeto ou uma etapa do trabalho.

Use labels e milestones conforme as convenções do repositório. Uma Issue pode ter mais de uma label e ser associada a um milestone.

## Boas práticas

- Pesquise se já existe uma Issue sobre o mesmo assunto antes de abrir outra.
- Escreva de forma objetiva e respeitosa.
- Inclua informações suficientes para que outra pessoa consiga entender ou reproduzir o problema.
- Atualize a Issue quando surgirem novas informações.
- Não publique senhas, tokens ou dados pessoais em descrições, logs ou anexos.
