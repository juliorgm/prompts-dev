# Documentação a partir do diff (Copilot agent)

**Objetivo:** fazer o Copilot ler o `git diff` entre duas branches e gerar uma documentação técnica da entrega em um arquivo `.md`: o que mudou, por quê, como funciona, fluxo, contratos, estados, como testar e riscos.

**Quando usar:** ao terminar uma feature ou correção, para registrar a entrega no repositório, anexar ao PR, passar contexto para o QA ou fazer handover para outro dev.

**Requisito:** Copilot Chat em **modo Agent** (VS Code ou Android Studio), para ele executar comandos e abrir arquivos. Sem modo agent, veja a seção *Alternativa* no fim.

**Placeholders:**
- `{{branch_base}}`: branch de destino (ex.: `develop`)
- `{{branch_feature}}`: branch com a entrega
- `{{contexto}}`: história, bug ou objetivo da entrega (cole o texto da história; opcional, mas melhora muito o "porquê")
- `{{publico}}`: quem vai ler (ex.: devs do time, QA, tech lead, novo integrante)
- `{{destino}}`: caminho do arquivo (ex.: `docs/features/`); se vazio, use `docs/features/`

## Prompt

```
Você é um desenvolvedor Android sênior e technical writer. Sua tarefa é gerar a documentação técnica de uma entrega a partir do diff entre duas branches. A documentação deve ser fiel ao código: descreva somente o que está no diff e nos arquivos relacionados. Quando não souber o motivo de algo, não invente: registre como pergunta.

## Parâmetros
- Branch base: {{branch_base}}
- Branch da entrega: {{branch_feature}}
- Contexto da entrega: {{contexto}}
- Público: {{publico}}
- Pasta de destino: {{destino}}

## Passo 1 — Coletar o diff (somente leitura)
Execute no terminal. NÃO altere nenhum arquivo do projeto e NÃO faça checkout de outra branch. A única escrita permitida é o arquivo de documentação do Passo 3.

git fetch origin
git log --oneline origin/{{branch_base}}..origin/{{branch_feature}}
git diff --stat origin/{{branch_base}}...origin/{{branch_feature}}
git diff --name-status origin/{{branch_base}}...origin/{{branch_feature}}
git diff origin/{{branch_base}}...origin/{{branch_feature}}

Regras:
- Use três pontos (...) para pegar só o que a entrega introduziu.
- Use as mensagens de commit como pista do "porquê", mas confirme no código.
- Abra os arquivos completos e as classes vizinhas quando o diff não der contexto suficiente para explicar o fluxo.
- Ignore arquivos gerados (build/, generated/).

## Passo 2 — Entender a entrega
Antes de escrever, monte para você:
1. O objetivo da entrega em uma frase.
2. O fluxo ponta a ponta: tela → ViewModel → UseCase → Repository → DataSource/API (e o caminho de volta).
3. O que é novo, o que foi alterado e o que foi removido.
4. Contratos: endpoints, DTOs, modelos de domínio, mapeamentos, navegação/deeplinks.
5. Estados de tela, regras de negócio, tratamento de erro.
6. Configurações: feature flags, remote config, permissões, dependências Gradle.
7. Observabilidade: eventos de analytics, logs.
8. Testes adicionados ou alterados.

## Passo 3 — Gerar o arquivo de documentação
Crie o arquivo Markdown:

{{destino}}/<nome-curto-da-entrega>.md

(nome em kebab-case derivado do objetivo, ex.: `edicao-de-perfil.md`; crie a pasta se não existir).
Escreva em português, com linguagem adequada para {{publico}}. Seja objetivo: prefira tabelas e listas a parágrafos longos.

Estrutura obrigatória (omita uma seção só se ela realmente não se aplicar, e diga "Não se aplica"):

# <Título da entrega>
> Branch: `{{branch_feature}}` → `{{branch_base}}` · Commits: <quantidade> · Atualizado em: <AAAA-MM-DD> · Commit: <hash curto>

## 1. Resumo
3 a 5 linhas: o que foi entregue, para quem e por quê.

## 2. Contexto
O problema ou necessidade que motivou a entrega (a partir do contexto informado e dos commits).

## 3. O que mudou
| Tipo (novo/alterado/removido) | Arquivo ou componente | Camada | Descrição |

## 4. Arquitetura e fluxo
- Diagrama Mermaid (`sequenceDiagram` ou `flowchart`) do fluxo principal.
- Explicação curta de cada passo e da responsabilidade de cada classe envolvida.
- Decisões técnicas relevantes visíveis no código (ex.: estratégia de cache, tratamento de erro, uso de Flow).

## 5. Contratos e dados
- Endpoints usados (método, rota genérica, request/response resumidos)
- DTOs e modelos de domínio criados ou alterados, com os campos principais
- Regras de mapeamento relevantes (nulos, enums, valores monetários, datas)

## 6. Estados e comportamento da tela
| Estado | Quando acontece | O que o usuário vê |
Inclua loading, sucesso, vazio e cada tipo de erro.

## 7. Regras de negócio
Lista numerada das regras implementadas, cada uma com o local no código (`arquivo:linha`).

## 8. Configuração
Feature flags (nome, valor padrão, efeito), remote config, permissões, dependências novas, migrações.

## 9. Observabilidade
Eventos de analytics e logs adicionados (nome, quando dispara, parâmetros).

## 10. Testes
- Testes automatizados adicionados/alterados e o que cobrem
- Lacunas de cobertura identificadas

## 11. Como testar manualmente
Passo a passo para o QA, incluindo pré-condições, massa de dados, flags e cenários de erro.

## 12. Riscos, limitações e pontos de atenção
Impactos em outros fluxos/módulos, compatibilidade com versões anteriores, débitos técnicos deixados.

## 13. Perguntas em aberto
Tudo o que não deu para concluir só pelo código.

Regras de escrita:
- Não copie blocos grandes de código; cite `arquivo:linha` e, se necessário, um trecho curto.
- Não inclua segredos, tokens, URLs de ambiente ou dados reais de usuários. Use valores fictícios nos exemplos.
- Toda afirmação sobre comportamento deve ter base no código. Se for dedução, sinalize com "(provável)".

## Passo 4 — Finalizar
- No chat, mostre só o resumo (seção 1), a lista de perguntas em aberto e o caminho do arquivo gerado.
- Não faça commit nem push. Pergunte se devo ajustar algo ou se a documentação deve ir junto com a branch.
```

## Alternativa (sem modo agent)

Gere o diff e anexe ao chat:

```bash
git fetch origin
git log --oneline origin/develop..origin/minha-branch > commits.txt
git diff origin/develop...origin/minha-branch > entrega.diff
```

Anexe os dois arquivos (`#file:entrega.diff` e `#file:commits.txt` no VS Code) e use o prompt trocando o **Passo 1** por: *"O diff e os commits estão nos arquivos anexados."* No Passo 3, peça a documentação como resposta no chat em vez de arquivo.

## Dicas
- Combine com o [Code review de branch](../codigo/code-review-branch-copilot.md): primeiro o review, depois a doc da versão final.
- Para o PR, peça depois: *"Resuma a doc em uma descrição de PR com no máximo 20 linhas."*
- Para o QA, peça: *"Gere só as seções 6, 8 e 11 em um arquivo separado para o QA."*
- Se o time tiver um template de documentação, cole no prompt e diga: *"Siga este template em vez da estrutura acima."*
