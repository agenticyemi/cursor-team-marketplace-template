# Approval Policy

This document is the Quinto Auto Approval source of truth for this repository.

Risk is judged from the **files and behavior a pull request actually changes**. When risk is unclear, prefer human review. Do not infer intent from the PR title, labels, or author comments.

## Auto-approve (Very Low / Low only)

Auto-approve **only** when **all** of the following are true:

1. The change is **documentation, typo, or comment-only**.
2. Every changed path is one of:
   - files under `docs/`
   - README markdown typo or wording-only edits at the repository root (`README.md`)
3. There is **no** code, config, workflow, script, plugin manifest, skill, agent, hook, or marketplace change.
4. Assessed risk is **Very Low** or **Low**.

Examples that may auto-approve:

- Fix a typo or add one clarifying sentence in `docs/add-a-plugin.md`
- Correct spelling or grammar in `README.md` without changing install, auth, or operational instructions that alter behavior

## Never auto-approve

Never auto-approve a pull request that touches **any** of:

- `plugins/`
- `.cursor-plugin/`
- `.github/`
- `scripts/`
- auth, billing, security, secrets, credentials, tokens, OAuth, webhooks, or equivalent paths
- CI, deploy, hook, MCP, or marketplace manifest files
- any mix of the above with documentation (the sensitive path wins)

These changes require a human reviewer even when the diff looks small.

## Medium and High

- **Medium and above:** require human reviewers. Do not auto-approve.
- **High:** never self-approve. A human who did not author the change must review.

## Ambiguity

If the risk rating is uncertain, the files sit outside the Very Low / Low allowlist, or a documentation edit could change operational, security, or plugin behavior, **do not auto-approve**. Route to a human.
