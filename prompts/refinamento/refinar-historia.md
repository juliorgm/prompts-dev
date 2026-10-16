# Refinar e quebrar história

**Objetivo:** quebrar uma história em tasks técnicas executáveis e antecipar riscos e dúvidas.

**Quando usar:** durante ou logo antes do refinamento técnico.

**Placeholders:**
- `{{historia}}` — história com critérios de aceite
- `{{arquitetura}}` — resumo genérico da arquitetura do módulo (camadas, padrões, libs)

## Prompt

```
Você é um desenvolvedor Android sênior (Kotlin, MVVM, Clean Architecture, Coroutines/Flow, Jetpack Compose) em um super app modular.

## Arquitetura do módulo
{{arquitetura}}

## História
{{historia}}

## Tarefa
Faça o refinamento técnico desta história.

## Formato da resposta

### 1. Entendimento
Resuma em 3 linhas o que precisa ser entregue. Aponte qualquer ambiguidade.

### 2. Impacto por camada
- UI (telas, componentes, navegação, estados)
- Presentation (ViewModel, UiState, eventos)
- Domain (UseCases, modelos, regras)
- Data (Repository, DataSource, DTOs, cache)
- Infra (DI, feature flag, analytics, deeplink)

### 3. Tasks técnicas
Tabela: | # | Task | Camada | Depende de | Complexidade (P/M/G) |
Cada task deve caber em no máximo 1 dia.

### 4. Riscos técnicos
Com probabilidade, impacto e mitigação.

### 5. Perguntas para PO / Design / BFF
Separadas por destinatário.

### 6. Estratégia de testes
Unitários, de UI e cenários manuais para o QA.
```
