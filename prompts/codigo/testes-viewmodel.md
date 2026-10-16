# Testes de ViewModel

**Objetivo:** gerar testes unitários completos para um ViewModel com Coroutines e Flow.

**Quando usar:** ao criar ou alterar um ViewModel.

**Placeholders:**
- `{{viewmodel}}` — código do ViewModel
- `{{dependencias}}` — interfaces dos UseCases/Repositories que ele usa
- `{{stack_testes}}` — ex.: JUnit4/5, MockK ou fakes, Turbine, kotlinx-coroutines-test, Truth/AssertJ

## Prompt

```
Você é um desenvolvedor Android sênior especialista em testes.

Stack de testes: {{stack_testes}}

## ViewModel
{{viewmodel}}

## Dependências
{{dependencias}}

## Tarefa
Escreva a classe de testes unitários do ViewModel.

Requisitos:
- Usar StandardTestDispatcher/UnconfinedTestDispatcher com Dispatchers.setMain e um MainDispatcherRule (inclua a rule se não existir).
- Testar emissões de StateFlow/Flow com Turbine (ou equivalente da stack).
- Preferir fakes a mocks quando a dependência for simples; usar mocks quando precisar verificar interação.
- Cobrir: estado inicial, caminho feliz, cada tipo de erro, estado vazio, loading, eventos únicos (navegação, toast), cancelamento e chamadas repetidas.
- Nomear no padrão `given_when_then` ou "`quando X, então Y`" com backticks.
- Estrutura Arrange / Act / Assert em cada teste.
- Não testar detalhes de implementação privados.

## Formato da resposta
1. Lista dos cenários que serão testados.
2. Código completo da classe de teste (e fakes/rules auxiliares).
3. Cenários que não dá para testar unitariamente e como cobri-los.
```
