# Testes de UseCase / Repository

**Objetivo:** gerar testes das camadas de domínio e dados, incluindo mapeamento e tratamento de erro.

**Quando usar:** ao criar ou alterar UseCases, Repositories, DataSources ou mappers.

**Placeholders:**
- `{{codigo}}` — classe(s) a testar
- `{{dependencias}}` — interfaces usadas
- `{{stack_testes}}` — JUnit, MockK/fakes, coroutines-test etc.

## Prompt

```
Você é um desenvolvedor Android sênior especialista em testes de domínio e dados.

Stack de testes: {{stack_testes}}

## Código
{{codigo}}

## Dependências
{{dependencias}}

## Tarefa
Escreva os testes unitários cobrindo:
- Regras de negócio do UseCase (cada ramo de decisão)
- Mapeamento DTO → domain: campos obrigatórios, opcionais nulos, enums desconhecidos, listas vazias, formatos de data/valor
- Tratamento de erro: HTTP 4xx/5xx, timeout, sem conexão, payload inválido; como cada erro é convertido para o domínio
- Estratégia de cache (se houver): hit, miss, expiração, fonte de verdade
- Concorrência: chamadas simultâneas, cancelamento

## Formato da resposta
1. Matriz de cenários (tabela: cenário | entrada | resultado esperado)
2. Código completo dos testes
3. Builders/fixtures de dados de teste reutilizáveis
```
