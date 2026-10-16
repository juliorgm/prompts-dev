# Tela em Jetpack Compose

**Objetivo:** criar (ou revisar) uma tela Compose bem estruturada: estado, eventos, previews e acessibilidade.

**Quando usar:** ao implementar uma tela nova ou migrar uma tela de XML para Compose.

**Placeholders:**
- `{{descricao_tela}}` — layout e comportamento em texto (componentes, estados, interações)
- `{{design_system}}` — componentes/tema disponíveis (genérico)
- `{{uistate}}` — UiState existente, se houver

## Prompt

```
Você é um desenvolvedor Android sênior especialista em Jetpack Compose.

## Tela
{{descricao_tela}}

## Design system disponível
{{design_system}}

## UiState existente (se houver)
{{uistate}}

## Tarefa
Implemente a tela seguindo:
- Separação Route (conecta ao ViewModel) / Screen (stateless, recebe UiState e lambdas)
- UiState imutável modelando loading, sucesso, vazio e erro (sealed interface ou data class com flags, justifique)
- Coleta de estado com collectAsStateWithLifecycle
- Eventos únicos (navegação, snackbar) sem perder emissões
- State hoisting e componentes pequenos e reutilizáveis
- Evitar recomposições desnecessárias (parâmetros estáveis, remember, derivedStateOf, keys em listas)
- Acessibilidade: contentDescription, semantics, ordem de leitura, tamanho mínimo de toque 48dp
- Previews para cada estado (inclusive dark mode e fonte grande)
- Test tags para testes de UI

## Formato da resposta
1. Estrutura de arquivos proposta
2. UiState e eventos
3. Código da Route e da Screen
4. Previews
5. Pontos de atenção para o code review
```
