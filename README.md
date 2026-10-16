# prompts-dev

Biblioteca pessoal de prompts reutilizáveis para o dia a dia de desenvolvimento Android/Kotlin.

> ⚠️ **Regra de ouro:** este repositório é público e contém apenas prompts **genéricos**. Nunca versione aqui código, payloads, nomes de módulos, endpoints, regras de negócio ou qualquer dado de cliente/empregador. O conteúdo real é colado **somente na hora de usar**, no lugar dos placeholders `{{...}}`.

## Como usar

- **Copilot** (prompts que mexem em código): são curtos e divididos em **partes**. Rode a Parte 1, leia a resposta e mande a Parte 2. Use `#file` em vez de colar código. Os que rodam `git` precisam do **modo Agent**.
- **StackSpot** (prompts que não mexem em código): são completos, em um único envio.

Troque os `{{...}}` pelo seu contexto antes de enviar.

## Índice

### 📋 Refinamento
| Prompt | Onde | Para quê |
|---|---|---|
| [Criar história](prompts/refinamento/criar-historia.md) | StackSpot | Demanda → história com critérios de aceite em Gherkin |
| [Refinar e quebrar história](prompts/refinamento/refinar-historia.md) | StackSpot | Tasks técnicas, riscos e perguntas para PO/Design/BFF |
| [Estimar história](prompts/refinamento/estimar-historia.md) | StackSpot | Apoio para estimativa com justificativa |

### 💻 Código
| Prompt | Onde | Para quê |
|---|---|---|
| [Code review (arquivo)](prompts/codigo/code-review.md) | Copilot · 3 partes | Bugs, arquitetura e testes faltando |
| [Code review de branch](prompts/codigo/code-review-branch-copilot.md) | Copilot Agent · 6 partes | Diff entre branches, relatório `.md` e aplicação aprovada |
| [Tagueamento item a item](prompts/codigo/tagueamento-item-a-item.md) | Copilot | Analytics e correções, um item por vez |
| [Testes de ViewModel](prompts/codigo/testes-viewmodel.md) | Copilot · 2 partes | Cenários e testes com Coroutines/Flow |
| [Testes de UseCase/Repository](prompts/codigo/testes-usecase-repository.md) | Copilot · 2 partes | Matriz de cenários e testes |
| [Refatoração](prompts/codigo/refatoracao.md) | Copilot · 3 partes | Refatorar sem mudar comportamento |
| [Tela em Compose](prompts/codigo/tela-compose.md) | Copilot · 3 partes | Estado, UI, previews e acessibilidade |

### 🏛️ Arquitetura
| Prompt | Onde | Para quê |
|---|---|---|
| [Revisão de arquitetura](prompts/arquitetura/revisao-arquitetura.md) | Copilot · 3 partes | Mapa, diagnóstico e plano para um módulo |
| [ADR](prompts/arquitetura/adr.md) | StackSpot | Registrar decisão técnica |

### 🔌 BFF / Contratos
| Prompt | Onde | Para quê |
|---|---|---|
| [Payload → modelos](prompts/bff/payload-para-modelos.md) | Copilot · 3 partes | DTO, domain, mappers e testes |
| [Revisar contrato](prompts/bff/revisar-contrato.md) | StackSpot | Lacunas no contrato antes de implementar |

### 🐞 Bugs
| Prompt | Onde | Para quê |
|---|---|---|
| [Análise de stacktrace](prompts/bugs/analise-stacktrace.md) | Copilot · 3 partes | Diagnóstico, reprodução e correção de crash |
| [Investigar bug](prompts/bugs/investigar-bug.md) | Copilot · 3 partes | Bug sem crash: caminho do dado e hipóteses |

### 🚀 Release
| Prompt | Onde | Para quê |
|---|---|---|
| [Changelog e nota de versão](prompts/release/changelog.md) | StackSpot | Changelog técnico e nota para negócio |
| [Checklist de release](prompts/release/checklist-release.md) | StackSpot | Checklist pré-release da entrega |

### 📝 Documentação e comunicação
| Prompt | Onde | Para quê |
|---|---|---|
| [Doc a partir do diff](prompts/documentacao/doc-a-partir-do-diff.md) | Copilot Agent · 3 partes | Documentação técnica da entrega em `.md` |
| [Descrição de PR](prompts/documentacao/descricao-pr.md) | Copilot | Descrição do PR a partir do diff |
| [Explicar código legado](prompts/documentacao/explicar-codigo.md) | Copilot · 2 partes | Entender e saber onde mexer |
| [Mensagem para o time](prompts/documentacao/mensagem-time.md) | StackSpot | Impedimento, status ou decisão técnica |

## Criando um prompt novo

Use o [TEMPLATE.md](TEMPLATE.md).
