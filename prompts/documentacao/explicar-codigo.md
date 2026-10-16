# Explicar código legado

**Onde:** Copilot.
**Uso:** entender um trecho desconhecido antes de mexer.
**Troque:** `{{arquivo}}` = #file; `{{objetivo}}` = o que você precisa fazer nele.

## Parte 1 — Entender
```
Explique {{arquivo}}: o que faz em 3 linhas, o fluxo passo a passo (diagrama Mermaid de sequência) e efeitos colaterais, dependências escondidas ou estado global.
```

## Parte 2 — Onde mexer
```
Preciso: {{objetivo}}. Diga exatamente onde alterar, o que pode quebrar e quais armadilhas o código tem (nomes enganosos, comportamentos não óbvios).
```
