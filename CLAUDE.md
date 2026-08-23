# CLAUDE.md — bes-ips-dashboard

Conventions for Claude Code sessions in this repo.

## Finishing work: Claude merges

**Claude merges finished branches into `main`.** Do not end a task by handing
Corbett a branch to merge. This is a standing preference (confirmed
2026-08-23) and it applies to **every** repo in `~/Sessions`, not only this one.

The flow is: branch → implement → **verify** → merge to `main` → push → delete
the branch, local and remote. Do **not** open a PR unless explicitly asked.

Merging is part of the **end-of-session routine**, not an optional extra. If a
session ends with work sitting on an unmerged branch, that session is not
finished.

Two conditions on "finished", both load-bearing:

- **Merge only genuinely verified work.** Whatever this repo's gate is — tests,
  CI, a preflight, a deploy check — it passes *before* the merge.
- **Re-run that check on `main` after the merge and before the push.**
  Verifying the branch is not the same as verifying the merge result.

Merge stacked branches oldest-first. A `--ff-only` merge is a useful tell: it
succeeds only when the history is linear, so nothing is being silently
rewritten.

Note that an issue closed by a commit trailer (`Closes #12`) only actually
closes when that commit reaches the **default** branch — so an unmerged branch
quietly leaves its issues open too.
