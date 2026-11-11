# Cloud providers: personal use only

RunPod and other cloud GPU providers are useful for one person's own experiments. They are not a safe place for other people's tax returns or a university's records, so Fonsviva allows them for personal use only.

## Fonsviva is the only place cloud lives

UntoCaesar, Gantrel and UniCerebrum never talk to a cloud provider. They connect to Fonsviva and show where each job ran. Fonsviva alone owns adding providers, storing their keys (encrypted, never shown again after entry), estimating and tracking cost, the personal-use-only rule and the blocks below. The apps' compute settings are "Connect to Fonsviva" screens.

## The rule

- **Vetted providers only.** Providers come from [providers](providers.md).
- **Spend protection on.** Budget caps, auto-stop, orphan cleanup and an emergency stop are always on. See [COSTS](COSTS.md).

- **Off by default.** Cloud providers stay off until the user turns them on.
- **Personal profile only.** They can be enabled only on a personal profile.
- **Hard block for protected work.** Jobs from UntoCaesar client or volunteer returns and from UniCerebrum (institutional and student data) can never run on a cloud provider. There is no override, setting or flag that changes this. Those jobs run on owned local compute or shared Sparks the institution or preparer controls, or they wait.
- **Cost first.** Before a cloud job starts, Fonsviva shows the expected cost and the provider.
- **Confirm every job.** Each cloud job needs an explicit confirmation. No silent fallback to cloud when local is busy.
- **Labelled.** Every job and result records where it ran.

## Why

- **FERPA.** A school may share education records with a contractor only under the "school official" exception, which requires the school to keep direct control over the use and maintenance of the records (34 CFR 99.31(a)(1)(i)(B)), and limits redisclosure (34 CFR 99.33). See the Student Privacy Policy Office (PTAC) guidance on cloud computing.
- **Tax return information.** Preparers may not disclose or use return information without the taxpayer's written consent (26 U.S.C. 7216 and 26 CFR 301.7216).
- **GLBA Safeguards Rule.** Tax preparers are financial institutions under the FTC Safeguards Rule (16 CFR 314), which requires overseeing service providers that handle customer information.
- **RunPod today.** RunPod reports SOC 2 and ISO 27001, but publishes no FERPA or Section 7216 terms and offers a custom data processing agreement only at large monthly spend (about $3,000 or more). Generic GPU rental does not meet the bar above.

This file is not legal advice. Institutions and preparers should confirm with their own counsel.
