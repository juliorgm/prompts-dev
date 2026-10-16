# Documentação a partir do diff

**Onde:** Copilot (modo Agent).
**Uso:** gerar a documentação técnica de uma entrega em `.md`.
**Troque:** `{{base}}`, `{{feature}}` e `{{contexto}}` (texto da história; opcional, mas ajuda no "porquê").

## Parte 1 — Entender
```
Sem alterar arquivos, rode: git fetch origin && git log --oneline origin/{{base}}..origin/{{feature}} && git diff --stat origin/{{base}}...origin/{{feature}}
Leia o diff completo. Contexto: {{contexto}}. Resuma o objetivo em 1 frase e o fluxo tela → ViewModel → UseCase → Repository → API.
```

## Parte 2 — Rascunho técnico
```
Liste: o que mudou (tabela novo/alterado/removido por camada), contratos e DTOs, estados da tela, regras de negócio com arquivo:linha, flags, eventos de analytics e testes. Só o que está no código; dedução marque "(provável)".
```

## Parte 3 — Gerar arquivo
```
Grave em docs/features/<nome-da-entrega>.md com: Resumo, Contexto, O que mudou, Fluxo (Mermaid), Contratos, Estados, Regras, Configuração, Analytics, Testes, Como testar (passo a passo para QA), Riscos e Perguntas em aberto.
Sem segredos nem dados reais. Não faça commit. No chat, mostre só o resumo e o caminho.
```
