# rustbucket-gates

Central RustBucket gates. This repository is owner-only and locked by the
organization ruleset `rustbucket-gates-lock`. The `main` branch serves
projects; the `staging` branch serves the canary repositories.

**Status: probe-session skeleton (round 2, step 2b).** The workflow here has the
real job layout (`gates-static`, `gates-lint`, `gates-test`, aggregate
`rustbucket-gates`) but no real gates. It will be replaced by the real gates.

## Marker files

Files under `probe/` in a pull request decide what each job does:

| File | Effect |
| --- | --- |
| `probe/fail-static` | `gates-static` refuses |
| `probe/fail-lint` | `gates-lint` refuses |
| `probe/error-lint` | `gates-lint` ends with status `error` |
| `probe/fail-test` | `gates-test` refuses |
| `probe/hang-test` | `gates-test` sleeps past its timeout |

## Log lines

Each line is a marker, one space, then compact JSON:

- `RUSTBUCKET-PROBE-CONTEXT`: workflow ref and commit, repository, PR head and
  merge commits, whether this repository could be checked out at the workflow
  commit, runner image.
- `RUSTBUCKET-PROBE-TOOLS`: tool versions (or `absent`) and runner resources.
- `RUSTBUCKET-GATE-REFUSAL`: a refusal, with rule, file, line, reason and fix.
- `RUSTBUCKET-PROBE-NOTE`: free-form note (hang marker).
- `RUSTBUCKET-GATE-RESULT`: per-job result, and the aggregate result.

## Secrets

This repository is public. Never put secrets in it.
