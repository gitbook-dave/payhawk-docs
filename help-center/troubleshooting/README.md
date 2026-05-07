---
description: "Solutions to common issues in Payhawk."
icon: wrench
---

# Troubleshooting

## Card issues

<details>
<summary>My card was declined despite having sufficient balance</summary>

This is usually a spend policy restriction, not a balance issue. Check:

1. **Category restriction** — the merchant's MCC code may be blocked by your spend policy
2. **Per-transaction limit** — the amount may exceed your card's per-transaction cap
3. **Card frozen** — check the card status in your Payhawk app; it may have been frozen by your administrator

Contact your administrator if you need a policy exception.

</details>

<details>
<summary>I cannot unfreeze an employee's card</summary>

If a card belongs to an employee who is marked inactive in your HRIS (e.g. BambooHR, Workday), Payhawk locks the card automatically to prevent misuse. To unfreeze:

1. Reactivate the employee in your HRIS
2. Wait for the Payhawk–HRIS sync to run (up to 15 minutes)
3. The card will unlock automatically

If the employee has genuinely left, do not unfreeze — deactivate their Payhawk user instead.

</details>

## Export errors

<details>
<summary>Export to QuickBooks Online failed: "invalid account type for billable expense"</summary>

A billable expense must be mapped to an income account in QuickBooks, not an expense account. In Payhawk:

1. Go to **Settings → Integrations → QuickBooks Online**
2. Find the expense category causing the error
3. Change the mapped account to an income-type account in QuickBooks

</details>

<details>
<summary>Export to Microsoft Business Central failed: "cannot assign new numbers from the number series"</summary>

The number series for the document type in Business Central is exhausted or incorrectly configured. In Business Central:

1. Go to **Setup → No. Series**
2. Find the series used for the document type (usually G/L Journal or Purchase Invoice)
3. Extend the range or create a new series, then re-run the export from Payhawk

</details>

## Login issues

<details>
<summary>I can't log in to Payhawk</summary>

Try these steps in order:

1. Check you are using the correct email address (your work email, not a personal one)
2. Use **Forgot password** to reset your credentials
3. Check with your administrator that your account has not been deactivated
4. Clear your browser cache and cookies, then try again

If none of these work, contact <code class="expression">space.vars.support_email</code>.

</details>

## Still stuck?

Contact Payhawk support at <code class="expression">space.vars.support_email</code> or use the **Help** button in the bottom-right corner of the dashboard.
