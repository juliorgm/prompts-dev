# Tela em Jetpack Compose

**Onde:** Copilot.
**Uso:** criar ou migrar uma tela para Compose.
**Troque:** `{{tela}}` = descrição da tela (componentes, estados, interações).

## Parte 1 — Estado
```
Tela: {{tela}}. Proponha o UiState imutável (loading, sucesso, vazio, erro) e os eventos únicos (navegação, snackbar). Só o modelo, sem UI.
```

## Parte 2 — UI
```
Implemente Route (conecta ao ViewModel com collectAsStateWithLifecycle) e Screen stateless (recebe UiState e lambdas). Use o design system do projeto e componentes pequenos.
```

## Parte 3 — Qualidade
```
Adicione previews de cada estado (incluindo dark e fonte grande), contentDescription/semantics, área de toque de 48dp e testTags. Aponte riscos de recomposição.
```
