# RTIS × ATMS Interface Specification (v0.1)

This document specifies how a semantic state framework (RTIS) can interoperate with the Adaptive Topological Motion System (ATMS).

RTIS provides meaning and state transitions.
ATMS provides constrained action generation and coherent motion across arbitrary morphologies.

---

## Design Goals

- Keep RTIS and ATMS independent and replaceable.
- Allow RTIS to influence behavior without prescribing anatomy.
- Ensure ATMS can run without RTIS (default semantics).
- Make integration implementable without machine learning.

---

## Responsibility Boundaries

### RTIS Responsibilities

RTIS defines:
- What an entity is (semantic identity, state labels)
- How states transition (rules, triggers, probabilities)
- High-level context signals (mood, intent, narrative phase)

RTIS does NOT define:
- Joint-level motion
- Rig structures
- Pose sequences
- Physics or smoothing

### ATMS Responsibilities

ATMS defines:
- What actions are available under constraints
- How actions remain coherent and continuous
- How morphology is driven without anatomical assumptions

ATMS does NOT define:
- Semantic meaning of states
- Narrative logic
- Why an entity chooses an intention (that is RTIS or external logic)

---

## Interface Overview

RTIS outputs a semantic state package.
ATMS consumes this package to select an action space and generate behavior.

RTIS State Package
↓
ATMS Action Space Selection
↓
Stochastic Proposal (optional ML)
↓
Coherence & Constraint Enforcement
↓
Observable Motion / Form Change


---

## RTIS State Package (Input to ATMS)

ATMS expects a minimal set of fields. Additional fields are optional.

### Required Fields

- `state_id`  
  A stable identifier for the current RTIS state.

- `state_phase`  
  A normalized phase value in [0, 1] describing progression within the state.

- `intent_vector`  
  A compact vector describing high-level intent. Example dimensions may include:
  - activation (calm → intense)
  - openness (closed → expansive)
  - stability (stable → volatile)
  - directionality (inward → outward)

- `constraint_profile_id`  
  A reference to a constraint profile used by ATMS (e.g. strict, relaxed, experimental).

### Optional Fields

- `style_tags`  
  Symbolic labels (e.g. "dance-like", "creature", "ritual", "mechanical").

- `tempo`  
  A tempo hint; can be musical BPM or abstract pacing.

- `beat_phase`  
  If synchronized to music: a normalized beat position in [0, 1].

- `interaction_signals`  
  Signals from environment or other entities (proximity, threat, attraction, collision risk).

- `inheritance_event`  
  If a morphology combination event is triggered, a package describing parents and constraints.

---

## ATMS Outputs (Observable Layer)

ATMS produces outputs at multiple levels. Implementations may choose any subset.

### Output A: Action Trace (Recommended)

A sequence of executed action tokens with parameters.

- `tokens[]`: ordered list of action tokens
- `params[]`: per-token parameter bundles
- `timestamps[]`: token start/end markers

This output is the most portable and audit-friendly.

### Output B: Topology Transform Trace

A structured record of changes to nodes/edges/parameters.

- node additions/removals
- edge rewiring
- parameter updates

### Output C: Render/Animation Stream

Implementation-dependent pose/mesh/skeleton updates.

This is an optional downstream representation and is not required for system validity.

---

## Mapping: RTIS → ATMS Action Space

ATMS uses the RTIS state package to determine:

1. **Action Categories Enabled**
   - locomotion-like
   - oscillation-like
   - propagation-like
   - contraction/expansion
   - rotation/twist
   - fragmentation/aggregation

2. **Parameter Bounds**
   - energy range
   - frequency range
   - amplitude range
   - propagation depth
   - smoothing aggressiveness

3. **Constraint Profile**
   - continuity strictness
   - topological validity strictness
   - contact/collision enforcement level (if applicable)

RTIS does not choose specific tokens; it shapes the allowable space.

---

## Minimal Compatibility Contract

An integration is considered RTIS-compatible if:

- RTIS can provide the required fields in the State Package.
- ATMS can consume those fields and produce an Action Trace.
- The mapping is deterministic with respect to the State Package and ATMS random seed.

---

## Inheritance Event Hook (RTIS-triggered)

RTIS may trigger morphology combination by sending:

- `inheritance_event.parents[]`
- `inheritance_event.policy`
  - preserve_ratio (how much to preserve vs redistribute)
  - redistribute_strength (how aggressively to reassign)
  - validity_strictness (how strict topology constraints are)

ATMS executes the event using its own topological validity rules and records results in the transform trace.

---

## Default Behavior Without RTIS

If RTIS is absent, ATMS may operate under a default state package:

- `state_id = "default"`
- `state_phase = 0`
- `intent_vector = [0.5, 0.5, 0.5, 0.5]`
- `constraint_profile_id = "balanced"`

This ensures ATMS remains standalone.

---

## Versioning

This document defines interface version: v0.1

Changes that break the minimal compatibility contract require a major version bump.
