# Creep does not harvest: target is beyond range

## Symptom and scope

An owned Creep is not collecting from its intended harvest target.

For **Screeps World/MMO**, not Arena. This is an invented exercise, not real player data, a live test, or accepted Runtime Evidence.

## Complete minimal input

Copy only the JSON into the matching symptom in the optional [website Doctor](https://www.linqingan.com/en/resolver?doctor=creep-not-harvesting#screeps-doctor). It is a V1 snapshot, with exact keys and fewer than 4096 characters.

```json
{
  "version": 1,
  "symptom": "creep-not-harvesting",
  "creep": {
    "visible": true,
    "owned": true,
    "activeWorkParts": 2
  },
  "target": {
    "visible": true,
    "inRange": false
  }
}
```

## Expected diagnosis

- Classification: `target-out-of-range`.
- Confidence: `direct` (directly supported by these synthetic fields).
- The Doctor executes no action: `doctorExecutesAction=false`.
- Verification remains `session-only`; `publishableRuntimeEvidence=false`.

The visible, owned Creep has active WORK parts and the target is visible, but inRange is false. Range is the observed blocker. This is not a captured ERR_NOT_IN_RANGE result: no harvest call was made by the fixture or Doctor.

## Manual fix

1. In your own game, identify the intended harvest target and check whether the Creep can reach an adjacent position.
2. Let your own code move the Creep into harvest range (range 1), checking the movement result and later position. The Doctor does not issue movement or harvesting actions.
3. Resample once both objects remain visible and inRange is true. Changing JSON alone does not move a live Creep.

## Resample after the fix

This second JSON is also synthetic: it illustrates the expected changed observation, not a measured game outcome.

```json
{
  "version": 1,
  "symptom": "creep-not-harvesting",
  "creep": {
    "visible": true,
    "owned": true,
    "activeWorkParts": 2
  },
  "target": {
    "visible": true,
    "inRange": true
  }
}
```

Expected classification: `return-code-required`, confidence `bounded`, canonical Resolver step `harvest-result`. The previous blocker is absent; success has **not** been demonstrated.

## Verify in your game

Record the actual harvest(target) return value in your own game logic. On later ticks, inspect the Creep's relevant resource store and the target's state, accounting for other transfers, drops, or simultaneous actions. Being adjacent does not prove a valid target, available resource, or successful collection.

No live game action was executed to validate this recipe. The examples validate the Doctor's deterministic interpretation of supplied facts only. Keep real observations private.

## Applicability limits

The boolean is meaningful only when both the Creep and target are visible. The snapshot does not identify Source, Mineral, or Deposit; capture their actual API semantics through the canonical harvest-result step. It omits resource amounts, cooldowns, extractor constraints, storage state, and conflicting actions.

The recipe does not replace the canonical Resolver or official API reference. Recheck the live game state and actual return value rather than inventing one from the snapshot.

## Official references

- [Creep.harvest](https://docs.screeps.com/api/#Creep.harvest)
- [RoomPosition.inRangeTo](https://docs.screeps.com/api/#RoomPosition.inRangeTo)

[All recipes](../README.md) · [Synthetic-only feedback](https://github.com/ubvsuid/screeps-debugging-recipes/issues/new/choose)
