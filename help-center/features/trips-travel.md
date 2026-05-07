---
description: "Book and manage business travel within policy using Payhawk's Travel AI Agent."
icon: plane
---

# Trips and Travel

Payhawk's Travel AI Agent lets employees search for and book flights and hotels within their company's travel policy — without leaving the Payhawk app. All travel costs are charged to the employee's Payhawk card and auto-categorised as travel expenses.

{% hint style="info" %}
The Travel AI Agent is currently in beta via [Payhawk Labs](../payhawk-labs/README.md). Enable it from **Settings → Labs**.
{% endhint %}

## How it works

{% stepper %}
{% step %}
## Create a trip

Go to **Trips → New trip** and enter your destination, travel dates, and purpose. The AI Agent checks your company travel policy before showing results.
{% endstep %}

{% step %}
## Review options

The agent presents flights and hotels that are within policy, sorted by price. Options that would require an approval are flagged but still visible.
{% endstep %}

{% step %}
## Book

Select your preferred options and confirm. The agent books directly with the airline or hotel and emails confirmation to you and your manager.
{% endstep %}

{% step %}
## Expense auto-created

The booking cost appears in your Expenses list immediately, pre-coded with the travel category and trip details attached.
{% endstep %}
{% endstepper %}

## Travel policy configuration

Administrators set travel policy rules under **Settings → Travel Policy**:

| Setting | Description |
|---------|-------------|
| Max flight cost (economy) | Per-segment cap for economy class |
| Business class threshold | Trip duration above which business class is allowed |
| Hotel star rating | Maximum star rating per night |
| Max hotel cost | Per-night cap |
| Advance booking window | Minimum days before departure for standard booking |

## Supported providers

The Travel AI Agent currently books through:

- **Flights**: All major airlines via the GDS network (Amadeus)
- **Hotels**: Major hotel chains and independent properties via Booking.com for Business

Rail and car hire support is on the roadmap.
