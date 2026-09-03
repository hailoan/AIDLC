# /vibe — autonomous AI-DLC (vibe flow)

Run the guarded vibe flow end-to-end, no human gates: feature-analysis → solution-design →
implementation-plan → android-dev → testing → automation-test → review. Resolve the **ticket output folder**
once ($AIDLC_OUTPUT_DIR if set, else output/<ticket>/) and use it for every stage. For each
stage, use a fresh native subagent/context when the runtime supports it and return only its marker,
artifact path, and short summary before continuing. A native subagent already has its agent
definition; do not reload it. Without native isolation, read `.aidlc/agents/<stage>.md` once.
Add `--flow impl-flow` to that agent's context-loader command. Use only the resulting packet,
named prior artifacts, and applicable atomic skills. Require each stage artifact's first
line to be `AUTOMATION: CONTINUE` or
`AUTOMATION: STOP — <reason>`, and stop immediately on STOP. In android-dev, implement each parallel
wave from the plan's Dependency Map concurrently only when file ownership is disjoint; keep DI,
navigation, database schema/migrations, shared state, and build configuration serialized. Stop
and report at <ticket folder>/CODE-REVIEW.md.

## Inputs

Ask one concise question for each missing required value, in table order, then wait. Ask in the chat — one message per missing input — and wait.
Never invent identifiers, paths, or branches; do not ask for optional values.

| Input | Required | Notes |
| --- | --- | --- |
| Ticket id | **yes** | e.g. `PROJ-123` — resolves the ticket folder `output/<ticket>/` |
| BA spec / API doc | **yes** | link or file path; a non-`.md` file is converted into `output/<ticket>/input/` first |

If a required prior artifact is missing, name its producing stage and stop.

Apply it to: $ARGUMENTS
