---
name: voiceover
description: Make a SaleMate voiceover when the user wants spoken audio from text or a saved script.
---

# voiceover

Get the exact script, language, voice and target length (15, 30 or 60 seconds). Gemini defaults to Kore; Voxtral defaults to jane-neutral. Choose Voxtral preset IDs from list_models(kind: "audio"). Do not invent a voice-clone ID.

Use a saved text asset_id or supply text. Estimate generate_voiceover, state the price (currently 2.5 credits) and balance, then use max_credits. If the user chooses another voice, check its supported identifier before submitting.

Wait for saved output and settled credits. A requested-duration voiceover is not ready until the product reports duration verification. Return the durable audio link; do not claim a provider acceptance is a finished recording.
