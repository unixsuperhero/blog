 there is a site i built for managing invoices, commission, etc for a company.

when dealing with money, special care should be taken because mistakes can ruin someone's day.

for this site, commission for an employee is earned 2 different times per job.
1. when they do the work
2. when the customer pays for the work

commission is calculated every week.  so commission for a job can end up on 2 different commission sheets.

for various reasons, after the original job record was created, the pricing/invoice amount is changed.

so, if the invoice already appeared on a commission sheet, it's values are now inaccurate.

so....

how do you address this?

- bg task that checks commission sheet amounts and recalculates the amount from the current job amounts (passive)
- when a job is updated, see if it was on a commission sheet and update it (active)
- lock a job once it's on a commission sheet
- don't put a job on a cmmission sheet unless it's marked as finalized

how do you get visibility into when this happens?

- send an email notification?

how do you track the amounts before/after?

- adjustments records?