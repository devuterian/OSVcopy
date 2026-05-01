# OSVcopy Status

Current accepted operational reality for this repo.

## Snapshot

- **Last updated:** 2026-05-02
- **Overall posture:** `active`
- **Current focus:** Public OSS maintenance; align repo with [LPFchan/repo-template](https://github.com/LPFchan/repo-template) (records, hooks, CI).
- **Highest-priority blocker:** none
- **Next operator decision needed:** whether to pursue Apple notarization for releases.
- **Related decisions:** none

## Current State Summary

**OSVcopy 1.0.0** is published on GitHub Releases as a **DMG**. The codebase is SwiftPM on **macOS 13+**. Repository operations now follow repo-template: `records/*`, `skills/`, commit provenance hooks, and CI commit-standards plus Swift build.

## Active Phases Or Tracks

### Template adoption

- **Goal:** Match LPFchan/repo-template scaffold (policy, hooks, skills, workflows).
- **Status:** `in progress`
- **Why this matters now:** Single operator + agents need a shared contract for commits and artifacts.
- **Current work:** Land scaffold files; migration commit; policy in `records/REPO.md` only.
- **Exit criteria:** Hooks installed by default for contributors who run `install-hooks.sh`; CI green on `main`.
- **Dependencies:** none
- **Risks:** Contributors unfamiliar with `LOG-*` commits; mitigated via `records/REPO.md` and `skills/commit-generator/SKILL.md`.
- **Related ids:** none

## Recent Changes To Project Reality

- 2026-05-02
  - **Change:** Open-sourced app; added GitHub Actions Swift CI; released DMG 1.0.0.
  - **Why it matters:** Establishes public baseline for issues and PRs.
  - **Related ids:** none

## Active Blockers And Risks

- **Risk:** Unsigned macOS binaries may trigger Gatekeeper friction.
  - **Effect:** Support burden; users must follow README security steps.
  - **Owner:** operator
  - **Mitigation:** Document clearly; consider notarization in `PLANS.md`.
  - **Related ids:** none

## Immediate Next Steps

- **Next:** Confirm `commit-standards` and `ci` workflows pass on `main` after template merge.
  - **Owner:** operator / agents with push access
  - **Trigger:** post-merge CI run
  - **Related ids:** none
