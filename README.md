# Agent Lifecycle Framework

> A research framework first; a software framework later.

This repository currently contains an in-progress paper and notation reference for analyzing AI-agent failure across the full lifecycle: from the LLM primitive, through agent composition and deployment, to operational coupling, false closure, stabilization, and propagation.

It does **not yet** provide an SDK, runtime, benchmark suite, deployment platform, or executable agent harness.

The intended next step is a proof-of-concept implementation that operationalizes selected parts of the framework as analysis tools, diagnostics, and stabilization checks.

---

## Status

**Current status:** research draft  
**Current artifacts:** paper + notation reference  
**Implementation status:** no SDK/runtime yet  
**Planned direction:** proof-of-concept lifecycle analysis and stabilization toolkit

---

## One-sentence thesis

AI-agent failures are not adequately explained at the level of single prompts, single model outputs, or single tool calls. They emerge across the lifecycle:

```text
LLM primitive → agent composition → deployment → operational coupling → false closure → propagation
```

---

## Core claim

The central failure mode is **false closure**: treating coherent model behavior as evidence of structural understanding, control, or safety.

Coherence is useful. Coherence is necessary for many successful agent behaviors. But coherence is not sufficient evidence that the system understands the structure it is operating inside, preserves the relevant invariants, or remains inside a viable operating regime.

---

## What this is

This is a research and analytical framework for diagnosing AI-agent failures across their full lifecycle.

It introduces vocabulary for describing failures that are not visible at the level of a single prompt, model output, tool call, eval score, benchmark result, or local incident.

The framework is intended to help analyze how failures propagate across abstraction boundaries:

```text
model behavior
  → agent composition
  → tool use
  → deployment environment
  → operational coupling
  → human interpretation
  → organizational feedback
  → downstream propagation
```

---

## What this is not yet

This is not yet:

- an SDK
- an agent runtime
- a benchmark suite
- a deployment platform
- a complete stabilization harness
- a replacement for system tests, runtime controls, policy enforcement, or security boundaries

The current repository is paper-first. Implementation is planned, but the present artifacts are conceptual, analytical, and notational.

---

## Planned direction

The goal is to build a proof-of-concept implementation that turns selected parts of the framework into executable analysis and stabilization machinery.

Possible implementation directions include:

- lifecycle-stage classification
- false-closure diagnostics
- invariant and precondition checks
- trajectory/provenance analysis
- typed transition validation
- policy and authority-boundary checks
- operational coupling maps
- propagation-risk analysis
- replayable incident traces
- stabilization checks for agent/tool workflows

The intended implementation is not to make agents “safe” by prompt instruction. The goal is to expose and constrain lifecycle-level failure surfaces that are otherwise hidden by local coherence.

---

## Repository contents

The main artifacts are:

- `agent_lifecycle_framework.pdf`  
  The primary framework paper.

- `agent_lifecycle_framework.tex`  
  LaTeX source for the framework paper.

- `notation_reference.pdf`  
  A companion reference for the notation used in the paper.

- `notation_reference.tex`  
  LaTeX source for the notation reference.

- `README.md`  
  This file.

- `LICENSE`  
  MIT License.

- `CITATION.cff`  
  Citation metadata.

Exact filenames may change as the draft stabilizes.

---

## Key concepts

### 1. LLM primitive

The framework treats the LLM as an irreducible generative primitive inside the larger agent system.

The primitive emits locally coherent continuations under a learned model and decode policy. It should not be treated as a source of guaranteed structural understanding, policy compliance, or system-level control.

The important boundary is not “prompt versus tool call.” The important boundary is where unconstrained generative continuation is accepted as sufficient evidence for action.

---

### 2. Agent composition

An agent is not just a model. It is a composed system:

```text
model + prompt/context + memory + tools + policies + validators + runtime + users + environment
```

Failures can arise from the composition even when each local component appears to behave correctly.

This is why single-output evaluation is insufficient. The relevant object is often the trajectory, not the isolated response.

---

### 3. Deployment

Deployment changes the problem.

A model behavior that looks harmless in isolation can become hazardous once connected to:

- tools
- credentials
- filesystems
- browsers
- APIs
- user accounts
- organizational workflows
- external state
- other agents
- human trust and delegation

Deployment turns text into action. That transition is where many lifecycle failures become operationally meaningful.

---

### 4. Operational coupling

Operational coupling occurs when an agent becomes connected to real systems whose state evolves as a result of the agent’s actions.

At that point, failures are no longer confined to output quality. They can alter the environment that future decisions depend on.

Examples of coupled surfaces include:

- documents
- tickets
- codebases
- calendars
- email
- databases
- deployment systems
- access-control systems
- incident workflows
- compliance artifacts
- managerial reporting loops

Operational coupling makes post-hoc explanation especially dangerous, because the system may produce a coherent story about a trajectory whose structural consequences were never actually controlled.

---

### 5. False closure

**False closure** occurs when a lifecycle actor accepts coherence as sufficient evidence of understanding, control, or safety.

The closure is “false” because the apparent explanatory or operational loop closes at the level of narrative, history, or local plausibility, while the underlying structural preconditions for safe action remain unverified.

False closure can appear as:

- a plausible post-hoc explanation
- a fluent incident summary
- a locally coherent tool-call sequence
- a passing eval result
- a clean demo
- a managerially satisfying status update
- a benchmark score treated as evidence of deployment safety
- a human accepting the agent’s explanation because it sounds structurally complete

The failure is not that coherence has no value. The failure is treating coherence as enough.

---

### 6. Historical coherence vs. structural understanding

