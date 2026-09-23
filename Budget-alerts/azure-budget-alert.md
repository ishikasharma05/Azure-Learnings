# Azure Budget Alert Setup (Cost Management)

First hands-on project on **Azure** 🎉 — mirroring the budget/billing alarm work I'd already done on AWS (AWS Budgets → CloudWatch Billing Alarms), this time in Azure's Cost Management + Billing.

## Goal

Set up a monthly budget with alert thresholds so I get notified before I accidentally rack up charges on a free-tier account.

## Steps

1. **Log in to the Azure Portal**

2. **Search "Cost Management + Billing"**
   Used the top search bar → selected it.

3. **Navigate to Budgets**
   Cost Management + Billing → **Cost Management** → **Monitoring** → **Billing** → **Budgets** → **+ Add**.

4. **Scope**
   Selected my subscription as the scope (single subscription on the free tier).

5. **Budget basics**
   - Name: `monthly-learning-budget`
   - Reset period: Monthly
   - Amount: small threshold (few dollars) — just enough to catch any accidental spend

6. **Alert conditions**
   Configured two alert types:
   - **Actual cost** @ 25% — flags real spend as it happens
   - **Forecasted cost** @ 100% — warns me *before* I'm projected to hit the limit, based on Azure's spend trend

  <img width="888" height="260" alt="image" src="https://github.com/user-attachments/assets/34ddfe72-f25a-4f4c-b7cd-e4ae4ccc2fdc" />


7. **Alert recipients**
   Added my email under Alert recipients so notifications land directly in my inbox — no Action Group needed for a simple email alert (that's only required if you want automation, like auto-disabling a resource).

8. **Create**
   Reviewed and created the budget. First evaluation typically takes a few hours to kick in.

## AWS → Azure mapping

| AWS | Azure |
|---|---|
| AWS Budgets | Cost Management → Budgets |
| CloudWatch Billing Alarm | Budget alert conditions (Actual / Forecasted) |
| SNS topic for alert delivery | Built-in email alerts (or Action Groups for automation) |

## Notes / gotchas

- Hit a "Unique email address is required" validation error even with only one email entered — cleared the field and retyped manually instead of pasting, which resolved it.

## Next steps

- Add a second alert threshold (e.g. Actual @ 80%) for tighter monitoring
- Explore Action Groups to trigger automated responses (e.g. Azure Function to shut down resources) — parallel to AWS's SNS + Lambda auto-response pattern
- Continue mirroring AWS learning path: VM setup + IAM/RBAC next
