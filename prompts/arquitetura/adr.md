# ADR (Architecture Decision Record)

**Onde:** StackSpot (não mexe em código, pode ser completo).

**Objetivo:** registrar uma decisão técnica de forma clara, com alternativas e consequências.

**Quando usar:** ao decidir lib, padrão, estratégia de cache, estrutura de módulo, migração etc.

**Placeholders:**
- `{{decisao}}` — o que está sendo decidido
- `{{contexto}}` — situação atual e restrições
- `{{opcoes}}` — alternativas consideradas (se já houver)

## Prompt

```
Você é um arquiteto de software ajudando a documentar uma decisão técnica.

## Decisão
{{decisao}}

## Contexto
{{contexto}}

## Opções consideradas
{{opcoes}}

## Tarefa
Escreva um ADR no formato abaixo. Se houver poucas opções, sugira outras alternativas viáveis. Seja honesto nos contras da opção escolhida.

# ADR-XXX: <título>
- **Status:** Proposto
- **Data:** <hoje>

## Contexto
## Decisão
## Alternativas consideradas
Tabela: | Opção | Prós | Contras | Esforço |
## Consequências
Positivas, negativas e o que passa a ser necessário.
## Critérios para revisitar
Em que situação essa decisão deveria ser reavaliada.
```
