---
name: agent-styles
description: Run SaleMate Default, Sparrow, Fashion, UGC Products or Perfumes and Beauty Ads with one approved workflow budget and explicit human review.
---

# Agent Styles

Use `run_style`. Ask which style the user wants; do not choose a style or video model implicitly.

| Style ID | Required choice and images |
| --- | --- |
| `default` | `quality`: `lite`, `pro` or `pro-1.5`; one image |
| `sparrow` | `video_model`: `seedance-1.5-pro` or `veo-3.1-fast`, plus `model_gender`; one image |
| `fashion` | Native Nova workflow; one image |
| `narrative` | UGC Products: `narrative_model` of `nova`, `spark` or `vanta`; 1–10 images |
| `perfumes-beauty-ads` | One Perfumes and Beauty Ads product; exactly 1 or 3 distinct images; `full_access` only |

1. Use `list_models` with `kind: "style"` and the current schema for supported durations/resolutions. `customized` mode must already be enabled in SaleMate; `preferences` is a read, not a settings write.
2. Estimate `run_style` with `action: "start"` and exact inputs. Explain the complete workflow price, supply `max_credits` and obtain required human approval before starting. This admits one workflow budget covering its native stages.
3. Save its run/job ID and poll `get_job` with backend `agent_styles`. `history`, `status`, `outputs` and `preferences` are inspection actions; never use `start`, `regenerate_image`, `approve_image` or `continue_video` to poll.
4. If the workflow requests `review_image`, show the image and wait for the user's decision. Call `approve_image` with `confirm_approval: true` only after explicit approval. For an explicitly requested change, use `regenerate_image`; include the desired prompt except where Narrative uses its native prompt handling.
5. Call `continue_video` only when the workflow requests `provide_video_prompt`, with the supplied prompt. Review/continue actions retain the existing budget and require `max_credits` plus a fresh `action_id` for that intentional action. Reuse that same ID and unchanged fields on retries.

Never auto-confirm review, bypass product checks, or treat initial budget approval as image approval. Review actions must belong to a nonterminal workflow started through this connection. Website runs and other connections' runs are not authorized for paid continuation. If the price changes, stop for the required pricing review; never increase the ceiling silently. A terminal workflow needs a separately authorized new start.

The native start is not idempotent. If its result is uncertain, the MCP deliberately does not send it again. Check workflow history or seek support; do not create another take or action ID to escape `unknown`/`recovery_required`. MCP cancellation is unavailable for Agent Styles.
