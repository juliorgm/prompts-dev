# Investigar bug (sem crash)

**Objetivo:** montar hipóteses e um plano de investigação para um bug de comportamento (dado errado, tela travada, estado inconsistente).

**Quando usar:** bug reportado pelo QA, usuário ou produção, sem stacktrace claro.

**Placeholders:**
- `{{descricao_bug}}` — comportamento esperado vs observado
- `{{passos}}` — passos para reproduzir (se conhecidos)
- `{{frequencia}}` — sempre, intermitente, só em alguns dispositivos/versões
- `{{codigo}}` — trechos do fluxo envolvido

## Prompt

```
Você é um desenvolvedor Android sênior conduzindo uma investigação de bug de forma sistemática. Não proponha correção antes de entender a causa.

## Bug
Esperado vs observado: {{descricao_bug}}
Passos: {{passos}}
Frequência: {{frequencia}}

## Código do fluxo
{{codigo}}

## Tarefa
1. Reescreva o problema de forma precisa (o que, onde, quando).
2. Mapeie o caminho do dado: origem (API/cache) → Repository → UseCase → ViewModel → UI. Em qual ponto ele pode estar se corrompendo?
3. Liste hipóteses ordenadas por probabilidade. Considere: cache desatualizado, race condition, estado restaurado após process death, recomposição, flag/feature toggle, diferença de ambiente, fuso horário/locale.
4. Para cada hipótese: um experimento barato para confirmar ou descartar (log, breakpoint, teste, mudança de config).
5. Quando a causa estiver clara: correção mínima + teste de regressão.
```
