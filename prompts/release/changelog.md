# Changelog e nota de versão

**Objetivo:** gerar o changelog técnico e uma nota de versão em linguagem de negócio a partir dos commits/PRs.

**Quando usar:** no fechamento de uma versão do módulo.

**Placeholders:**
- `{{commits}}` — lista de commits ou títulos de PRs desde a última versão
- `{{versao}}` — número da versão
- `{{publico_nota}}` — quem lê a nota (PO, QA, outras squads, release manager)

## Prompt

```
Você é um desenvolvedor responsável pela release de um módulo de um app mobile.

Versão: {{versao}}

## Commits / PRs
{{commits}}

## Tarefa
Gere dois textos:

### 1. Changelog técnico (formato Keep a Changelog)
Seções: Adicionado, Alterado, Corrigido, Removido, Segurança.
Agrupe commits relacionados, ignore commits triviais (formatação, merge), mantenha as referências de história/PR.

### 2. Nota de versão para {{publico_nota}}
Linguagem não técnica, focada no impacto para o usuário e para o negócio. Máximo de 10 linhas. Destaque feature flags, riscos conhecidos e o que o QA deve priorizar.

Se algum commit for ambíguo, liste-o no final como "precisa de confirmação".
```
