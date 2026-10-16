# Payload do BFF → modelos

**Onde:** Copilot.
**Uso:** criar DTO, domain e mappers para um endpoint novo ou alterado.
**Troque:** `{{json}}` = payload de exemplo (troque dados reais por fictícios).

## Parte 1 — DTO e domain
```
Payload: {{json}}
Crie os DTOs (campos anuláveis, anotações da lib de serialização do projeto) e os modelos de domínio (tipos ricos, BigDecimal para dinheiro, enums). Siga o padrão de um DTO existente no módulo.
```

## Parte 2 — Mappers
```
Crie os mappers DTO → domain como extension functions. Enum desconhecido vira UNKNOWN; para campo obrigatório ausente, diga se lança erro ou usa padrão e por quê.
```

## Parte 3 — Testes e dúvidas
```
Escreva testes dos mappers (payload completo, mínimo, com nulos, enum desconhecido) e liste dúvidas de contrato para o BFF.
```
