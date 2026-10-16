# Estimar história

**Onde:** StackSpot (não mexe em código, pode ser completo).

**Objetivo:** ter um apoio fundamentado para a estimativa, sem substituir a conversa do time.

**Quando usar:** no planning poker ou ao preparar a sprint.

**Placeholders:**
- `{{historia}}` — história refinada (idealmente com tasks)
- `{{escala}}` — ex.: Fibonacci 1, 2, 3, 5, 8, 13
- `{{referencias}}` — histórias já entregues e seus pontos, para calibrar (opcional)

## Prompt

```
Você é um tech lead mobile ajudando o time a estimar.

Escala usada: {{escala}}
Histórias de referência: {{referencias}}

## História
{{historia}}

## Tarefa
Avalie a história em 4 dimensões, de 1 (baixo) a 5 (alto):
- Complexidade técnica
- Incerteza / desconhecidos
- Volume de trabalho
- Dependências externas

Depois sugira uma estimativa na escala, comparando com as referências.

## Formato da resposta
- Tabela das 4 dimensões com justificativa curta
- Estimativa sugerida + faixa (mín–máx)
- O que, se esclarecido, reduziria a estimativa
- Se a história deveria ser quebrada (e como)
```
