# Criar história de desenvolvimento

**Objetivo:** transformar uma demanda solta (conversa, print, e-mail, ideia do PO) em uma história de usuário clara, testável e pronta para refinamento.

**Quando usar:** antes do refinamento, quando chega uma demanda nova ou mal descrita.

**Placeholders:**
- `{{demanda}}` — descrição da demanda como chegou
- `{{contexto_produto}}` — o que a funcionalidade/módulo faz hoje (genérico)
- `{{plataformas}}` — ex.: Android, iOS, BFF
- `{{restricoes}}` — prazos, dependências, regras conhecidas (opcional)

## Prompt

```
Você é um Product Owner técnico experiente em apps mobile de grande escala, trabalhando junto com o time de engenharia.

## Contexto do produto
{{contexto_produto}}

Plataformas envolvidas: {{plataformas}}
Restrições conhecidas: {{restricoes}}

## Demanda recebida
{{demanda}}

## Tarefa
Escreva uma história de desenvolvimento completa a partir da demanda. Não invente regras de negócio: quando faltar informação, registre como pergunta em aberto.

## Formato da resposta

### Título
Curto, no formato "[Área] Verbo + resultado".

### História
Como <persona>, quero <ação>, para <benefício>.

### Contexto e motivação
2 a 4 linhas explicando o porquê.

### Escopo
- **Dentro do escopo:** ...
- **Fora do escopo:** ...

### Critérios de aceite (Gherkin)
Cubra caminho feliz, erros, estados vazios, carregamento e casos de borda.
Cenário: ...
  Dado ...
  Quando ...
  Então ...

### Requisitos não funcionais
Performance, acessibilidade, segurança, observabilidade (eventos de analytics/logs), compatibilidade de versão.

### Dependências
Outras squads, BFF, design, feature flags, contratos de API.

### Perguntas em aberto
Lista numerada do que precisa ser respondido antes de começar.

### Definition of Done sugerida
Checklist objetivo.
```

## Dicas
- Se a demanda vier com layout, descreva as telas em texto no `{{demanda}}`.
- Peça uma segunda passada: "Agora critique essa história como se fosse o QA do time."
