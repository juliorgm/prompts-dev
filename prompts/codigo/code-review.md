# Code review (arquivo ou trecho)

**Onde:** Copilot.
**Uso:** revisar um arquivo ou trecho aberto no editor.
**Troque:** `{{arquivo}}` = #file do código (ou selecione o trecho).

## Parte 1 — Bugs e crash
```
Revise {{arquivo}} como revisor Android sênior. Foque em bugs e risco de crash: null safety, !!, casts, coleções vazias, lifecycle, coroutines (escopo, dispatcher, exceção, cancelamento).
Para cada achado: severidade (🔴🟠🟡), linha, problema e correção. Não invente problemas.
```

## Parte 2 — Arquitetura e padrão
```
Agora revise arquitetura e padronização: respeito às camadas, responsabilidade única, estado de UI imutável, nomes, hardcoded, código duplicado ou morto. Mesmo formato.
```

## Parte 3 — Testes
```
Liste os cenários de teste que faltam para esse código.
```
