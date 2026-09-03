# Interview, audit, and output guide

Use this guide after the destination preflight and privacy warning. Keep the process conversational: the user can answer in any language, skip any question, correct prior answers, or stop after a round.

## 1. Zero-context start and consent

Assume no personal facts at the start. Do not search for or reuse a personal profile, memory, resume, project history, or prior conversation unless the user explicitly asks to import that source. The skill itself must elicit the context through conversation.

If the invocation includes a destination directory, inspect it and list relevant existing files. If it is non-empty, do not write into it; offer a different empty directory or an audit-only session. If no destination was supplied, continue the interview without one and choose an empty destination only after the user approves the fact audit. Destination selection must not become onboarding homework.

Explain the boundary in plain language:

- This process creates a local Markdown context package; it does not create a personality diagnosis or make the AI an authority over the user.
- The user controls what to share. Avoid secrets and sensitive data unnecessary for future collaboration.
- Nothing becomes a formal file until the user approves the fact audit.

Invoking the skill is sufficient consent to begin a non-writing interview after this boundary is explained. The user may skip any question or stop at any time. Begin Round 1 in the same response; do not add a separate "reply yes to continue" gate.

## 2. Full-life or focused interview

Read and follow [the interview playbook](interview-playbook.md). Ask short, concrete questions and infer patterns only after gathering behavioral evidence. The user should recall events and choices; the agent should do the work of proposing what those examples may mean.

For a bare creation request, run the Full Personal OS path. Do not ask about the user's reason for using AI or use an AI task to steer the biography. The life interview must stand on its own and remain the same whether the eventual tool is Codex, Claude, another AI, or no AI yet. The full path may take multiple sessions. Do not announce a round count, rush toward file generation, or imply Luke OS-level depth after a few answers.

Use the Focused Context Pack path only after an explicit narrow request. Name the scoped result accurately and state which life domains remain unassessed.

Do not move to the fact audit until the selected path meets its readiness criteria. In full mode this requires a usable life chronology plus current responsibilities, direction, evidence-based patterns, and an explicit covered/skipped/not-assessed status for sensitive domains. A vague first answer is not evidence that an area is irrelevant.

If a domain needs detail but should not burden the core, propose a routed reference such as `references/CAREER.md`, `references/ASSETS.md`, `references/RELATIONSHIPS.md`, or `personal-company/OPERATING_MODEL.md`. Create none merely to imitate another Personal OS. Sensitive references require explicit approval for both their content and their retention; participating in that interview module is not automatic permission to write it.

## 3. Fact audit and approval

Before writing files, present a compact, complete audit with these four headings:

| Category | Meaning | Treatment in the files |
| --- | --- | --- |
| Confirmed facts | The user explicitly stated and affirmed it. | May enter the core or an approved reference. |
| User interpretations | The user's own meaning, preference, or framing. | Attribute it to the user; keep it revisable. |
| AI working hypotheses | A useful inference from the conversation. | Include only as a clearly labeled, revisable hypothesis after approval. |
| Needs confirmation | Ambiguous, stale, incomplete, or inferred material. | Exclude until the user confirms, corrects, or removes it. |

For each proposed item, state its destination (`ME.md`, a named reference, or excluded) and why it belongs there. Mark anything time-sensitive with a verification need. Do not include current project status in `ME.md`.

In a full-mode audit, include a short coverage statement listing domains covered, intentionally skipped, and not assessed. In a focused-mode audit, place the declared scope and unassessed life domains at the top so the package cannot be mistaken for a complete Personal OS.

Ask one unambiguous question: **"Do you approve this audit and the proposed files for writing? You may approve all, approve only named sections, or request edits."** Do not write a formal Personal OS until the user explicitly approves.

The personal fact audit covers the person, not their AI use case. After it is approved, run a separate short operational-configuration step for privacy boundaries, agent behavior, and actions requiring approval. Keep those operating rules distinct from biographical facts and do not retroactively reshape the interview around them.

## 4. Generate the minimal Personal OS

After approval, ask the user to select or approve a destination if none was supplied earlier. Inspect it and require it to be empty. For Full Personal OS mode, generate only approved files:

```text
personal-os/
├── ME.md
├── README.md
├── AGENTS.md
├── CHANGELOG.md
├── VERSION
└── references/                 # only when an approved routed module needs it
```

Do not create an empty `references/` directory, a personal-company structure, or detailed records merely for symmetry.

