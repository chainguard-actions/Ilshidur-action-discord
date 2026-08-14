<!-- markdownlint-disable -->

# Hardening Report: Ilshidur--action-discord/0.3.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **Ilshidur--action-discord/0.3.1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file uses `Ilshidur/action-discord@master` (a mutable branch reference) in two steps. These should be pinned to a full 40-character commit SHA to prevent supply-chain attacks. Failing references: `uses: Ilshidur/action-discord@master` (appears twice).

Locations:

- `.github/workflows/main.yml:18`
- `.github/workflows/main.yml:22`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key and the only job (`build`) also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the default (often broad) repository permissions. A minimal `permissions:` block should be added.

Locations:

- `.github/workflows/main.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

1. Pinned both `uses: Ilshidur/action-discord@master` references to the full commit SHA `d2594079a10f1d6739ee50a2471f0ca57418b554` with a `# master` comment for readability. 2. Added `permissions: {}` at the top level of the workflow to enforce least-privilege — the workflow only sends Discord notifications via a webhook secret and requires no GitHub API permissions.

