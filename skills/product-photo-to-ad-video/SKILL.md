---
name: product-photo-to-ad-video
description: Create a product ad from an existing photo using the user's selected SaleMate video model.
---

# Product photo to ad video

1. Clarify whether the user wants one animated product clip or a guided product-ad workflow. If they did not choose a model, call list_models with recommendation.use_case `single_video` or `product_ad`, their budget, duration, format and supplied reference counts. Explain the recommended option and alternative with tradeoffs, then ask which video model or workflow they want. Never silently choose Vanta or another model.
2. Find the product image in list_assets or upload it with create_upload. Ask for the audience, offer, aspect ratio and message if missing. Use the selected model's supported duration and inputs.
3. Call estimate_cost for the selected tool with the exact planned inputs. Indicative recommendation prices are not quotes. State the price and balance; set max_credits to the permitted amount. Do not estimate every candidate just to rank it.
4. Call generate_video once for a selected direct clip, or follow agent-styles for a chosen run_style workflow. Supply the selected model and asset_id or upload_id. Follow confirmation_required through the host's human approval flow; workflow image review remains explicit.
5. Use wait_for_job or honor retry_after_seconds. Return the saved output after terminal success and settled credits. Provider acceptance is not completion.

Vanta supports 5-15 seconds and starts at 5 seconds. Other models have their own requirements; use list_models. Never show internal queue positions, shared capacity or wait estimates.

Use `quality_focus: "product_fidelity"` when preserving the product's shape, packaging or logo is the key concern; for a spoken product pitch use `quality_focus: "dialogue"` and the user's stated `dialogue_language`. Explain the returned test observations and evidence gaps. A visually present product or an ad-effectiveness score does not establish reference fidelity or a better video model. Current saved evidence does not provide a graded product-fidelity comparison, so do not claim a winner.
