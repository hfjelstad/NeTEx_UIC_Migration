# Lifecycle — DatedServiceJourney

Profile term: DatedServiceJourney (NeTEx Part 2: DatedVehicleJourney)

Purpose
- Describe the allowed lifecycle states and transitions for a DatedServiceJourney on a specific OperatingDay.

Lifecycle states
- planned: The journey is produced from the planned ServiceJourney and published for the OperatingDay.
- reinforcement: The journey is an extra dated run created to increase capacity, referencing the journey it reinforces.
- replacement: The journey substitutes another dated journey (typically when the original is cancelled), and references the cancelled journey.
- cancelled: The journey is cancelled and must not be operated.

State transitions
- planned → reinforcement: Create an extra dated run (ReinforcementForRef required). Original remains planned.
- planned → replacement: Create a substitute dated run (ReplacementForRef required). Original may transition to cancelled.
- planned → cancelled: Cancel a previously planned dated run.
- reinforcement → cancelled: Cancel the extra dated run.
- replacement → cancelled: Cancel the substitute dated run.

Transition constraints
- A journey cannot be both reinforcement and replacement simultaneously.
- ReinforcementForRef (0..1) is mandatory when state = reinforcement.
- ReplacementForRef (0..1) is mandatory when state = replacement.
- JourneyStatus SHOULD reflect the state (planned | reinforcement | replacement | cancelled) when provided.

Operational notes
- A cancelled journey MUST NOT be allocated to a Block unless explicitly retained for historical trace; do not operate.
- Replacement and reinforcement journeys must carry the same JourneyPattern as the original unless a deviation is intentionally modelled.

References
- See Description_DatedServiceJourney.md for mapping and field cardinalities.
