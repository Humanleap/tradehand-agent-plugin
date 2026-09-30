---
name: tradehand
description: Find, price and book local UK tradespeople with Tradehand, then hand the customer a Stripe link to pay.
---

Tradehand's MCP server is `https://tradehand.com/api/mcp` (ChatGPT: `/api/mcp/chatgpt`), Streamable HTTP.

Find
- `browse_trades` lists the trades. `search_traders` finds public listings by trade and area. `get_trader` and `get_service_options` open one listing.

Book (signed-in customer)
1. `prepare_booking` with the listing's reference (or a business's own `co-…` reference), the service, the full address and postcode. It returns fixed-price services, live slots (each with a `slotReference`) and a `revision`.
2. `confirm_booking` with that `revision` as `expectedRevision` and the chosen `slotReference` exactly. The first call returns the live total and books nothing. Show it.
3. Only after the customer says yes, call `confirm_booking` again with that exact `confirmedTotalAmount`. It books the visit and returns `checkoutUrl`. Give the customer that link.
- A link is never payment. Say it is paid only when `get_job` says so.
- `SLOT_UNAVAILABLE` or `STALE_REVIEW`: call `prepare_booking` again and offer the new times or price.

Quotes and jobs
- `quote_start`, `quote_answer` and the other `quote_*` tools price work that has no fixed price. `list_my_jobs` and `get_job` show the customer's jobs. `start_job_checkout` returns the payment link for money due on a job.
