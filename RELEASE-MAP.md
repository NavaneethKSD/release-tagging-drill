# Release Map

This map ties each established release tag to an immutable commit and its deployment meaning. Dates are commit dates from the repository history.

| Version (tag) | Commit (short hash) | Date | What Shipped |
| --- | --- | --- | --- |
| `v1.0.0` | `c17d4c4` | 2026-06-06 | Initial checkout service implementation and runnable service entry point. |
| `v1.1.0` | `82535d9` | 2026-06-06 | Checkout service naming and startup output were made explicit, including a service version value. |
| `v1.1.1` | `82535d9` | 2026-06-06 | Patch release baseline for the verified service state; no additional application change was required after the existing cleanup commit. |

The tags are annotated release markers. The last two tags intentionally share a commit because the repository contains no later application commit; the map makes that fact visible rather than implying an unrecorded code change.

## Traceable rollback

```sh
git tag --sort=-v:refname        # the sortable release history
git checkout v1.1.0              # roll back to the last known-good tag, then redeploy
```

The sortable `vMAJOR.MINOR.PATCH` sequence identifies the current release and its predecessor without interpreting names such as `latest-good`. Because each tag points to a known commit and the release map records what shipped, the rollback is precise and reproducible instead of guesswork.