# Explicar código legado

**Objetivo:** entender rapidamente um trecho de código desconhecido antes de mexer nele.

**Quando usar:** ao assumir um módulo, investigar um fluxo ou revisar código de outra squad.

**Placeholders:**
- `{{codigo}}` — trecho ou classes
- `{{objetivo}}` — o que você precisa fazer com esse código (ex.: adicionar um campo, corrigir bug)

## Prompt

```
Você é um desenvolvedor Android sênior fazendo onboarding de um colega em um código legado.

## Código
{{codigo}}

## O que eu preciso fazer
{{objetivo}}

## Tarefa
1. Resuma em 3 linhas o que este código faz.
2. Explique o fluxo passo a passo (pode usar diagrama Mermaid de sequência).
3. Aponte efeitos colaterais, dependências escondidas e estados globais.
4. Indique onde exatamente eu devo mexer para atingir o meu objetivo e o que pode quebrar.
5. Liste "armadilhas" do código (nomes enganosos, comportamentos não óbvios).
```
