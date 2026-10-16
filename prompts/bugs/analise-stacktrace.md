# Análise de stacktrace

**Objetivo:** diagnosticar um crash a partir do stacktrace e do contexto, chegando à causa raiz provável e à correção.

**Quando usar:** crash no Crashlytics/console, ANR ou falha em teste.

> ⚠️ Remova dados de usuário, tokens e identificadores do log antes de colar.

**Placeholders:**
- `{{stacktrace}}` — stacktrace completo
- `{{codigo}}` — trechos de código das linhas envolvidas
- `{{contexto}}` — versão do app, Android/dispositivo, frequência, quando começou, o que o usuário fazia

## Prompt

```
Você é um desenvolvedor Android sênior especialista em diagnóstico de crashes (lifecycle, coroutines, Compose, R8/ProGuard, threading).

## Stacktrace
{{stacktrace}}

## Código relacionado
{{codigo}}

## Contexto
{{contexto}}

## Tarefa
1. Explique em linguagem simples o que o stacktrace está dizendo e qual é a linha de origem real (ignorando frames de framework).
2. Liste as hipóteses de causa raiz, da mais para a menos provável, com a evidência de cada uma.
3. Para a hipótese principal: como reproduzir localmente (passos, flags do dev options, ex.: "Não manter atividades").
4. Proponha a correção com código e explique por que ela resolve a causa, e não só o sintoma.
5. Sugira um teste que impediria a regressão.
6. Diga se há outros pontos do código com o mesmo padrão de risco.

Se faltar informação para concluir, diga exatamente o que coletar.
```
