# Agent Lifecycle Framework

A working framework for analyzing the full lifecycle of AI agents — from the irreducible primitive they are built around, through composition, deployment, operational coupling, and the dynamics that govern how they collide with the systems they are deployed into.

## What this is

This repository contains a structural framework for diagnosing what goes wrong across the lifecycle of AI agents — engineered composites built around large language models — when they are deployed into the kinds of coupled engineered systems that organizations actually run. It is an analytical document rather than a software framework. It identifies the primitive that AI agents are built around, the composition path from primitive to autonomous system, the deployment error that produces the central failure mode (false closure), and the dynamics that govern how that failure propagates through coupled systems.

The framework is intended for engineers, architects, operators, and governance practitioners who have already encountered the dysfunction it names and need vocabulary, structure, and predictions they can use in their own work.

The current document focuses primarily on the deployment and operational-coupling phases of the lifecycle, which is where the central failure mode (false closure) becomes visible. Earlier phases (primitive, composition, industrialized composition) and later phases (tempo, viability, regime change) are also covered. As the framework develops, additional phases — pre-deployment design, instrumentation, governance, retirement — are candidates for further analytical attention.

## What this is not

This is not yet a software framework. There is no library to install, no agent harness to deploy, no SDK. The repository is an analytical foundation for that future work. Proof-of-concept tooling around the structural ideas — instrumentation for trajectory traces, tooling for cascade analysis over operational closures, viability-aware deployment harnesses — is plausible follow-on work but is not present here.

This is also not a peer-reviewed paper. It is a working document, calibrated for analytical density rather than academic conventions. It will be revised as additional incidents, predictions, and analytical refinements emerge.

## Contents

- **`agent_deployment_framework.pdf`** — The framework itself. Twenty-seven sections plus preface, table of contents, and references. PDF rendered from LaTeX source.
- **`agent_deployment_framework.tex`** — LaTeX source for the framework.
- **`notation_reference.pdf`** — A standalone notation reference document. Defines symbols used across the framework, the author's security talk, and related working papers. Documents conflicts, rejections, and cross-references to the broader literature.
- **`notation_reference.tex`** — LaTeX source for the notation reference.

The framework and notation reference are mutually consistent and should travel together.

## Reading order

Read the framework first. The preface explains the framework's posture and audience. The notation table in section 2 establishes conventions. Sections 1 and 3–6 develop the primitive and composition argument. Sections 7–22 develop the deployment and operational dynamics. Sections 23–27 cover tempo, viability, and the closing claim about regime change.

The notation reference is a companion document, not a prerequisite. Read it when you want to understand a specific symbol's lineage or when you are reading the framework alongside the author's other work and need a translation table.

A practitioner-facing introduction is also available as a separate piece: "Diagnosing Hidden Control Edges in Agent Systems," which compresses the framework's core diagnostic claims for engineering audiences.

## Citation

If you cite this work, please use:

> Alioto, J. P. (2026). *Agent deployment into coupled systems: A working framework* (Version 1.0). https://github.com/jpalioto/agent-lifecycle-framework

A `CITATION.cff` file is included in the repository for tools that consume that format.

## Related work

This framework is part of an ongoing body of work on AI agent deployment, security, and risk:

- **AI Security: The Geometry of Failure** — A talk on the structural geometry of language model security, presenting the transformer pipeline used as the central schematic in this framework.
- **Ambient Reachability Attacks** — A working paper on the specific attack class where credentials, tools, and context become reachable through paths the operator did not intend. Cited by section 12 of this framework.
- **Gravity of Risk** — A working paper on barrier-coordinate measurement of existential risk, providing a complementary structural lens on viability boundaries. Cited by section 27 of this framework.

## Compiling

Both PDFs compile from LaTeX source with a standard TeX Live install. Required packages are widely available: `lmodern`, `microtype`, `amsmath`, `amssymb`, `mathtools`, `booktabs`, `longtable`, `enumitem`, `mdframed`, `hyperref`, `titlesec`. To compile:

```
pdflatex agent_deployment_framework.tex
pdflatex agent_deployment_framework.tex
```

(Two passes are needed to resolve the table of contents and cross-references.)

## Versioning

This is version 1.0. Future revisions will be tagged. Substantive changes will be noted in commit messages and, eventually, in a change log section appended to the framework.

The framework's notation conventions are versioned with the framework. The notation reference holds the canonical definitions and explains the rationale behind each choice, including conflicts, rejections, and reservations against future collisions.

## Status

Working document. Stable enough to cite. Will be revised.

## License

Pending. Contact the author for licensing questions in the meantime.

## Contact

Issues are open for substantive engagement. For correspondence, the author's other channels are linked from the body-of-work papers referenced above.
