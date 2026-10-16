# Investigar bug (sem crash)

**Onde:** Copilot.
**Uso:** dado errado, tela travada ou estado inconsistente.
**Troque:** `{{bug}}` = esperado x observado, passos e frequência.

## Parte 1 — Caminho do dado
```
Bug: {{bug}}. Mapeie o caminho do dado da API até a tela (Repository → UseCase → ViewModel → UI) e diga em que pontos ele pode se corromper. Não proponha correção ainda.
```

## Parte 2 — Hipóteses
```
Liste as hipóteses por probabilidade (cache, race condition, process death, recomposição, flag, locale/fuso) e um experimento barato para confirmar ou descartar cada uma.
```

## Parte 3 — Correção
```
A causa é {{causa}}. Proponha a correção mínima e um teste de regressão.
```
