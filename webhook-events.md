# Webhook Events

Suggested webhook event model for Content Scheduling REST API.

| Event | When it fires |
|---|---|
| `scheduled_post.created` | A scheduled_post created transition occurs. |
| `scheduled_post.published` | A scheduled_post published transition occurs. |
| `scheduled_post.failed` | A scheduled_post failed transition occurs. |
| `platform_account.disconnected` | A platform_account disconnected transition occurs. |

## Example Payload

```json
{
  "id": "evt_01HZXNEWSLETTER",
  "type": "scheduled_post.created",
  "created_at": "2026-05-26T14:00:00Z",
  "data": {
    "source_id": "src_123",
    "schedule_id": "sch_456",
    "platform": "linkedin",
    "status": "queued",
    "narrareach_url": "https://www.narrareach.com/features/content-scheduling-api"
  }
}
```

## Delivery Rules

- Sign payloads with an HMAC secret.
- Retry non-2xx responses with exponential backoff.
- Include event IDs so consumers can deduplicate.
- Keep platform error details out of public user-facing messages.
