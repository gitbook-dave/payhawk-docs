---
description: "Configure approval workflows for expenses, purchase requests, and card limit increases in Payhawk."
icon: check-circle
---

# Approvals in Payhawk

Payhawk supports flexible approval workflows for expenses, purchase requests, and card top-up requests. Approval rules are set by administrators and enforced automatically.

## Types of approvals

| Type | Triggered by | Who approves |
|------|-------------|-------------|
| Expense approval | Employee submits an out-of-pocket expense | Team manager or custom approver |
| Purchase request | Employee raises a request before spending | Line manager + optional Finance sign-off |
| Card limit increase | Employee requests a higher card limit | Administrator |
| Fund account top-up | Administrator requests a top-up above a threshold | Finance director or CFO |

## Configuring approval rules

Go to **Settings → Approval workflows** to create and edit rules.

### Rule conditions

Each rule triggers when one or more conditions are met:

- Amount above a threshold
- Expense category
- Team or department
- Individual employee

### Approval chain

For each rule you can set:

- **Single approver** — one person must approve
- **Sequential chain** — approvers must sign off in order
- **Any of** — the first available approver in a group can approve

{% hint style="info" %}
Approval chains support up to 5 levels. For more complex workflows, use the [Approvals API](https://app.gitbook.com/s/6bSyETdqciHmrkb7hGG5/).
{% endhint %}

## Approving requests

Approvers receive an email notification and in-app notification when an item needs their attention. They can approve or reject directly from the notification, or from the **Approvals** section in the dashboard.

## Delegation

If an approver is out of office, they can delegate their approval authority to another user for a specified period: go to **Profile → Out of office** and set a delegate.
