# Revisar contrato de API

**Objetivo:** encontrar lacunas e ambiguidades em um contrato de API antes de começar a implementar.

**Quando usar:** quando o BFF/backend compartilha o contrato (Swagger, exemplo de JSON, documento).

**Placeholders:**
- `{{contrato}}` — especificação ou exemplos de request/response (anonimizados)
- `{{necessidade_tela}}` — o que a tela/feature precisa exibir e fazer

## Prompt

```
Você é um desenvolvedor mobile sênior revisando um contrato de API antes da implementação.

## O que a tela precisa
{{necessidade_tela}}

## Contrato
{{contrato}}

## Tarefa
Analise o contrato e aponte:
1. **Cobertura:** a tela consegue ser montada só com esses dados? O que falta?
2. **Estados:** como o contrato representa vazio, erro de negócio, erro técnico, item bloqueado/indisponível?
3. **Erros:** códigos HTTP e códigos de negócio estão definidos? Há mensagem para o usuário ou só técnica?
4. **Tipos e formatos:** datas (timezone), valores monetários (centavos? string?), enums documentados, campos opcionais.
5. **Evolução:** o mobile quebra se aparecer um enum novo ou um campo for removido? Há versionamento?
6. **Performance:** paginação, tamanho do payload, chamadas encadeadas desnecessárias.
7. **Segurança:** dados sensíveis expostos além do necessário, mascaramento.
8. **Lógica no cliente:** regras de negócio que deveriam estar no BFF.

## Formato da resposta
Tabela: | # | Ponto | Tipo (lacuna/risco/sugestão) | Pergunta para o BFF |
Depois, uma mensagem curta e cordial pronta para enviar ao time do BFF com as perguntas.
```
