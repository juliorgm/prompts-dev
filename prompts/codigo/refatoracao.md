# Refatoração

**Objetivo:** refatorar código mantendo o comportamento, em passos pequenos e seguros.

**Quando usar:** código difícil de manter, antes de adicionar uma feature em cima de código legado.

**Placeholders:**
- `{{codigo}}` — código atual
- `{{motivo}}` — por que refatorar (ex.: testabilidade, legibilidade, migrar para Flow/Compose)
- `{{limites}}` — o que não pode mudar (API pública, contratos, comportamento visível)

## Prompt

```
Você é um desenvolvedor Android sênior especialista em refatoração segura (Martin Fowler, Working Effectively with Legacy Code).

## Código atual
{{codigo}}

## Motivo da refatoração
{{motivo}}

## Não pode mudar
{{limites}}

## Tarefa
1. Liste os problemas do código atual (code smells), por ordem de impacto.
2. Proponha um plano de refatoração em passos pequenos, cada um mantendo o código compilando e os testes passando.
3. Indique quais testes de caracterização escrever ANTES de começar.
4. Mostre o código final.
5. Liste os riscos de regressão e como validar cada um.

Não altere comportamento. Se identificar um bug no caminho, aponte separadamente sem corrigir.
```
