# Mensagem para o time

**Onde:** StackSpot (não mexe em código, pode ser completo).

**Objetivo:** comunicar impedimento, status, risco ou decisão técnica de forma clara e curta.

**Quando usar:** Slack/Teams com PO, outras squads, BFF, liderança.

**Placeholders:**
- `{{situacao}}` — o que aconteceu / o que precisa ser comunicado
- `{{destinatario}}` — quem vai ler (PO, tech lead, outra squad, gestor)
- `{{pedido}}` — o que você precisa da pessoa (decisão, ajuda, só ciência)

## Prompt

```
Você me ajuda a escrever mensagens de trabalho claras e objetivas.

## Situação
{{situacao}}

## Para quem
{{destinatario}}

## O que eu preciso
{{pedido}}

## Tarefa
Escreva a mensagem para chat corporativo:
- Primeira linha já diz o assunto e o pedido
- Contexto em no máximo 3 linhas, sem jargão desnecessário para o destinatário
- Impacto (prazo, usuário, outras squads) quando houver
- Próximo passo e prazo esperado de resposta
- Tom cordial e direto

Gere 2 versões: uma curta (até 4 linhas) e uma completa.
```
