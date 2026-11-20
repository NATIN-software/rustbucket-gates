# rustbucket-gates

Central gates for RustBucket projects. Owner-only: only the organization owner
changes this repository, and it is locked by the organization ruleset
`rustbucket-gates-lock`.

This is the spike version with a single gate, `spike-marker`: it fails when
`spike/fail.txt` exists in the pull request.

How it is required: the organization ruleset `rustbucket-default-branch`
requires the workflow `.github/workflows/rustbucket-gates.yml` from this
repository on every repository whose custom property `rustbucket` is `true`.

Do not add secrets to this repository: it is public and its workflow runs on
untrusted pull request code.
