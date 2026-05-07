---
description: "HTTP status codes and error response format for the Payhawk API."
icon: triangle-exclamation
---

# Errors

The Payhawk API uses standard HTTP status codes and returns a consistent JSON error body.

## Error response format

```json
{
  "code": "RESOURCE_NOT_FOUND",
  "message": "Expense with ID exp_abc123 was not found.",
  "details": {
    "resourceType": "expense",
    "resourceId": "exp_abc123"
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `code` | string | Machine-readable error code |
| `message` | string | Human-readable description |
| `details` | object | Optional additional context |

## Status codes

| Code | Meaning | Common causes |
|------|---------|---------------|
| `200 OK` | Success | — |
| `201 Created` | Resource created | POST that creates a new resource |
| `204 No Content` | Success, no body | DELETE operations |
| `400 Bad Request` | Invalid input | Missing required field, wrong type, invalid enum value |
| `401 Unauthorized` | Authentication failed | Missing or invalid `X-Payhawk-ApiKey` header |
| `403 Forbidden` | Insufficient permission | Key lacks the required scope |
| `404 Not Found` | Resource not found | Wrong ID, or resource was deleted |
| `409 Conflict` | State conflict | Trying to approve an already-approved expense |
| `422 Unprocessable` | Business logic error | Expense cannot be exported (missing receipt, open approval) |
| `429 Too Many Requests` | Rate limit hit | See [Rate Limits](rate-limits.md) |
| `500 Internal Server Error` | Server error | Retry with backoff; contact support if persistent |

## Common error codes

| `code` | Meaning |
|--------|---------|
| `AUTHENTICATION_FAILED` | API key is missing, malformed, or revoked |
| `PERMISSION_DENIED` | Key does not have the required scope |
| `RESOURCE_NOT_FOUND` | The requested resource does not exist |
| `VALIDATION_ERROR` | Request body failed schema validation |
| `RATE_LIMIT_EXCEEDED` | Too many requests — see [Rate Limits](rate-limits.md) |
| `EXPENSE_NOT_EXPORTABLE` | Expense is missing required fields or has a pending approval |
| `CARD_FROZEN` | Operation cannot be performed on a frozen card |

## Idempotency

`POST` requests that create resources accept an optional `Idempotency-Key` header. If you send the same key twice, the second request returns the original response without creating a duplicate:

```bash
curl -X POST https://api.payhawk.com/api/v3/cards \
  -H "X-Payhawk-ApiKey: YOUR_API_KEY" \
  -H "Idempotency-Key: create-card-user-123-2024-01-15" \
  -H "Content-Type: application/json" \
  -d '{"userId": "usr_abc", "limit": {"amount": 500, "currency": "GBP"}}'
```

Use a deterministic key (e.g. `action-resourceId-date`) so retries after a network failure don't accidentally create duplicates.
