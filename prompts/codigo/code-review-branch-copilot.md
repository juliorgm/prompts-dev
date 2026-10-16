# Code review de branch

**Onde:** Copilot (modo Agent).
**Uso:** revisar tudo o que uma branch mudou antes do merge, com relatório em `.md`.
**Troque:** `{{base}}` (ex.: develop), `{{feature}}` (sua branch) e, na Parte 6, `{{ids}}` (ex.: CR-01, CR-03, LP-02).

## Parte 1 — Diff
```
Sem alterar nenhum arquivo, rode: git fetch origin && git diff --stat origin/{{base}}...origin/{{feature}}
Depois leia o diff completo arquivo por arquivo. Resuma em 5 linhas o que a branch faz e liste os arquivos por camada.
```

## Parte 2 — Crash e bugs
```
Revise o diff procurando risco de crash e bugs: !!, lateinit, casts, first()/[i] em lista vazia, parsing, binding após onDestroyView, requireContext em callback, exceção em coroutine, CancellationException engolida, trabalho na main thread, R8 em classes serializadas.
Para cada achado: ID (CR-01...), severidade 🔴🟠🟡, arquivo:linha, problema e correção. Não invente.
```

## Parte 3 — Arquitetura e padrão
```
Continue os IDs. Revise: camadas (UI→VM→UseCase→Repo), ViewModel com Context, DTO vazando, GlobalScope/runBlocking, Mutable*Flow público, catch genérico, hardcoded, nomes, duplicação, código que pode ser simplificado.
```

## Parte 4 — Limpeza
```
Liste candidatos a exclusão (IDs LP-01...): imports e código mortos, logs de debug, TODO sem ticket, recursos/classes/dependências sem uso, arquivos commitados por engano.
Antes de afirmar que algo não é usado, busque referências em todos os módulos e diga a busca feita.
```

## Parte 5 — Relatório
```
Grave tudo em code-review/CR_{{feature}}_<data>.md (troque / por -) e adicione code-review/ ao .git/info/exclude.
Estrutura: veredito, painel por severidade, achados com "- [ ]", tabela de limpeza e um Plano de ação em checklist.
No chat, mostre só o veredito e o caminho do arquivo.
```

## Parte 6 — Aplicar
```
Aplique só os IDs: {{ids}}. Um por vez, mostrando o antes/depois. Marque [x] no relatório.
No fim rode build, testes e lint do módulo. Não faça commit nem push.
```
