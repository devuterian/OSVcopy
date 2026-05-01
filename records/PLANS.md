# OSVcopy Plans

Accepted future direction only. No raw brainstorms here.

## Planning Rules

- Only accepted future direction belongs here.
- Plans should be specific enough to guide execution later.
- Product or architecture rationale should link to `DEC-*` records when relevant.
- When a plan becomes current truth, reflect it into `records/SPEC.md` or `records/STATUS.md` and update this file.

## Approved Directions

### Optional Apple notarization

- **Outcome:** Release builds that open without extra Gatekeeper steps for typical users.
- **Why this is accepted:** Reduces friction for non-technical operators.
- **Expected value:** Fewer support questions; more trust in the binary.
- **Preconditions:** Apple Developer Program enrollment; signing cert and hardened runtime audit.
- **Earliest likely start:** TBD by operator
- **Related ids:** none

### Broader device coverage (documentation-first)

- **Outcome:** README and `SPEC.md` explicitly list tested camera firmware / export paths.
- **Why this is accepted:** 360 vendors evolve container formats quickly.
- **Expected value:** Clear expectations before download.
- **Preconditions:** Volunteer or operator test matrix.
- **Earliest likely start:** as issues arrive
- **Related ids:** none

## Sequencing

### Near Term

- **Initiative:** Keep Swift CI and commit standards green on every PR.
  - **Why now:** Template contract is only valuable if enforced.
  - **Dependencies:** contributor onboarding via `CONTRIBUTING.md`
  - **Related ids:** none

### Mid Term

- **Initiative:** Evaluate notarization (see above).
  - **Why later:** cost and Apple account overhead.
  - **Dependencies:** stable release cadence
  - **Related ids:** none

### Deferred But Accepted

- **Initiative:** Windows port.
  - **Why deferred:** out of scope for current `SPEC.md`.
  - **Revisit trigger:** explicit operator decision and funding/time.
  - **Related ids:** none
