---
description: "Request rate limits for the Payhawk API and how to handle throttling."
icon: gauge-high
---

# Rate Limits

The Payhawk API enforces rate limits per API key to ensure fair usage and system stability.

## Limits

| Tier | Requests per minute | Requests per day |
|------|--------------------:|----------------:|
| Standard | 60 | 10,000 |
| Enterprise | 300 | 100,000 |

Limits apply per API key. Contact Payhawk support to request an increase.

## Rate limit headers

Every response includes headers showing your current usage:

```http
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 42
X-RateLimit-Reset: 1712345678
```

- `X-RateLimit-Limit` — requests allowed per minute
- `X-RateLimit-Remaining` — requests remaining in the current window
- `X-RateLimit-Reset` — Unix timestamp when the window resets

## Handling 429 responses

When you exceed the limit, the API returns `429 Too Many Requests` with a `Retry-After` header:

```http
HTTP/1.1 429 Too Many Requests
Retry-After: 30
Content-Type: application/json

{
  "code": "RATE_LIMIT_EXCEEDED",
  "message": "Too many requests. Retry after 30 seconds."
}
```

Implement exponential backoff with jitter for any automated client:

```javascript
async function fetchWithRetry(url, options, maxRetries = 3) {
  for (let attempt = 0; attempt <= maxRetries; attempt++) {
    const response = await fetch(url, options);
    if (response.status !== 429) return response;

    const retryAfter = parseInt(response.headers.get('Retry-After') ?? '5', 10);
    const jitter = Math.random() * 1000;
    await new Promise(r => setTimeout(r, (retryAfter * 1000) + jitter));
  }
  throw new Error('Max retries exceeded');
}
```
