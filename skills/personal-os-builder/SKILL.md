---
name: personal-os-builder
description: Build, audit, or safely update a portable Personal OS that gives coding agents durable user context. Use for a guided personal-context interview, a Personal OS profile, or Codex context integration; not for ordinary project documentation or credentials.
metadata:
  short-description: Build a portable Personal OS for coding agents
---

# Personal OS Builder

Help the user create a compact, portable Markdown context system that lets agents understand their durable background, direction, working style, and decision boundaries. It is personal context, not an autonomous agent, a personality diagnosis, a project-status database, or a credential store.

## Zero-context default

When create mode is invoked, assume nothing about the person. Do not require a resume, questionnaire, biography, existing profile, or prepared background. Do not import facts from host memories, prior personal-context files, unrelated repositories, or other conversations unless the user explicitly selects that source for this Personal OS. Learn the person through this skill's interview and treat only their answers in the current run as candidate profile content.

First identify the mode:

- **Create — Full Personal OS (default):** A bare invocation such as “建立我的 Personal OS” means a whole-person interview. Build a durable life-context system from the user's chronology and current reality: early life and family context, education, work and projects, important relationships, money and risk, health and energy, present responsibilities, direction, and repeated choices. Some domains are sensitive and optional.
- **Create — Focused Context Pack (explicit only):** Use a narrower interview only when the user explicitly asks for a quick version or a single-domain pack such as career-only, founder-only, or coding-collaboration context. Label the result accurately; do not present it as a complete Personal OS.
- **Audit:** Inspect an existing Personal OS and report gaps, conflicts, stale claims, privacy risks, and compaction opportunities without changing files unless the user separately asks for edits.
- **Update:** Inspect the existing system, then follow the safe-update protocol in the guide. Do not restart the creation interview or require an empty destination.

In full mode, do not ask why the user wants AI, what they want AI to help with, or which AI use case matters most. AI use purpose must not select, reorder, shorten, or deepen the life interview. First understand the person independently of any tool or task. Only after the personal fact audit is complete may the workflow separately configure how an agent should read the approved context and collaborate with its owner.

Do not ask the user to choose between full and focused mode after a normal bare invocation; start full mode unless they explicitly requested a narrow result.

## Start safely

In create mode, begin the privacy explanation and first interview round immediately. If the user already selected a destination, inspect it before writing and report any collision. If no destination was supplied, do not block the interview or ask the user to prepare one; defer destination selection and inspection until after the fact audit is approved. Do not create formal profile files, overwrite anything, or edit Codex configuration at this stage.

Give a short privacy warning: do not collect or store passwords, API keys, recovery codes, verification codes, private keys, or full payment-account numbers. Invite the user to omit, generalize, or keep locally sensitive information. Do not imply that an AI service, its logs, or a local computer is private by default.

Then run the relevant mode in [the interview and output guide](references/interview-and-output.md). For create mode, also read and follow [the evidence-led interview playbook](references/interview-playbook.md). It prevents abstract self-analysis questions and defines how to uncover durable context from concrete events, choices, and tradeoffs.

## Core invariants

- Use short adaptive rounds, normally one to three concrete questions at a time. Continue until the required evidence coverage is sufficient; do not stop merely because a fixed round count was reached.
- Expect a full Personal OS interview to take multiple rounds and sometimes multiple sessions. Do not rush from a few answers into a generic profile or a fact audit.
- Ask the questions yourself. A bare `$personal-os-builder` invocation is sufficient to start; never tell the user to prepare a separate biography or complete an external questionnaire first.
- Do not ask the user to diagnose their own personality or name their "formative experiences." Elicit specific events, decisions, conflicts, repeated behavior, and outcomes; propose interpretations separately for confirmation.
- Move through the user's life chronologically before extracting traits. Cover the baseline whole-person domains in full mode; record a sensitive domain as skipped or not assessed when the user declines it rather than filling the gap with an inference.
- Before entering childhood/family, relationships, finances/assets, or health, briefly explain why that domain may affect present decisions and explicitly allow the user to skip it, keep it high-level, or exclude it from files. Never assume trauma, diagnose the user, or press for intimate details.
- Treat "I don't know" as a signal to change the question, not as evidence that the person has no relevant history or preference. Offer concrete memory anchors or a simple comparison.
- Keep confirmed facts, the user's interpretations, AI hypotheses, and unresolved items visibly separate. Never turn an AI inference into a profile fact.
- Present a complete fact audit and require the user's explicit approval of the reviewed content before writing any formal Personal OS file.
- Keep only durable cross-context information in the core. Put current project status, temporary tasks, and implementation details in their project repositories or explicitly scoped references.
- Create only the minimal approved files in an empty destination. Never silently merge into or overwrite an existing Personal OS.
- Offer global Codex `AGENTS.md` integration only after the profile exists. Inspect the actual file and show the exact additive pointer before requesting a separate explicit approval.
- Treat later changes as proposals: show the reason, evidence, confidence, and exact diff; apply only approved scope and record approved changes in `CHANGELOG.md`.

## Completion

Completion means the user has a reviewed, owner-approved local Personal OS and, if they chose Codex integration, a fresh-task verification that demonstrates the actual pointer was loaded. Do not claim persistent loading from a same-task response or an unverified configuration edit.
