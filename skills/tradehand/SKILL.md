---
name: tradehand
description: Browse and book local UK tradespeople on Tradehand. Use when looking up UK trades, public listings, or preparing a quote to continue on Tradehand.
---

Use Tradehand MCP at `https://tradehand.com/api/mcp` over Streamable HTTP. UK only.

Public tools:

- `browse_trades`
- `search_traders`
- `get_trader`
- `get_service_options`
- `prepare_instant_quote`
- `get_page_markdown`
- `get_agent_discovery`
- `read_okf_concept`

Browse public listings and prepare a quote. `prepare_instant_quote` checks the facts; it does not submit, text, charge, or assign a trader. If the user names a listing, ask whether they want that trader preferred or exclusive. Opening a profile is not exclusivity.

Signed-in booking and quote decisions continue on Tradehand. Never say an appointment is booked or a payment is complete unless the MCP response proves it. A prepared quote or a matched trader is not a booked appointment. Checkout, if shown, is due until Tradehand records payment.

Prices and assignment come from tool results. Do not invent them.
