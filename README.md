# Screeps Debugging Recipes

Three small, reproducible debugging exercises for **Screeps World (MMO)**: distinguish an observed blocker from a successful game action.

| Symptom | Recipe | What you learn |
| --- | --- | --- |
| Spawn is idle but no Creep appears | [Spawn: energy blocked](recipes/spawn-energy-blocked.md) | Compare requested body cost with available room energy. |
| A Creep stays still | [Movement: fatigue blocked](recipes/movement-fatigue-blocked.md) | Check fatigue before investigating pathfinding. |
| A Creep does not harvest | [Harvest: target out of range](recipes/harvest-out-of-range.md) | Check range before interpreting a harvest result. |

Each recipe includes a complete synthetic V1 JSON input, an explainable expected diagnosis, a manual fix, a second synthetic snapshot, and a separate in-game verification checklist. You can use the documents without installing or running anything.

## Optional interactive Doctor

Open [Screeps Doctor on linqingan.com](https://www.linqingan.com/en/resolver#screeps-doctor), select the matching symptom, and paste a recipe's JSON. The website is maintained by this repository's owner; visiting it is optional.

The existing website owns the diagnosis engine. This repository contains documents and synthetic examples only: no copied engine, CLI, npm package, or game automation.

## Privacy and evidence boundary

All included snapshots are invented teaching fixtures. They contain no real player names, room names, object IDs, colony state, tokens, or secrets. They are **not actual gameplay observations or public Runtime Evidence**.

The Doctor handles pasted snapshots locally in the browser. The existing site may send limited structured product events; the snapshot and free text are excluded by its current telemetry contract. Reading this repository or clicking a link does not establish that someone completed a diagnosis.

Do not post real snapshots, account details, tokens, code dumps, Memory, or private logs in Issues. Use the [recipe feedback form](https://github.com/ubvsuid/screeps-debugging-recipes/issues/new/choose) with a synthetic reproduction only. Inspect and remove sensitive details before submitting anything; GitHub Issues are public.

## Compatibility and limits

These fixtures use LQ Diagnostic Snapshot **version 1**, as checked against the site's [Doctor source at e03a871c](https://github.com/ubvsuid/linqingan-blog/blob/e03a871c8f198101d147e4c79aaf71b91071a7ec/src/lib/screeps-doctor.ts). The parser accepts exact fields only and a maximum of 4096 characters. Do not add annotations inside the JSON.

A classification describes the supplied facts. Clearing one blocker produces `return-code-required`, not proof that spawning, movement, or harvesting succeeded. Record the actual API return value and inspect later game ticks yourself. These are World/MMO recipes, not Screeps Arena API examples.

## License and pilot

The [MIT license](LICENSE) covers the original documents and synthetic examples in this repository only. It grants no license to the website's source, linked documentation, third-party material, or Screeps trademarks. Official references are linked, not republished. This is an independent project, not an official Screeps product.

This is a bounded [28-day distribution pilot](MEASUREMENT.md). GitHub Actions are disabled; there are no workflows, builds, packages, deployments, or scheduled collection jobs. No community promotion is part of the initial release.
