# Code review de branch (Copilot agent)

**Objetivo:** fazer o Copilot rodar o `git diff` entre duas branches e entregar um code review completo (riscos de crash, arquitetura, padronização, simplificação, antipatterns e limpeza de arquivos/código desnecessário), gravado em um arquivo `.md` no projeto com checklist de todas as mudanças sugeridas.

**Quando usar:** antes de abrir o PR (auto-review) ou ao revisar a branch de alguém.

**Requisito:** Copilot Chat em **modo Agent** (VS Code ou Android Studio), para ele conseguir executar comandos no terminal e abrir arquivos. Sem modo agent, veja a seção *Alternativa* no fim.

**Placeholders:**
- `{{branch_base}}` — branch de destino do merge (ex.: `develop`, `main`)
- `{{branch_feature}}` — branch a ser revisada
- `{{padroes_time}}` — convenções do time (opcional; apague a linha se não usar)

## Prompt

```
Você é um revisor de código Android sênior (Kotlin, MVVM, Clean Architecture, Coroutines/Flow, Jetpack Compose, injeção de dependência, testes) em um app modular de grande escala. Faça o code review da branch abaixo antes do merge. Seja rigoroso e pragmático: aponte apenas problemas reais, sempre com evidência no código. Nada de elogios genéricos.

## Parâmetros
- Branch base: {{branch_base}}
- Branch da feature: {{branch_feature}}
- Padrões do time: {{padroes_time}}

## Passo 1 — Coletar o diff (somente leitura)
Execute no terminal. Nesta etapa NÃO altere, crie ou exclua nenhum arquivo e NÃO faça checkout de outra branch. A única exceção em todo o review é o arquivo de relatório do Passo 3.

git fetch origin
git diff --stat origin/{{branch_base}}...origin/{{branch_feature}}
git diff --name-status origin/{{branch_base}}...origin/{{branch_feature}}
git diff origin/{{branch_base}}...origin/{{branch_feature}}

Regras:
- Use três pontos (...) para comparar com o merge-base, ou seja, só o que a feature introduziu.
- Se o diff for grande, revise arquivo por arquivo com `git diff origin/{{branch_base}}...origin/{{branch_feature}} -- <arquivo>`.
- Quando o diff não der contexto suficiente, abra o arquivo completo e as classes que ele usa.
- Não revise arquivos gerados (build/, generated/), mas sinalize se foram commitados por engano.

## Passo 2 — Analisar
Avalie cada arquivo alterado nos eixos abaixo.

1. **Riscos de crash**
   - `!!`, `lateinit` possivelmente não inicializado, cast com `as` sem `as?`
   - `first()`, `single()`, `[index]`, `get()` em coleção possivelmente vazia
   - parsing sem proteção: `toInt()`, datas, `enumValueOf`/`valueOf`, JSON
   - platform types vindos de Java tratados como não nulos
   - acesso a view/binding de Fragment após `onDestroyView`; `requireContext()`/`requireActivity()` em callback assíncrono
   - `IllegalStateException` de navegação duplicada ou transação após `onSaveInstanceState`
   - exceção não tratada em coroutine (launch sem tratamento), `CancellationException` engolida por `catch (e: Exception)`
   - `TransactionTooLargeException` (Bundle/Parcelable grande, SavedStateHandle)
   - I/O ou rede na main thread (ANR)
   - classes serializadas/usadas por reflexão sem regra de R8/ProGuard
   - novas permissões, componentes ou deeplinks no Manifest sem tratamento

2. **Arquitetura**
   - direção das dependências: UI → ViewModel → UseCase → Repository → DataSource
   - regra de negócio na UI (Composable, Fragment, Activity) ou no Repository
   - ViewModel com referência a Context, View, Activity ou NavController
   - DTO vazando para domain/UI; falta de mapper
   - acoplamento indevido entre módulos; uso de implementação em vez da API pública do módulo
   - responsabilidades misturadas, classes "Deus"

3. **Concorrência**
   - `GlobalScope`, `runBlocking` em código de produção, escopo errado
   - dispatcher fixo em vez de injetado (dificulta teste)
   - Flow coletado sem respeitar lifecycle (`repeatOnLifecycle`, `collectAsStateWithLifecycle`)
   - `MutableStateFlow`/`MutableLiveData` exposto publicamente
   - StateFlow usado para evento único (ou SharedFlow perdendo evento)
   - condições de corrida, jobs duplicados a cada chamada

4. **Estado de UI e Compose**
   - UiState mutável ou incompleto (sem loading/erro/vazio)
   - recomposições desnecessárias: parâmetros instáveis, lambdas recriadas, falta de `remember`/`derivedStateOf`, listas sem `key`
   - side effects fora de `LaunchedEffect`/`DisposableEffect`
   - estado perdido em rotação ou process death
   - acessibilidade: `contentDescription`, semântica, área de toque

5. **Padronização**
   - nomenclatura (classes, funções, pacotes, recursos) e consistência com o restante do módulo
   - strings, cores e dimensões hardcoded em vez de recursos/tema
   - magic numbers, parâmetros booleanos que mudam comportamento
   - formatação e regras do lint/detekt/ktlint do projeto
   - {{padroes_time}}

6. **Simplificação**
   - código que pode usar recursos idiomáticos de Kotlin (scope functions com moderação, `when`, extension functions, `sealed`, `data class`, stdlib de coleções)
   - lógica duplicada que pode ser extraída
   - abstrações sem uso real (interface com uma única implementação sem motivo, camadas que só repassam)
   - condicionais aninhadas que podem virar early return
   - funções longas que devem ser quebradas

7. **Antipatterns**
   - `catch (e: Exception)` genérico engolindo erro ou sem log
   - singletons com estado mutável ou guardando Context (memory leak)
   - herança onde composição resolveria
   - classes utilitárias estáticas para lógica de negócio
   - copy-paste entre telas/módulos
   - feature flag morta ou lógica de flag espalhada

8. **Limpeza (arquivos e código desnecessários)**
   - imports não usados, código comentado, `println`/`Log.d` de debug, TODO sem ticket
   - classes, funções, parâmetros, recursos (strings, drawables, layouts, dimens) e dependências Gradle sem uso
   - testes com `@Ignore` ou vazios
   - arquivos commitados por engano: `.idea/`, `local.properties`, `build/`, `.DS_Store`, APK/AAB, arquivos temporários
   - IMPORTANTE: antes de afirmar que algo não é usado, procure referências no projeto inteiro (todos os módulos), incluindo XML, Manifest, navegação, reflexão, serialização e deeplinks. Informe a busca que você fez como evidência.

9. **Segurança e dados sensíveis**
   - dados pessoais, tokens ou dados financeiros em logs, analytics ou crash reports
   - armazenamento local sem criptografia, `exported=true` sem necessidade, WebView inseguro
   - segredos ou URLs de ambiente hardcoded

10. **Performance**
    - alocações e cálculos pesados em composição ou `onBindViewHolder`
    - chamadas repetidas à API/banco, falta de cache ou de debounce
    - imagens sem dimensionamento

11. **Testes**
    - código novo sem teste; cenários de erro e borda descobertos
    - testes frágeis (dependem de ordem, tempo real, `Thread.sleep`)
    - uso incorreto de dispatchers de teste

12. **Build e dependências**
    - dependências novas ou atualizadas: necessidade, versão, impacto no tamanho do app
    - mudanças em Gradle, versionCode/versionName, regras de R8/ProGuard

## Passo 3 — Relatório em arquivo Markdown
Grave o relatório completo em um arquivo Markdown na raiz do projeto:

code-review/CR_<branch_feature>_<AAAA-MM-DD>.md

(troque "/" do nome da branch por "-"; crie a pasta code-review/ se não existir).
Para o relatório não ir para o repositório por engano, adicione a linha `code-review/` ao arquivo `.git/info/exclude` (ignore local, não altera o .gitignore do time) se ela ainda não estiver lá.

No chat, mostre só o veredito, o painel de severidade e o caminho do arquivo gerado.

O arquivo deve ser escrito em português e começar com um cabeçalho:
# Code Review — <branch_feature>
- Base: <branch_base> | Data: <AAAA-MM-DD> | Commit analisado: <hash curto da feature>

Em seguida, siga este formato:

### Veredito
Aprovar / Aprovar com ajustes / Solicitar mudanças — com o motivo principal em 2 linhas.

### Resumo do diff
Arquivos alterados, linhas +/-, e em 3 linhas o que a branch faz.

### Painel
| Severidade | Quantidade |
|---|---|
| 🔴 Bloqueante (crash, bug, segurança, quebra de arquitetura) | |
| 🟠 Importante | |
| 🟡 Sugestão | |
| 🔵 Nitpick | |

### Achados
Ordenados do mais grave para o menos grave. Cada achado começa com uma caixa de seleção para acompanhar a aplicação, no formato `#### - [ ] CR-01 — <título curto>`, seguido de:
- **ID:** CR-01, CR-02...
- **Severidade e categoria** (ex.: 🔴 Crash)
- **Local:** `arquivo:linha`
- **Problema:** o que está errado
- **Risco:** o que pode acontecer em produção
- **Correção:** como resolver, com código antes/depois quando ajudar

