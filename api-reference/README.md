---
description: "Developer API for integration with Payhawk — manage expenses, cards, users, and more."
icon: code
layout:
  width: wide
  cover:
    visible: false
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
---

# Payhawk API

The Payhawk API is a REST API that lets you integrate your systems with Payhawk's spend management platform. Use it to sync expenses into your ERP, automate card issuance, manage users, or build custom approval workflows.

**Base URL:** `https://api.payhawk.com/api/v3`

<table data-view="cards">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th data-hidden data-card-target data-type="content-ref"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Authentication</strong></td>
      <td>Get your API key and authenticate requests.</td>
      <td><a href="getting-started/authentication.md">authentication</a></td>
    </tr>
    <tr>
      <td><strong>Rate Limits</strong></td>
      <td>Understand request limits and how to handle 429s.</td>
      <td><a href="getting-started/rate-limits.md">rate-limits</a></td>
    </tr>
    <tr>
      <td><strong>Errors</strong></td>
      <td>HTTP status codes and error response shapes.</td>
      <td><a href="getting-started/errors.md">errors</a></td>
    </tr>
  </tbody>
</table>

## What you can do

| Resource | Description |
|----------|-------------|
| [Expenses](https://app.gitbook.com/s/6bSyETdqciHmrkb7hGG5/) | Retrieve, update, and export expense records |
| [Cards](https://app.gitbook.com/s/6bSyETdqciHmrkb7hGG5/) | Issue virtual cards, set limits, freeze/unfreeze |
| [Users](https://app.gitbook.com/s/6bSyETdqciHmrkb7hGG5/) | Manage employees and their roles |
| [Purchase Orders](https://app.gitbook.com/s/6bSyETdqciHmrkb7hGG5/) | Create and manage the full PO lifecycle |
| [Webhooks](https://app.gitbook.com/s/6bSyETdqciHmrkb7hGG5/) | Subscribe to real-time events |
| [Fund Accounts](https://app.gitbook.com/s/6bSyETdqciHmrkb7hGG5/) | Query balances and statement lines |

## OpenAPI spec

Download the full spec: [`https://api.payhawk.com/api/v3/docs.json`](https://api.payhawk.com/api/v3/docs.json)
