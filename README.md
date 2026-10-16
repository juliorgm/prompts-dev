# prompts-dev

Biblioteca pessoal de prompts reutilizáveis para o dia a dia de desenvolvimento Android/Kotlin.

> ⚠️ **Regra de ouro:** este repositório contém apenas prompts **genéricos**. Nunca versione aqui código, payloads, nomes de módulos, endpoints, regras de negócio ou qualquer dado de cliente/empregador. O conteúdo real é colado **somente na hora de usar**, no lugar dos placeholders `{{...}}`.

## Como usar

1. Abra o prompt desejado aqui no GitHub.
2. Copie o bloco dentro de **Prompt**.
3. Substitua os placeholders `{{...}}` pelo seu contexto.
4. Cole na ferramenta de IA autorizada pelo seu ambiente de trabalho.

## Índice

### 📋 Refinamento
| Prompt | Para quê |
|---|---|
| [Criar história de desenvolvimento](prompts/refinamento/criar-historia.md) | Transformar uma demanda em história com critérios de aceite (Gherkin) |
| [Refinar e quebrar história](prompts/refinamento/refinar-historia.md) | Quebrar em tasks técnicas, levantar riscos e perguntas pro PO |
| [Estimar história](prompts/refinamento/estimar-historia.md) | Apoio para estimativa (pontos/complexidade) com justificativa |

### 💻 Código
| Prompt | Para quê |
|---|---|
| [Code review](prompts/codigo/code-review.md) | Review completo de PR Kotlin/Android com severidade |
| [Code review de branch (Copilot agent)](prompts/codigo/code-review-branch-copilot.md) | Copilot roda o `git diff` entre duas branches e faz o CR com limpeza |
| [Testes de ViewModel](prompts/codigo/testes-viewmodel.md) | Gerar testes unitários de ViewModel com Coroutines/Flow |
| [Testes de UseCase/Repository](prompts/codigo/testes-usecase-repository.md) | Testes das camadas de domínio e dados |
| [Refatoração](prompts/codigo/refatoracao.md) | Refatorar mantendo comportamento, passo a passo |
| [Tela em Jetpack Compose](prompts/codigo/tela-compose.md) | Criar/revisar tela Compose com estado, previews e acessibilidade |

### 🏛️ Arquitetura
| Prompt | Para quê |
|---|---|
| [Revisão de arquitetura](prompts/arquitetura/revisao-arquitetura.md) | Avaliar aderência a MVVM/Clean e modularização |
| [ADR](prompts/arquitetura/adr.md) | Registrar decisão de arquitetura |

### 🔌 BFF / Contratos
| Prompt | Para quê |
|---|---|
| [Payload → modelos](prompts/bff/payload-para-modelos.md) | Mapear JSON do BFF em DTO, domain e mappers |
| [Revisar contrato de API](prompts/bff/revisar-contrato.md) | Encontrar lacunas no contrato antes de implementar |

### 🐞 Bugs
| Prompt | Para quê |
|---|---|
| [Análise de stacktrace](prompts/bugs/analise-stacktrace.md) | Diagnosticar crash a partir do stacktrace |
| [Investigar bug](prompts/bugs/investigar-bug.md) | Hipóteses e plano de investigação para bug sem crash |

### 🚀 Release
| Prompt | Para quê |
|---|---|
| [Changelog e nota de versão](prompts/release/changelog.md) | Gerar changelog técnico e nota para negócio |
| [Checklist de release](prompts/release/checklist-release.md) | Checklist pré-release adaptado à entrega |

### 📝 Documentação e comunicação
| Prompt | Para quê |
|---|---|
| [Descrição de PR](prompts/documentacao/descricao-pr.md) | Escrever a descrição do PR a partir do diff |
| [Explicar código legado](prompts/documentacao/explicar-codigo.md) | Entender rapidamente um trecho desconhecido |
| [Mensagem para o time](prompts/documentacao/mensagem-time.md) | Comunicar impedimento, status ou decisão técnica |

## Criando um prompt novo

Use o [TEMPLATE.md](TEMPLATE.md) para manter o padrão.