The framework distinguishes three different notions that are often conflated.

#### Historical coherence

Can the system produce a plausible story about how it got here?

#### Operational coherence

Do the local steps appear compatible with each other?

#### Structural understanding

Does the system preserve the invariants required for safe action under the actual coupled environment?

The mistake is to infer structural understanding from historical or operational coherence alone.

A system can narrate a trajectory without understanding the structure that made the trajectory safe, unsafe, reversible, authorized, or damaging.

---

### 7. Stabilization

Stabilization means constraining the coupled system so that dangerous trajectories are prevented, interrupted, or made recoverable.

Stabilization is not the same as asking the model to behave. It requires external structure.

Potential stabilization mechanisms include:

- typed transitions
- explicit state machines
- capability separation
- authority-boundary checks
- provenance validation
- semantic validators
- invariant checks
- policy enforcement outside the model
- scoped credentials
- human approval gates
- rollback paths
- replayable audit trails
- bounded tool interfaces
- kill switches
- blast-radius containment

The framework assumes that language alone is not a security boundary.

---

### 8. Propagation

Agent failures can propagate through coupled systems.

A local failure may become a lifecycle failure when it is:

- written into persistent state
- copied into documents
- accepted into a codebase
- forwarded through email
- incorporated into planning
- used as evidence in a future decision
- embedded into another agent’s context
- treated as authoritative by humans
- converted into operational policy

Propagation is one reason false closure matters. Once coherent but structurally invalid output becomes part of the environment, future agents and humans may treat it as ground truth.

---

## Diagnostic questions

For a deployed or planned agent system, ask:

### 1. What is the irreducible primitive?

Where does the system rely on unconstrained or weakly constrained generative continuation?

What part of the workflow is not a verified transition?

---

### 2. Where is coherence being treated as evidence?

Examples:

- output fluency
- tool-call plausibility
- post-hoc explanation
- passing local tests
- successful demo behavior
- benchmark performance
- user satisfaction
- incident narrative quality

---

### 3. What invariants must actually hold?

Examples:

- authorization
- data integrity
- reversibility
- scope control
- provenance
- confidentiality
- auditability
- human accountability
- blast-radius containment
- compliance requirements
- semantic correctness
- operational recoverability

---

### 4. Where can false closure occur?

Examples:

- prompt testing
- eval design
- developer review
- tool-call inspection
- user trust
- managerial reporting
- incident review
- compliance theater
- postmortems
- agent-to-agent handoff
- persistent memory or retrieval

---

### 5. What prevents propagation?

Examples:

- typed transitions
- external policy enforcement
- state-machine constraints
- capability separation
- replayable audit
- semantic validators
- provenance checks
- human approval gates
- rollback paths
- containment boundaries

---

## Minimal example

A user asks an agent to clean up a project repository.

The agent produces a coherent plan, identifies files that appear redundant, deletes several of them, and then provides a fluent explanation:

> “I removed obsolete files that were no longer referenced by the active build.”

The explanation is historically coherent. The local tool calls may appear operationally coherent. The repository may even pass a shallow test suite.

But the action may still be structurally invalid if:

- the files were used by a deployment script
- the test suite did not cover production paths
- the agent inferred “obsolete” from textual similarity rather than actual dependency structure
- the human accepted the explanation as evidence of understanding
- the deletion propagated into a release branch
- future agents treated the cleaned repository as authoritative

The failure is not merely that the model made a mistake. The lifecycle failure is that the system accepted coherence as evidence of control.

That is false closure.

---

## Relationship to agent safety and evaluation

This framework is adjacent to, but distinct from:

- prompt engineering
- model alignment
- agent benchmarking
- eval design
- runtime monitoring
- governance workflows
- software lifecycle management
- incident analysis
- AI safety policy

The framework’s emphasis is structural: how agent failures emerge and propagate across lifecycle boundaries.

It is not primarily asking:

> Did the model produce a good answer?

It is asking:

> Where did the system treat local coherence as sufficient evidence for safe continuation?

---

## Design stance

The framework starts from several working assumptions:

1. **The model is not the agent.**  
   The agent is the composed system around the model.

2. **The output is not the trajectory.**  
   A single response may hide lifecycle-level failure.

3. **Coherence is not understanding.**  
   Coherent behavior is evidence of local compatibility, not necessarily structural control.

4. **Prompts are not security boundaries.**  
   Language can guide behavior, but it cannot enforce non-bypassable authority separation.

5. **Deployment changes semantics.**  
   Connecting a model to tools, state, credentials, and organizations changes the failure surface.

6. **Post-hoc explanation is not verification.**  
   A coherent explanation can be useful evidence, but it is not proof that required invariants held.

7. **Stabilization requires external structure.**  
   Reliable control requires constraints outside the model’s fluent continuation dynamics.

---

## Intended audience

This work is intended for:

- AI engineers
- ML engineers
- software architects
- safety researchers
- security engineers
- platform engineers
- agent-framework designers
- technical policy researchers
- incident reviewers
- organizations deploying AI agents into coupled workflows

It is especially aimed at readers who need to reason about agent behavior beyond isolated prompts, demos, benchmarks, or model-card claims.

---

## Citation

If you use this work, cite the repository using the included `CITATION.cff`.

A stable citation format will be added as the draft matures.

---

## License

MIT License.

See `LICENSE`.

---

## Current caveat

This is an early research draft.

Terminology, notation, artifact names, and implementation plans may change. The central direction is stable: develop a lifecycle-level framework for analyzing how AI-agent failures emerge, falsely close, stabilize or destabilize, and propagate through coupled systems.
