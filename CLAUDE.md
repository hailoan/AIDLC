# CLAUDE.md — My Project
## 0. Ground rules (read before touching anything)

1. Use a current project knowledge graph first for structural questions when it is available and
   covers the target module. Validate important results against source. Otherwise use focused text/
   symbol search and source inspection; never treat a missing graph edge as proof of no impact.
2. An authorized implementation or testing stage may run the smallest relevant compile, unit-test,
   or static-check command. Commit, push, distribution, signing, upload, and publishing always need
   separate explicit authorization.
3. Match the surrounding architecture, naming, and patterns. Project-specific invariants live in
   `.aidlc/context.md` under project ground rules.

## 0. Project ground rules

- Preserve existing XML/Fragment versus Compose ownership per screen; migration requires an
  explicit boundary decision. Treat navigation, Koin modules, Room schemas, socket/realtime state,
  notifications, call services/SDK integration, and flavor/build configuration as shared-risk
  surfaces that require caller/configuration impact checks before edits.
- Use a current project knowledge graph when available and validate it against source. Otherwise
  use focused `rg`/symbol search; never infer no callers from missing graph data.

## 1. What the app is

**My Project** (MyProject) is a **android** application.

- Language: **kotlin**
- Architecture: **clean-architecture**
- UI: **compose**
- DI: **hilt**
- SDK: min **24**, target **35**

WorkChat is an enterprise messaging application covering conversations, messages/media, search,
tasks, notifications, profile/settings, stories, calls, and realtime/offline synchronization. It
integrates backend REST/socket services, Firebase, Room, WorkManager, and the local `callsdk` and
`network` modules.

---

## Project context → `.aidlc/context.md` · AI-DLC machinery → `.aidlc/context-collection.md`

Everything specific to this codebase lives in **`.aidlc/context.md`**: modules,
architecture, data, UI, DI, storage, naming, testing, and high-risk areas. Stages
load only their relevant topics through `.aidlc/lib/stage-context.js`; section
numbers may differ between projects.

The generic AI-DLC machinery lives in **`.aidlc/context-collection.md`**: ground rules
(§0), planning conventions (§10), the feature→review workflow + per-stage artifact &
load contract (§11), and the testing process (§12).

Before a non-trivial change, generate the compact stage packet so the relevant
project conventions are present without loading both context files in full.
