---
name: contas_cemig_download-mcp
description: Skill da REST API do Cemig: Download de Contas na MCP.AI: 1 endpoint em /api/contas_cemig_download. Cemig: Download de Contas, consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Cemig: Download de Contas — REST API skill

Você tem acesso à **Cemig: Download de Contas** REST API na MCP.AI.

> Cemig: Download de Contas, consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago.

## Base URL

```
https://api.mcp.ai/api/contas_cemig_download
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/contas_cemig_download/consultar \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"senha":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/contas_cemig_download/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (1)

#### `contas_cemig_download_consultar`

Cemig: Download de Contas, consulta em fonte oficial. _(POST /api/contas_cemig_download/consultar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `email` | string | Não | Parâmetro de consulta "email". |
| `cpf` | string | Não | Parâmetro de consulta "cpf". |
| `cnpj` | string | Não | Parâmetro de consulta "cnpj". |
| `senha` | string | Sim | Parâmetro de consulta "senha". |
| `numero_instalacao` | string | Não | Parâmetro de consulta "numero_instalacao". |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_contas_cemig_download` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
