# 28-day GitHub distribution pilot

## Start and boundaries

D0 is the date when all seven files are public and release acceptance is complete. Publication date alone is not acceptance. D0 is confirmed in the execution result after final checks; until then it is pending. Use UTC for GitHub traffic records and retain actual acceptance timestamps, including the local date if different.

The pilot asks whether three useful World/MMO debugging recipes attract relevant readers and produce actionable feedback. It does not test a new engine, CLI, package, or website feature.

Keep the existing sitewide ACT-2026-09-001 status unchanged. Its fixed post-release windows are 2026-09-08..2026-09-14 and 2026-09-08..2026-10-05. This pilot starts independently after those historical windows and must not be credited to that SEO experiment. Current or future sitewide traffic may still have multiple causes.

## Manual readings

At D0, D7, D14, D21, and D28, manually read accessible GitHub Traffic, available website referral reports, and recipe Issues. No scheduled jobs or automatic collection. Save dated readings privately in an already authorized location; this document does not authorize writes to project canonical records.

| Layer | Record | Evidence boundary |
| --- | --- | --- |
| GitHub reach | Daily views, daily unique visitors, clones, readable referring sites and popular paths | Traffic is rolling 14 days, UTC. Read weekly to avoid gaps. Sum daily views for non-overlapping dates; never sum daily or weekly uniques and call it 28-day deduplicated users. Identify operator checks where possible. |
| Website referrals | Readable github.com-to-site arrivals and landing paths from existing reports | GitHub's referring-sites list measures inbound traffic to GitHub, not outbound clicks to the website. Without readable website-side evidence, record UNKNOWN. |
| Actual website use | Existing readable Doctor event counts, if available | Current events lack a GitHub campaign/referrer-to-session join. They cannot identify GitHub-origin diagnosis completions. Do not equate visits, link clicks, or aggregate Doctor events with completed use by GitHub readers. |
| Player value | Substantive feedback that identifies a recipe, expected/observed behavior, or a concrete clarification | A synthetic exercise is not live runtime verification. Separate author/operator activity, duplicates, and unsupported claims. |
| Cost and safety | Manual maintenance time, Actions disabled readback, runs since D0, unexpected automation | Target is 0 Actions job minutes. Zero observed runs supports zero observed runtime, not an account-wide billing audit or a promise about third-party App activity. |

For each reading retain the source, access time, exact date coverage, timezone, totals or daily grain, and missing fields. Missing, inaccessible, delayed, or privacy-filtered data is UNKNOWN, not zero.

GitHub Traffic documentation: https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/viewing-traffic-to-a-repository

## Review at D28

Assess concrete evidence of relevant readership, identifiable referrals where readable, and independently useful feedback against manual maintenance time. Stars and forks are secondary context, not causal growth evidence.

If reach exists but referral/use attribution is unavailable, report the limitation rather than infer conversion. If no relevant independent value is observed, hold expansion: do not build a CLI or package. If feedback identifies a useful bounded documentation fix, propose that scope separately.

## Resource protection and stop conditions

GitHub Actions must remain disabled. Do not add workflows or use Pages, Codespaces, Larger Runners, Actions Artifacts, Packages, Vercel, or automatic deployments for this pilot. Do not modify CNC resources or existing App installation scopes.

Stop new publication on unexplained Actions activity, a suspected cross-repository trigger, unexpected deployment linkage, a secret exposure, or a contract mismatch. Capture run ID, actor, event, timestamp, and commit where visible; do not cancel CNC runs or change account-wide settings without separate authorization. App background processing is an accepted bounded residual risk, not proven absent.

Community promotion is outside this release. D7/D14/D21/D28 are a manual observation plan, not scheduled automations.
