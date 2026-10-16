# Tagueamento e correções item a item

**Objetivo:** implementar o tagueamento (analytics) de uma feature e as correções pendentes, conferindo um item por vez, arquivo por arquivo.

**Placeholders:** `{{lista}}` (tags da especificação e correções), `{{arquivos}}` (arquivos da feature)

## Prompt

```
Vou te passar a lista de tags e correções: {{lista}}. Arquivos da feature: {{arquivos}}.
Siga o padrão de tagueamento que já existe no projeto (procure um exemplo antes de começar).
Trabalhe UM item por vez: diga o arquivo, a linha e o evento/parâmetros (ou a correção), e mostre o código antes/depois.
Confira se o evento dispara uma única vez, no momento certo, com os nomes e parâmetros exatamente como na especificação.
Não edite nada até eu responder "ok"; depois aplique, marque o item como ✅ e só então passe para o próximo.
Ao final, mostre a tabela: | Item | Arquivo:linha | Status | Observação |.
```