For Focused Context Pack mode, use a name that states the scope, such as `CAREER_CONTEXT.md`, plus only the minimal pointer and maintenance files the user approved. Do not use a generic `ME.md` in a way that implies whole-person coverage, and do not label the package a Full Personal OS.

### `README.md` requirements

Explain in plain language what the Personal OS is and is not, which file is canonical, how routed references work, how another AI can use it, how approved updates are recorded, and why credentials and live project state stay elsewhere. Keep machine-specific paths out of the canonical context. Include a short portability note: keep one private source of truth and point each AI tool to it instead of maintaining divergent copies.

### `ME.md` requirements

Keep the core compact, durable, and human-readable—often about 800–1,200 words when the interview supports that depth, with 1,500 words as a review trigger. If evidence remains sparse, continue the interview or produce a shorter honest core; never pad it with generic personality language. Use only sections justified by the approved audit. A strong default structure is:

```markdown
# [Name]'s Personal OS

> Canonical personal context for collaborating with [Name]. Keep this file compact, durable, and human-readable.

## Who I Am
## What Shaped Me              <!-- only durable, decision-relevant context -->
## What I Am Building          <!-- stable portfolio/direction, never live status -->
## Long-Term Direction
## How I Think
## Working Hypotheses About Me <!-- explicitly revisable; maximum eight -->
## How To Work With Me
## Sensitive Context           <!-- minimum necessary; no secrets -->
## Maintenance Rules
```

Do not pad empty headings. `What Shaped Me` must be grounded in the approved life-history evidence, not generic career traits. Direct the agent to load an approved reference only when relevant. The core must say that the user remains the decision-maker and that the agent may advise but cannot replace judgment or accountability.

### `AGENTS.md` requirements

Make this a concise repository-local pointer, not a second personal profile:

```markdown
# Personal OS

Before important work in this repository, read `ME.md` and use it as personal context.
Load only references routed by `ME.md` and relevant to the task.
Never modify this Personal OS without the owner's explicit approval.
Keep temporary work, project status, credentials, and secrets outside this Personal OS.
```

### Version and maintenance files

- `VERSION` starts as `0.1.0` unless the user provides a different format version.
- `CHANGELOG.md` records the initial owner-approved creation date, scope, and no unapproved claims. It must not reproduce sensitive facts.
- A detailed module must be plain Markdown, named for its actual domain, and loaded only when `ME.md` routes to it. It must include its own sensitivity and approval boundary when relevant.

After generating, list exact files created and summarize the scope that was intentionally excluded. Do not claim success before checking the files exist and match the approved audit.

## 5. Optional global Codex integration

Only after the profile is successfully written, offer Codex integration as an optional separate action. If the user declines, stop after explaining that they can upload or point tools at `ME.md` manually.

If the user wants integration:

1. Identify and inspect the actual global Codex `AGENTS.md` on the current machine. Do not assume it is empty or replace it.
2. Show the exact additive Markdown block and target path. Use an absolute path to the newly created `ME.md`.
3. Ask separately: **"Do you approve adding exactly this pointer to [path]?"**
4. On approval, make only that additive change and preserve unrelated instructions.

Use a short pointer such as:

```markdown
# Personal OS

Before important work, read `/absolute/path/to/personal-os/ME.md` and use it as personal context.
Never modify the Personal OS without the owner's explicit approval.
Keep temporary and project-specific details outside it.
```

If the global file already contains a conflicting Personal OS pointer, stop and show the conflict; never select, replace, or merge personal contexts without the owner's explicit direction.

## 6. Fresh-task verification

An edit in the current task does not prove that future tasks load it. Tell the user to open a **fresh Codex task** and send a low-sensitivity verification request, for example:

```text
Before we start, identify the personal-context file you loaded, then summarize one working preference and one approval boundary from it. Flag anything you cannot confirm from the file.
```

The result passes only if the new task identifies the correct file, accurately distinguishes known context from unknowns, and does not expose unnecessary sensitive material. If it fails, inspect the actual global configuration and the fresh-task context before proposing a repair; do not claim automatic loading based only on a same-task response.

## 7. Safe updates

For a later update, first inspect the existing profile and ask what durable fact, interpretation, hypothesis, or reference needs changing. Keep current project status in its project repository. Then propose:

- exact file and diff;
- evidence/source and confidence;
- whether the change replaces, merges, or removes an existing statement;
- any compaction needed to keep `ME.md` compact.

Require explicit approval for changes that alter meaning, remove material context, or revise working hypotheses. Apply only approved scope, update `CHANGELOG.md`, and verify the changed files. Never update based solely on an agent's new inference.
