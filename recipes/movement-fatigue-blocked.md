# Creep stays still: fatigue has not recovered

## Symptom and scope

An owned Creep remains at the same position.

For **Screeps World/MMO**, not Arena. This is an invented exercise, not real player data, a live test, or accepted Runtime Evidence.

## Complete minimal input

Copy only the JSON into the matching symptom in the optional [website Doctor](https://www.linqingan.com/en/resolver?doctor=creep-not-moving#screeps-doctor). It is a V1 snapshot, with exact keys and fewer than 4096 characters.

```json
{
  "version": 1,
  "symptom": "creep-not-moving",
  "creep": {
    "visible": true,
    "owned": true,
    "fatigue": 6,
    "activeMoveParts": 2
  }
}
```

## Expected diagnosis

- Classification: `fatigue-blocked`.
- Confidence: `direct` (directly supported by these synthetic fields).
- The Doctor executes no action: `doctorExecutesAction=false`.
- Verification remains `session-only`; `publishableRuntimeEvidence=false`.

The Creep is visible and owned, has two active MOVE parts, and has positive fatigue. Fatigue is the observed movement blocker. The input contains no path or movement return code, so it cannot diagnose a pathfinding failure.

## Manual fix

1. Observe fatigue on subsequent ticks and wait until it reaches zero. Do not assume the value 6 predicts an exact recovery duration without the relevant movement conditions.
2. If this repeats, review the Creep's body, carried load, and terrain in your own code; those are outside this fixture.
3. Resample the same visible, owned Creep once fatigue is zero. Editing the exercise JSON does not remove fatigue from a live Creep.

## Resample after the fix

This second JSON is also synthetic: it illustrates the expected changed observation, not a measured game outcome.

```json
{
  "version": 1,
  "symptom": "creep-not-moving",
  "creep": {
    "visible": true,
    "owned": true,
    "fatigue": 0,
    "activeMoveParts": 2
  }
}
```

Expected classification: `return-code-required`, confidence `bounded`, canonical Resolver step `move-result`. The previous blocker is absent; success has **not** been demonstrated.

## Verify in your game

Record the real move or moveTo return value from your own game logic, then compare the same Creep's position on a later tick. An accepted request is not proof that the Creep changed position. Investigate collisions, path choices, other movement requests, and destination constraints if it remains still.

No live game action was executed to validate this recipe. The examples validate the Doctor's deterministic interpretation of supplied facts only. Keep real observations private.

## Applicability limits

This exercise does not include terrain, load, boosts, path data, traffic, destinations, or conflicting intents. It does not calculate recovery time. Zero fatigue and active MOVE parts remove this particular blocker; they do not prove a traversable route or successful displacement.

The recipe does not replace the canonical Resolver or official API reference. Recheck the live game state and actual return value rather than inventing one from the snapshot.

## Official references

- [Creep.fatigue](https://docs.screeps.com/api/#Creep.fatigue)
- [Creep.move](https://docs.screeps.com/api/#Creep.move)
- [Creep.moveTo](https://docs.screeps.com/api/#Creep.moveTo)

[All recipes](../README.md) · [Synthetic-only feedback](https://github.com/ubvsuid/screeps-debugging-recipes/issues/new/choose)
