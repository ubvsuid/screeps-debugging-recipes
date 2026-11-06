# Spawn is idle: requested body exceeds available energy

## Symptom and scope

An idle Spawn does not start the requested Creep.

For **Screeps World/MMO**, not Arena. This is an invented exercise, not real player data, a live test, or accepted Runtime Evidence.

## Complete minimal input

Copy only the JSON into the matching symptom in the optional [website Doctor](https://www.linqingan.com/en/resolver?doctor=spawn-not-working#screeps-doctor). It is a V1 snapshot, with exact keys and fewer than 4096 characters.

```json
{
  "version": 1,
  "symptom": "spawn-not-working",
  "room": {
    "visible": true,
    "energyAvailable": 300
  },
  "spawn": {
    "visible": true,
    "owned": true,
    "spawning": false,
    "remainingTime": null
  },
  "request": {
    "bodyCost": 350
  }
}
```

## Expected diagnosis

- Classification: `energy-blocked`.
- Confidence: `direct` (directly supported by these synthetic fields).
- The Doctor executes no action: `doctorExecutesAction=false`.
- Verification remains `session-only`; `publishableRuntimeEvidence=false`.

The room and owned Spawn are visible and the Spawn is idle. The requested body costs 350 energy, while the room currently has 300. This identifies an energy shortfall in the supplied facts; it does not report an API call or return code.

## Manual fix

1. In your own game logic, check that the cost was computed from the actual requested body. For example, two WORK, one CARRY, and two MOVE parts cost 350 energy in World.
2. Either choose a body costing no more than the currently available energy, or refill the room's Spawn/extensions. Check capacity before waiting: if capacity is below the requested cost, refilling alone cannot reach it.
3. This exercise takes the refill path: resample when available energy reaches 350, keeping the same request. Do not change a live colony merely by editing JSON.

## Resample after the fix

This second JSON is also synthetic: it illustrates the expected changed observation, not a measured game outcome.

```json
{
  "version": 1,
  "symptom": "spawn-not-working",
  "room": {
    "visible": true,
    "energyAvailable": 350
  },
  "spawn": {
    "visible": true,
    "owned": true,
    "spawning": false,
    "remainingTime": null
  },
  "request": {
    "bodyCost": 350
  }
}
```

Expected classification: `return-code-required`, confidence `bounded`, canonical Resolver step `spawn-dryrun`. The previous blocker is absent; success has **not** been demonstrated.

## Verify in your game

Inspect the actual spawnCreep request with the canonical Resolver's dry-run step first. A dry run does not create a Creep. If appropriate, let your own game code issue the real request; record its return value, observe spawning state on later ticks, and verify the intended Creep appears after spawning completes. A fresh name, valid body, ownership, and other request conditions still matter.

No live game action was executed to validate this recipe. The examples validate the Doctor's deterministic interpretation of supplied facts only. Keep real observations private.

## Applicability limits

The fixture's room must have capacity of at least 350 for this refill path to be feasible. It does not capture body parts, name collisions, custom energyStructures options, competing requests, or timing changes between sampling and calling. A sample may become stale before the next action.

The recipe does not replace the canonical Resolver or official API reference. Recheck the live game state and actual return value rather than inventing one from the snapshot.

## Official references

- [StructureSpawn.spawnCreep](https://docs.screeps.com/api/#StructureSpawn.spawnCreep)
- [Room.energyAvailable](https://docs.screeps.com/api/#Room.energyAvailable)

[All recipes](../README.md) · [Synthetic-only feedback](https://github.com/ubvsuid/screeps-debugging-recipes/issues/new/choose)
