---
description: "How to authenticate with the Payhawk API using an API key."
icon: key
---

# Authentication

The Payhawk API uses API key authentication. Every request must include your key in the `X-Payhawk-ApiKey` header.

## Getting an API key

1. Log in to your Payhawk dashboard as an administrator
2. Go to **Settings → Developer → API Keys**
3. Click **Generate new key**, give it a descriptive name (e.g. `erp-integration-prod`)
4. Copy the key immediately — it is shown only once

{% hint style="danger" %}
Treat your API key like a password. Do not commit it to source control or include it in client-side code. Store it in an environment variable or secrets manager.
{% endhint %}

## Making an authenticated request

Include your API key in the `X-Payhawk-ApiKey` header on every request:

{% tabs %}
{% tab title="cURL" %}
```bash
curl -s https://api.payhawk.com/api/v3/expenses \
  -H "X-Payhawk-ApiKey: YOUR_API_KEY"
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const response = await fetch('https://api.payhawk.com/api/v3/expenses', {
  headers: {
    'X-Payhawk-ApiKey': process.env.PAYHAWK_API_KEY,
  },
});
const data = await response.json();
```
{% endtab %}

{% tab title="Python" %}
```python
import httpx

client = httpx.Client(headers={"X-Payhawk-ApiKey": os.environ["PAYHAWK_API_KEY"]})
response = client.get("https://api.payhawk.com/api/v3/expenses")
data = response.json()
```
{% endtab %}
{% endtabs %}

## Key scopes

When generating a key you can restrict it to specific resource types:

| Scope | Access |
|-------|--------|
| `expenses:read` | Read expense records |
| `expenses:write` | Create and update expenses |
| `cards:read` | Read card details |
| `cards:write` | Issue cards, set limits, freeze/unfreeze |
| `users:read` | Read user records |
| `users:write` | Create and update users |
| `webhooks` | Manage webhook subscriptions |

Restrict keys to only the scopes your integration needs — a key used only for expense export should not have `cards:write`.

## Rotating keys

Keys do not expire automatically. Rotate them periodically and immediately if you suspect a leak: go to **Settings → Developer → API Keys**, revoke the old key, and generate a new one.
