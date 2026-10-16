# Revisão de arquitetura

**Objetivo:** avaliar a arquitetura de um módulo ou feature e propor melhorias priorizadas.

**Quando usar:** antes de uma feature grande, em débito técnico recorrente ou ao assumir um módulo novo.

**Placeholders:**
- `{{estrutura}}` — árvore de pacotes/arquivos do módulo
- `{{fluxo}}` — descrição de um fluxo ponta a ponta (tela → API)
- `{{dores}}` — problemas sentidos pelo time (bugs recorrentes, lentidão para evoluir, testes difíceis)
- `{{codigo_amostra}}` — trechos representativos (opcional)

## Prompt

```
Você é um arquiteto Android especialista em apps modulares de grande escala (dezenas de módulos, centenas de devs), Clean Architecture e MVVM.

## Estrutura do módulo
{{estrutura}}

## Fluxo representativo
{{fluxo}}

## Dores do time
{{dores}}

## Código de amostra
{{codigo_amostra}}

## Tarefa
Avalie a arquitetura considerando:
- Separação de camadas e direção das dependências
- Fronteiras do módulo: API pública vs implementação, acoplamento com outros módulos
- Gerenciamento de estado e fluxo de dados (unidirecional?)
- Tratamento de erros entre camadas
- Testabilidade
- Injeção de dependência
- Navegação entre módulos
- Escalabilidade para novas features

## Formato da resposta
1. Diagnóstico: o que está bom, o que está ruim (com evidências)
2. Diagrama atual em texto (ou Mermaid)
3. Proposta de arquitetura-alvo (Mermaid)
4. Plano de migração incremental, priorizado por impacto/esforço
5. Riscos e o que NÃO vale a pena mudar agora
```
