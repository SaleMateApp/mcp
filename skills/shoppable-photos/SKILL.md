---
name: shoppable-photos
description: Generate SaleMate product-photo creatives through Shoppable Photos with its fixed-price preset contract and safe retries.
---

# Shoppable Photos

1. Use `shoppable_photos` when the user requests this product. Choose their intended preset: `single-image`, `tiktok-carousel`, `bottom-of-funnel`, `lifestyle-ad`, `comparison`.
2. Collect 1–8 JPEG/PNG/WebP product images. Supply at most one main `asset_id`, `upload_id` or `url`; additional images go in `reference_urls`. Accept optional instructions in `prompt` and one of `1:1`, `4:5`, `9:16`, `16:9` as `aspect_ratio`.
3. Call `estimate_cost` for `shoppable_photos` with those exact inputs. The checked-in product contract is 20 credits per generation; use the returned estimate and do not invent a per-slide multiplier. Supply the user's `max_credits` and obtain required human approval before generation. Never approve on the user's behalf.
4. Call the product tool once, retain the returned `job_id` and backend `shoppable_photos`, and poll only with `get_job` or bounded `wait_for_job`. Do not route this preset through generic `generate_image`.

Retry uncertain submissions only with the original unchanged inputs. Never create a new take ID to bypass `unknown`, a changed price or an approval requirement. An explicitly requested additional result uses `new_take: true` and one fresh `take_id`, preserved on retries. Cancellation is not exposed for this product. Report completion only when the MCP returns durable output and settled billing.
