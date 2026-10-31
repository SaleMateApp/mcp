---
name: mini-dramas
description: Write and review a SaleMate Mini Dramas episode, approve its native Vanta batch once, and export only when requested.
---

# Mini Dramas

Use `mini_dramas`; select its `operation`, not a made-up tool name. This product uses Vanta. Explain that before an episode generation; do not silently route a generic video request here.

1. Inspect or create the series with `list_series`, `get_series`, `create_series`, `configure_series` or `start_story`. Add cast with `upload_cast`: one JPEG/PNG/WebP up to 10 MiB from an owned asset/upload or safe URL. Preserve stable resource IDs.
2. Write for free with `write_episode` (or `create_episode` for a manual episode). Inspect with `get_writing_run` and `get_episode`. Editing uses `rewrite_episode`, `rewrite_scene`, `configure_episode`, `configure_scene`, `edit_scene_plan` and `apply_episode_plan`; use `get_scene_prompt` to inspect a compiled prompt. Writing must not automatically start a paid batch.
3. Review the existing scene plan with the user. Quote `generate_episode` with its episode ID, stable `batch_id`, current `total_seconds`, `mode: "all"` and `max_credits`. Vanta costs 2 credits per requested second; each scene is 5–15 seconds. The server checks the current plan. A changed plan needs a fresh quote.
4. Complete the human approval flow, then call `generate_episode` once with those same inputs and any required `quote_id`. Use the native all-scenes batch, not a loop of takes. Only set `auto_export: true` if the user requests automatic export, and supply a stable `export_id`.
5. Poll paid generation with `get_job` using the returned ID and backend `mini_dramas`. Do not call `generate_episode` or `generate_take` to check progress. Use `get_episode` for plan inspection, `get_writing_run` for writing and `get_export` for an existing export.
6. For requested batch controls use `pause_episode` or `stop_episode`. `resume_episode` requires the user's explicit confirmation (`confirm_resume: true`), the original tracked batch and `max_credits` within its original approval. Never auto-set `skip_audio` or `skip_pronunciation` to bypass a review or missing input.
7. `select_take` chooses an existing scene result. A separately requested new scene take uses `generate_take` with its own stable `take_id`, exact duration and quote/approval. `export_episode` produces the requested MP4; `retry_export` retries only that export, without generating video or spending generation credits.

Other read operations are `list_episodes` and `get_series`. Writing and exports are free within native limits. Existing dialogue audio can be reused; these operations do not generate paid dialogue audio.

Never replace a series, episode, writing run, take, batch, export or action ID after an ambiguous reply. Reconcile with the same IDs and inputs; missing results do not prove failure. Mutations requiring `action_id` receive one UUID per intentional action and retain it on retries. Resume cannot adopt an untracked website/other-connection budget. Stop/pause does not mean an in-flight take has stopped or been refunded; trust returned terminal billing. An unknown response needs recovery, not another paid batch.
