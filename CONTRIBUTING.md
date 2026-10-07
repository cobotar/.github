# Contributing to CobotAR

CobotAR spans several repositories in the [`cobotar`](https://github.com/cobotar) organisation:

| Repo | What |
|---|---|
| `protocol` | Protobuf definitions (buf), generated Go/TS/C#/Python code |
| `Authoring` | Go backend: authoring, process runtime, robot adapters, seeding |
| `web-cobotar` | Vue authoring web UI |
| `HoloCobotAR` | Unity / HoloLens AR client |
| `Fusion360Exporter` | Fusion 360 add-in that exports product and part definitions |

## Where work is tracked

All work is tracked as **GitHub issues** in the repo where the change happens, and collected on one board: **[CobotAR Roadmap](https://github.com/orgs/cobotar/projects/1)**.

### Board fields

| Field | Values | Meaning |
|---|---|---|
| Status | Backlog → Ready → In progress → In review → Done | Ready means it is specified well enough to start |
| Priority | P0 to P3 | P0 blocks other work; P3 is nice to have |
| Area | AR content model, Process/runtime, Robot/UR, Factory/scene, Tracking, Web UI, CAD/export, Security, Dev experience | The functional area. This often spans several repos |
| Size | S / M / L | Up to a day / a few days / a week or more (consider splitting) |
| Iteration | 2-week cycles | Optional; use when planning a cycle |

### Issue types and labels

- Issue **type**: Bug, Feature or Task. Choose one through the issue templates.
- Labels (the same in every repo):
  - `needs-decision`: an open design or protocol question. Decide before implementing.
  - `breaking-change`: requires a protocol release and updates in consumer repos.
  - `tech-debt`: cleanup without new behaviour.
  - `good first issue`: small and self-contained.

### Changes across repos

A change that touches several repos gets a **parent issue** where it starts (usually `protocol`), with **sub-issues** in each affected repo. The parent shows overall progress on the board.

## Conventions

- **TODO comments.** Small, local TODOs can stay as comments. Anything that needs a decision or spans repos becomes an issue, and the comment points to it: `// TODO(#42): ...` or `// TODO(cobotar/protocol#7): ...`.
- **Commits** follow Conventional Commits, as the existing history does: `feat(ar): ...`, `fix(seeding): ...`, `refactor(authoring): ...`. Breaking protocol changes use `!`: `feat(ar)!: ...`.
- **New issues go on the board.** Issues created with the web form are added automatically. With `gh`, pass `--project "CobotAR Roadmap"` to `gh issue create`. As a fallback, the `add-to-project` GitHub Action in each repo adds any new issue. Set Status, Priority, Area and Size on the board afterwards.
- **Closing issues.** Write `Fixes cobotar/<repo>#<n>` in a commit or PR description. It closes the issue on merge, and the board moves it to Done.
- **Protocol releases.** Bump the version in `protocol`, update `CHANGELOG.md`, then update the consumers. Each consumer has a sub-issue.

## Working with AI assistants

Each repo has an `AGENTS.md` with these rules (Claude reads it through `CLAUDE.md`). When Claude, ChatGPT/Codex or another assistant is connected to GitHub, it should:

1. look for an existing issue before creating one,
2. create issues with the templates' structure (type, labels, permalinks, "Done when"),
3. reference issues in commits and TODOs as described above.
