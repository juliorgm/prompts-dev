# Descrição de PR

**Onde:** Copilot.
**Uso:** escrever a descrição do PR a partir do diff.
**Troque:** `{{base}}`, `{{feature}}` e `{{historia}}` (link ou resumo).

## Prompt
```
Rode git diff --stat origin/{{base}}...origin/{{feature}} e leia o diff. História: {{historia}}.
Escreva a descrição do PR seguindo o template do repositório, se houver. Seções: O quê (2–3 linhas), Por quê, Como (decisões), Onde olhar com atenção, Como testar (passos, flags, massa), Checklist.
Seja direto, sem texto genérico.
```
