# DatosIA — MCP server for Central America data

**Official public data for Central America and the Dominican Republic, down to the municipality, for AI assistants.**
*Datos públicos oficiales de Centroamérica y República Dominicana, hasta el municipio, para asistentes de IA.*

DatosIA connects Claude, ChatGPT, Cursor and any MCP client to thousands of indicators and records from
Guatemala, El Salvador, Honduras, Nicaragua, Costa Rica, Panama, Belize and the Dominican Republic:
census and population by municipality, prices (daily supermarket and hardware prices, basic basket),
public procurement and suppliers, trade and logistics, labour, banking, energy, crime and risk, health,
education, climate, laws and official gazettes, news and the people and organisations in it, research,
and live official sources. Every answer cites its source.

- Website: https://datosia.net (Spanish) · developer docs: https://datosmcp.com/docs
- MCP endpoint (remote, Streamable HTTP): `https://datosia.net/mcp`
- Auth: OAuth 2.1 (free account, sign in with your email) or an `x-api-key` header (free key at https://datosia.net/account)
- Price: free tier; paid plans for higher limits

## Connect

**Claude (claude.ai / Desktop):** Settings → Connectors → Add custom connector → `https://datosia.net/mcp`

**Claude Code:**
```bash
claude mcp add --transport http datosia https://datosia.net/mcp
```

**Cursor / VS Code / Cline / any client with remote MCP:**
```json
{
  "mcpServers": {
    "datosia": { "url": "https://datosia.net/mcp" }
  }
}
```

**Clients without remote support (stdio bridge):**
```json
{
  "mcpServers": {
    "datosia": { "command": "npx", "args": ["-y", "mcp-remote", "https://datosia.net/mcp"] }
  }
}
```

## Tools

| Tool | What it does |
|---|---|
| `search_data` | Ask in plain Spanish or English; returns numbers with sources, charts and maps |
| `find_indicators` / `describe_indicator` / `query_data` | Find and query indicators by place and period |
| `resolve_place` / `list_places` / `enrich_place` | Countries, departments, municipalities; a profile of any place |
| `search_prices` | Daily retail prices (supermarkets, hardware, electronics), price per kg/l/unit, changes |
| `find_suppliers` / `procurement_network` / `search_opportunities` | Public procurement: suppliers, buyers, contracts, open tenders |
| `find_certified_companies` | Certified companies and exporters |
| `search_news` / `entity_timeline` / `entity_network` | News, public figures and organisations, timelines and relationships |
| `search_legal` | Laws, decrees and official gazettes |
| `search_research` | Academic and policy research |
| `call_live_source` | Live APIs of datasets published on the marketplace |
| `convert_currency` / `calendar` | Exchange rates; holidays and official calendars |
| `browse_marketplace` / `get_marketplace_terms` / `draft_dataset` / `estimate_dataset_demand` / `list_data_requests` | Data marketplace: buy or publish datasets |
| `report_data_issue` | Report a wrong or missing number |

## Example questions

- ¿Dónde está más barato el arroz esta semana en Guatemala?
- Population and household income by municipality in Sacatepéquez
- ¿Quiénes son los principales proveedores de medicinas del Estado en Honduras?
- Homicide rate trend by department in El Salvador since 2015
- Imports of car batteries (HS 850710) into Guatemala by origin

## About

Built by [Hapi.vc](https://www.hapi.vc). Data comes from national statistics offices, central banks,
ministries, procurement portals and international bodies; each result links to its source.
Contact: hola@datosmcp.com
