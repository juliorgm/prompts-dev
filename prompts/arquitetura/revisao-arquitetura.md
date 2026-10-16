# Revisão de arquitetura do módulo

**Onde:** Copilot (lê o projeto).
**Uso:** avaliar um módulo antes de uma feature grande ou ao assumir um módulo novo.
**Troque:** `{{modulo}}` = pasta do módulo; `{{dores}}` = problemas sentidos pelo time.

## Parte 1 — Mapa
```
Analise o módulo {{modulo}}. Mostre a estrutura de pacotes e um diagrama Mermaid do fluxo principal (tela → ViewModel → UseCase → Repository → API).
```

## Parte 2 — Diagnóstico
```
Avalie: direção das dependências, acoplamento com outros módulos, estado de UI, tratamento de erro entre camadas, DI e testabilidade. Dores do time: {{dores}}.
Liste o que está bom e o que está ruim, sempre com arquivo de exemplo.
```

## Parte 3 — Plano
```
Proponha melhorias incrementais em tabela: | Melhoria | Impacto | Esforço | Risco |. Diga também o que NÃO vale mudar agora.
```
