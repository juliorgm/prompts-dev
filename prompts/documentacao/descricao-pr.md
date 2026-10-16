# Descrição de PR

**Objetivo:** escrever uma descrição de PR clara, que facilite o review.

**Quando usar:** ao abrir um PR.

**Placeholders:**
- `{{historia}}` — história ou bug relacionado
- `{{diff}}` — diff ou resumo das mudanças
- `{{template_pr}}` — template de PR do time, se houver

## Prompt

```
Você é um desenvolvedor Android sênior escrevendo a descrição de um PR para facilitar o trabalho de quem vai revisar.

## História / bug
{{historia}}

## Mudanças
{{diff}}

## Template do time (se houver, siga-o)
{{template_pr}}

## Tarefa
Escreva a descrição com:
- **O quê:** resumo em 2–3 linhas
- **Por quê:** motivação e link da história
- **Como:** principais decisões técnicas e alternativas descartadas
- **Onde olhar com mais atenção:** arquivos/trechos de maior risco
- **Como testar:** passos objetivos, incluindo feature flag e massa de dados
- **Evidências:** espaço para prints/vídeo (antes/depois)
- **Checklist:** testes, acessibilidade, analytics, sem logs sensíveis

Seja direto. Nada de texto genérico.
```
