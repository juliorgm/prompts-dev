# Checklist de release

**Onde:** StackSpot (não mexe em código, pode ser completo).

**Objetivo:** gerar um checklist pré-release específico para o que está sendo entregue.

**Quando usar:** antes de congelar a versão / enviar para o trem de release.

**Placeholders:**
- `{{entregas}}` — histórias/bugs da versão
- `{{processo}}` — etapas do processo de release do time (genérico)

## Prompt

```
Você é um release manager mobile experiente.

## Processo de release do time
{{processo}}

## O que entra nesta versão
{{entregas}}

## Tarefa
Gere um checklist de release dividido em:
1. **Código:** PRs mergeados, versão/versionCode, lint e testes verdes, sem TODO/log de debug, R8/ProGuard (regras para novas classes serializadas).
2. **Feature flags:** quais existem, estado padrão, plano de ativação gradual e rollback.
3. **Contratos:** dependências de BFF já em produção, compatibilidade com versões antigas do app.
4. **Qualidade:** cenários de regressão prioritários com base nas entregas, dispositivos/versões de Android críticos, acessibilidade.
5. **Observabilidade:** eventos de analytics novos, logs, alertas e dashboards para acompanhar.
6. **Comunicação:** quem avisar, nota de versão, plano de contingência.
7. **Pós-release:** o que monitorar nas primeiras 24–72h e critério para rollback.

Formato: checklist em Markdown (- [ ]), com destaque nos itens de maior risco desta versão.
```
