# Análise de stacktrace

**Onde:** Copilot.
**Uso:** diagnosticar um crash ou ANR.
**Troque:** `{{stacktrace}}` (sem dados de usuário) e `{{contexto}}` = versão, aparelho, frequência, o que o usuário fazia.

## Parte 1 — Diagnóstico
```
Stacktrace: {{stacktrace}}. Contexto: {{contexto}}.
Ache a linha de origem no nosso código, explique o erro em linguagem simples e liste as hipóteses de causa da mais provável para a menos provável, com evidência.
```

## Parte 2 — Reproduzir
```
Para a hipótese principal, dê os passos para reproduzir localmente (inclua opções do desenvolvedor, como "Não manter atividades", se fizer sentido).
```

## Parte 3 — Corrigir
```
Proponha a correção da causa, não do sintoma, com código. Sugira um teste que pegaria a regressão e aponte outros lugares do código com o mesmo risco.
```