### Candidatos a limpeza/exclusão
| Aplicado | ID | Arquivo ou trecho | Motivo | Evidência (busca feita) | Seguro excluir? (sim/verificar) |
Use IDs LP-01, LP-02... e a coluna "Aplicado" com ⬜ (pendente) ou ✅ (aplicado).

### Plano de ação
Checklist único com todos os IDs (CR e LP) na ordem recomendada de aplicação, para eu marcar o que aprovo:
- [ ] CR-01 — <resumo em uma linha>
- [ ] LP-01 — <resumo em uma linha>

### Simplificações e melhorias
Mudanças que não são bugs mas deixam o código mais simples, legível ou alinhado ao padrão.

### Testes faltando
Cenários que deveriam ser cobertos.

### Perguntas ao autor
Pontos em que você não tem certeza; não transforme dúvida em achado.

## Passo 4 — Aplicar correções (somente com minha aprovação)
Não edite nem exclua nenhum arquivo do código até eu responder. Ao fim, pergunte quais IDs devo aplicar (posso responder no chat ou marcando `[x]` no Plano de ação do arquivo).
Quando eu aprovar:
- aplique apenas os IDs aprovados, um por vez, mostrando o que mudou
- a cada item aplicado, atualize o arquivo de relatório: marque `[x]` no achado e no Plano de ação (ou ✅ na tabela de limpeza) e acrescente uma linha "Aplicado em: <arquivos alterados>"
- ao final, acrescente ao relatório uma seção "Resultado da aplicação" com o resultado do build, testes e lint
- para exclusões, confirme de novo a busca por referências antes de remover
- depois rode o build, os testes unitários e o lint do módulo afetado e reporte o resultado
- não faça commit, push, rebase, reset ou checkout sem eu pedir explicitamente
```

## Alternativa (sem modo agent)

Gere o diff você mesmo e anexe ao chat:

```bash
git fetch origin
git diff origin/develop...origin/minha-branch > review.diff
```

No chat, anexe o arquivo (`#file:review.diff` no VS Code ou arrastando para o chat) e use o prompt acima trocando o **Passo 1** por: *"O diff está no arquivo anexado. Abra os arquivos completos do projeto quando precisar de contexto."*

## Dicas
- Branch muito grande: peça *"Revise só os arquivos da camada de dados agora"* e depois continue por camada.
- Para colar no PR: *"Reescreva os achados 🔴 e 🟠 como comentários curtos e educados, um por arquivo:linha."*
- Se o time tiver checklist de PR, cole no `{{padroes_time}}`.
- Para branch local ainda não enviada, troque `origin/{{branch_feature}}` por `{{branch_feature}}`.
