---
name: vibe-shift
description: Transfer motion to a character with SaleMate Vibe Shift using verified MP4 timing, an explicit credit ceiling and the existing job lifecycle.
---

# Vibe Shift

1. Use `vibe_shift` for the user's requested motion transfer, not as an automatic substitute for an unspecified video model.
2. Collect exactly one motion reference using `motion_asset_id`, `motion_upload_id` or `motion_url`, and exactly one character image using `character_asset_id`, `character_upload_id` or `character_url`. Do not use the generic main-media fields.
3. Motion must be a nonfragmented MP4 with readable video timing, longer than zero and at most 30 seconds. Character images support JPEG/PNG/WebP. If timing or format cannot be verified, ask for a supported MP4; do not guess its duration or rename another format.
4. Call `estimate_cost` for the exact `vibe_shift` inputs. The product quote uses measured video duration, rounded up, at 25 credits per second. Explain the returned total, supply the user's `max_credits`, and obtain required human approval. Never approve autonomously or substitute a client-provided duration.
5. Start once. Preserve the returned `job_id` and backend `vibe_shift`, then poll `get_job` or bounded `wait_for_job`. Do not resubmit the generation to check progress.

An uncertain response is the same pending logical request: retain the exact inputs and all IDs for reconciliation. Never use a fresh ID to escape `unknown`. Only an intentional additional result gets `new_take: true` and a fresh `take_id`, reused on retries. MCP cancellation is unavailable; do not call another product's cancellation endpoint or promise a refund. Success requires durable output and settled billing.
