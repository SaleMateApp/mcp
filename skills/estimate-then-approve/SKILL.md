---
name: estimate-then-approve
description: Estimate and obtain human approval before SaleMate spending when an action uses credits or returns confirmation_required.
---

# estimate then approve

Use `list_models` recommendation for a free capability and budget shortlist before the user chooses. Its base prices are indicative, and its budget is not spending permission. Estimate only the selected exact request; some estimates prepare and upload reference media, so do not call them merely to compare every candidate.

1. Call estimate_cost with the exact generation inputs and read get_account when the user needs their balance or connection limits.
2. State the price. Supply max_credits on every generation. A price above this ceiling is refused.
3. Above the connection threshold (default 100 credits), or beyond 300 unconfirmed credits in 24 hours, a signed quote is required. Quotes expire after ten minutes and bind the exact inputs and price.
4. Have the user approve through the MCP App card, Claude Code's interaction-required tool, client elicitation, or the signed SaleMate sign-in link. Never approve autonomously. Opening a link does not approve; the user submits its protected form.
5. Replay unchanged generation inputs with quote_id. Approval alone does not start a job. Changed inputs or an expired quote require a fresh quote.

Do not suggest circumventing limits with another connection. The one-active-Vanta rule applies to the user across all connections. ChatGPT replies must not contain top-up links or promotion text.
