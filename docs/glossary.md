# ATMS Glossary

This glossary defines the core terms used in the Adaptive Topological Motion System (ATMS).

All terms are defined within the context of ATMS and may differ from their usage in animation, robotics, or machine learning literature.

---

## Action Grammar

A formalized set of abstract action tokens that describe *how* an entity behaves.

In ATMS, actions are not animations or poses, but symbolic instructions applied to topological relationships.

---

## Action Token

The minimal unit of behavior in ATMS.

An action token represents an abstract operation (e.g. expand, oscillate, propagate) that can be applied to one or more topological elements.

Action tokens do not assume anatomy or physical form.

---

## Arbitrary Morphology

Any form that does not rely on predefined anatomical templates such as humanoid skeletons.

An arbitrary morphology may be asymmetric, recursive, non-biological, or dynamically changing.

---

## Coherence

The property that ensures generated behavior remains continuous, interpretable, and stable over time.

In ATMS, coherence is enforced through constraints rather than learned implicitly.

---

## Continuity Guard

A constraint mechanism that prevents discontinuities in pose, velocity, energy, or structural state.

Continuity guards ensure that stochastic action generation does not result in chaotic or invalid transitions.

---

## Edge

A relational constraint between nodes.

Edges may encode hierarchy, attachment, symmetry, influence, or dependency.

Edges define how actions propagate through a topology.

---

## Energy

A scalar or vector parameter that modulates the intensity, scale, or responsiveness of an action.

Energy is not force, but an abstract modifier used to shape behavior.

---

## Morphology

The structural configuration of nodes, edges, and parameters at a given moment.

In ATMS, morphology is mutable and does not define identity.

---

## Undifferentiated Morphology

A morphology that lacks distinct or identifiable structural features.

In ATMS, undifferentiated morphologies are not treated as invalid.  
Instead, they are initialized through uniform or quasi-uniform distribution of latent nodes across the available form space.

This process establishes a minimal topological substrate upon which actions and future differentiation may occur.

---

## Feature Seeding

The process by which latent or inherited features are distributed across a topology.

When a morphology originates from an undifferentiated state, features may be seeded evenly or stochastically across nodes.

Feature seeding defines *potential for differentiation*, not fixed structure.

---

## Feature Redistribution

A mechanism by which inherited features are reassigned across a topology during combination, reproduction, or hybridization events.

Rather than inheriting complete structures, descendant morphologies receive redistributed features at the node or relational level.

Redistribution is stochastic but constrained by topological validity.

---

## Inheritance Event

An operation in which two or more morphologies contribute features to a resulting morphology.

Inheritance in ATMS does not imply biological reproduction, but topological recombination.

Feature allocation during inheritance may be randomized, redistributed, or partially preserved.

---

## Constraint-Bounded Learning

A generation paradigm in which machine learning models propose morphological or behavioral structures within predefined system constraints.

In ATMS, learning mechanisms do not replace rules, but operate inside coherence, continuity, and topological validity bounds.

---

## Node

The fundamental unit of transformation in a topological entity.

A node may represent a point, segment, cluster, or abstract control element.

Nodes do not imply joints, bones, or limbs.

---

## Proposal Layer

An optional mechanism that suggests candidate actions or parameters.

Proposal layers may be procedural, rule-based, or machine-learning-driven, but do not define system behavior on their own.

---

## Semantic State

A high-level descriptive state that contextualizes behavior.

Semantic states may be provided by external systems such as RTIS.

---

## Stochastic Action

An action selected through probabilistic methods within constrained action spaces.

Randomness in ATMS operates only within coherence bounds.

---

## Topological Entity

An entity defined by nodes, edges, and parameters rather than by geometry or anatomy.

Topological entities are the primary subjects of ATMS-driven behavior.

---

## Topological Validity

The condition that ensures an action respects the structural rules of a topology.

Actions that violate topological validity are rejected or corrected.

Extend glossary with morphology initialization and inheritance rules

