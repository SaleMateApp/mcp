---
name: getting-files-in
description: Upload or reuse files for SaleMate when a task needs a reference image, video, audio or saved text.
---

# getting files in

Use list_assets and get_asset to reuse the user's library. Pass the returned asset_id, not a guessed storage key. A URL may only be a public HTTPS image, audio or video with permission for this use.

Claude web and desktop: attachments in chat are not automatically visible to the MCP server. Open the create_upload card; the user selects the actual file.

Claude Code, Codex and Cursor: call create_upload with the actual filename, content type and byte size. Run the returned curl command with the user's chosen local path. If your sandbox blocks the upload, show the user the returned curl command and ask them to run it with their local file; do not claim it uploaded. Links expire after ten minutes and permit one upload; keep them private.

ChatGPT: use the supported file parameter (url) or the upload card. Do not pass a local file path as a remote URL.

After upload success, use upload_id. Vanta registers every reused reference through its own upload endpoint automatically. Images for Vanta must be no larger than 10 MB; other uploads are capped at 20 MB. Never claim a missing or failed upload succeeded.
