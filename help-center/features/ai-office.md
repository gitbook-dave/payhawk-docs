---
description: "Use Payhawk's AI features to automate expense coding, receipt processing, and financial reporting."
icon: robot
---

# AI Office

AI Office is Payhawk's suite of AI-powered automation features. It reduces manual data entry for employees and reviewers by extracting information from receipts, suggesting accounting codes, and surfacing anomalies before they reach month-end.

{% hint style="info" %}
AI Office features are available on Ultimate and Enterprise plans. Some features are in beta via [Payhawk Labs](../payhawk-labs/README.md).
{% endhint %}

## Features

### Automated expense coding

When an expense is created — from a card transaction or a manual submission — AI Office analyses the merchant name, category, and historical coding patterns to suggest:

- Accounting code / GL account
- Cost centre
- VAT / tax rate
- Project code (if configured)

Accountants can accept suggestions individually or in bulk from the review queue.

### Receipt OCR

The Payhawk mobile app automatically extracts key data from receipt photos:

- Merchant name and address
- Total amount and currency
- Line items (where available)
- VAT / tax amount and rate

This pre-fills the expense form so employees only need to confirm, not type.

### Anomaly detection

AI Office flags expenses that look unusual based on your company's historical patterns:

- Amount significantly above category average
- Duplicate merchant + date + amount combination
- Expense submitted significantly after the transaction date

Flagged expenses appear in the **Review queue** with an explanation of why they were flagged.

### Travel AI Agent

See [Trips and Travel](trips-travel.md) for the full guide on the AI-powered travel booking feature.

## Enabling AI Office

AI Office is on by default for supported plan tiers. To configure individual features, go to **Settings → AI Office**.
