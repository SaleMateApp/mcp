---
name: checking-jobs
description: Check SaleMate generation progress without duplicate charges when a job is queued, running, ambiguous or finishing.
---

# checking jobs

Once you have a job_id, check it only with get_job or wait_for_job; never call generate_* again to check status.

Prefer wait_for_job with up to eight jobs and a timeout of at most 45 seconds. Otherwise use get_job and respect retry_after_seconds, usually 10-15 seconds. Do not busy-poll.

A repeated identical generation within ten minutes returns the same run, even if it finished. Ambiguous submissions stay deduplicated while unresolved. If there is no job_id and the response is unknown, repeat the exact inputs to reconcile that logical run. The server reuses its stored upstream key and payload; do not invent another request. Explicit rejected responses are safe to retry. Do not change max_credits or use another take to work around an unknown response.

For an intentional additional result, use new_take: true and a fresh take_id UUID, preserving that UUID on retries. That explicit ID protects the additional take against transport retries.

MCP-generated success requires durable output and settled credits. Failed or canceled jobs report their execution status even when billing_pending is true; follow retry_after_seconds while accounting is pending, and never claim a refund until it is confirmed. A terminal older website job may report billing: unknown with no retry hint: show its actual status and unknown cost without repeatedly polling it.

If recovery_required is true, follow the returned explanation. Changed Mini Dramas scenes and exhausted Flow/Nova resend limits keep the original request unknown for lookup or operator reconciliation; they do not authorize another generation or prove that nothing was charged.

Vanta cancellation works only before the video starts. Only delete saved assets when the user explicitly requests permanent deletion.
