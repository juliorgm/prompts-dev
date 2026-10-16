# Payload do BFF → modelos

**Objetivo:** transformar um JSON de resposta em DTOs, modelos de domínio e mappers, com tratamento de nulos e valores inesperados.

**Quando usar:** ao integrar um endpoint novo ou quando o contrato muda.

> ⚠️ Antes de colar, troque dados reais por valores fictícios (nomes, números, IDs, valores monetários).

**Placeholders:**
- `{{json}}` — exemplo de payload (anonimizado)
- `{{lib_serializacao}}` — kotlinx.serialization, Moshi ou Gson
- `{{regras}}` — campos obrigatórios, enums conhecidos, formatos (opcional)

## Prompt

```
Você é um desenvolvedor Android sênior especialista em integração com APIs e Clean Architecture.

Biblioteca de serialização: {{lib_serializacao}}

## Payload
{{json}}

## Regras conhecidas
{{regras}}

## Tarefa
1. **DTOs** (camada de dados): espelham o JSON, campos anuláveis por padrão, anotações da lib, nomes em camelCase com mapeamento do nome original.
2. **Modelos de domínio**: só o que a aplicação usa, tipos ricos (enum, BigDecimal para valores monetários, tipos de data), não anuláveis quando a regra garantir.
3. **Mappers** DTO → domain como funções de extensão, com:
   - fallback para enums desconhecidos (ex.: UNKNOWN), sem crash
   - decisão explícita para campo obrigatório ausente (erro de domínio vs valor padrão), justificada
   - parsing seguro de datas e valores
4. **Testes dos mappers** cobrindo payload completo, mínimo, com nulos e com enum desconhecido.
5. **Dúvidas sobre o contrato** para levar ao time do BFF.

Não use Double/Float para dinheiro.
```
