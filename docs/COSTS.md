# Costs, budgets and spend protection

Fonsviva shows what work costs, local or cloud, before it runs.

## Local power cost

Estimated power cost = device wattage while working (GPU plus CPU, measured where the hardware reports it, otherwise rated wattage) × hours × the electricity rate. The rate defaults from the user's region and can be edited. Shown per job and as daily and monthly totals, labelled as an estimate.

## Cloud cost

- Price per hour for the chosen GPU, and an estimate per job, shown **before** the job runs.
- Running totals by day and month, per provider.

## Spend protection (cloud)

It is easy to burn money on rented GPUs. These protections are on by default and are part of the personal-use-only rule in [CLOUD](CLOUD.md).

- **Hard budget caps** per day, per month and per job. A provider can't be turned on until caps are set. At the cap, Fonsviva stops cloud jobs and blocks new ones.
- **Estimate and confirm** before every launch.
- **Auto-stop idle pods** after 10 minutes by default, and a **max runtime** per job.
- **Scale to zero** and prefer serverless options when the provider has them.
- **Orphan cleanup:** find and stop pods and volumes Fonsviva launched that no job owns.
- **Storage warning** before creating any volume or disk that costs money while idle.
- **Alerts** at 50%, 80% and 100% of each budget.
- **Cheapest safe GPU picker:** the lowest-cost GPU that has a passing registry recipe for the model.
- **Dry run:** `--dry-run` shows the plan, GPU, estimate and caps without launching anything.
- **Emergency stop:** one "Stop all cloud" button and `fonsviva cloud stop-all`, which stops every pod and job on every provider and turns cloud off until the user turns it back on.
