---
name: tradehand
description: Browse UK trades and public Tradehand listings, then continue an instant quote on Tradehand.
---

Use Tradehand MCP at `https://tradehand.com/api/mcp` over Streamable HTTP.

- Public journey tools: `browse_trades`, `search_traders`, `get_trader`, `get_service_options`, `prepare_instant_quote`.
- Also listed: `get_page_markdown`, `get_agent_discovery`, `read_okf_concept` (site reading, not quoting).
- Linked tools: `get_customer_access`, `list_my_jobs`, `get_job`, `prepare_booking`; with write: `submit_instant_quote`, `prepare_quote_decision`, `confirm_quote_decision`. With write: `confirm_booking` books a slot from `prepare_booking` (pass its `revision` as `expectedRevision`). The first call returns the live total; show it and repeat with that `confirmedTotalAmount` only after the customer says yes. That books the visit and returns `checkoutUrl` with `payment.state: "due"`. With write and `tradehand:checkout:create`: `start_job_checkout` returns the payment link for a job with money due. A link is never payment; report paid only when `get_job` says so.
- Instant quote works before a trader is assigned. Matching taken is not an appointment.
- Named listing intent must be `preferred` or `exclusive`. A profile click is not exclusivity.
- Anonymous `prepare_instant_quote` validates only. Linked write scope may persist a reviewable preparation; it still does not text, charge, or assign.
- `submit_instant_quote` takes `preparationToken`, `expectedRevision`, `idempotencyKey`, and `confirmationReference` only. Never pass session tokens, contact ids, or `confirmed: true`. First-party continue is `/instant-quote?prep=` — same customer reviews stored facts and sends.
- Prices and assignment come from tool results. Never invent them.
- This package is the Cursor / Grok Bots Agent Plugin. It is not the Grok Build marketplace and not a Grok consumer-store listing.
