# Tag Audit

The repository's current clone has no refs under `refs/tags/`, so the legacy names below are evidenced by `docs/release-notes-old.md`, `docs/deployment-history.md`, and `docs/incident-log.md` rather than by verifiable Git objects. That absence is itself a release-control failure: the team cannot prove which commit a historical deployment used.

| Evidence | Problem | Operational and traceability risk |
| --- | --- | --- |
| `version-1.0` | Uses a word instead of the exact semantic version format and omits a patch number. | Automation and humans cannot reliably compare it with later versions, so selecting the correct rollback target is ambiguous. |
| `release_2` | Uses an ordinal label with no major, minor, or patch meaning. The incident log says it was a lightweight tag with no annotation. | The team cannot tell what changed or whether it is compatible with the failed deployment; the documented rollback already returned to an unsupported commit. |
| `1.5.0` | Is semantically shaped but omits the required `v` prefix and has no documented tag metadata. | It will not match a single release pattern, and an auditor cannot distinguish an intentional release from an arbitrary ref. |
| `v2-final-FINAL` | Contains a duplicated final marker and no machine-sortable release identity. | A second “final” or hotfix cannot be ordered predictably, making incident selection and automated deployment filtering unsafe. |
| `stable-build` | Describes a mutable status rather than an immutable release version. | “Stable” can point to a different commit over time, so the production artifact and rollback target cannot be reproduced. |
| `latest-good` | Uses a moving adjective instead of a version; deployment history records production as deployed from it. | Responders cannot identify what “good” means or compare it with the current production build during an outage. |
| `patch-new` | Calls something a patch without declaring which major/minor line it belongs to. | The release cannot be placed in sequence or mapped to a compatible previous version for rollback. |
| No local tag refs | `git tag` and `git show-ref --tags` return no tags in this clone. | Even the historical labels cannot be checked against commits, dates, or annotations; auditing and rollback are therefore guesswork. |

## Remediation

Use immutable annotated tags in the form `vMAJOR.MINOR.PATCH`, maintain a release map, and push tags alongside the release branch. The new tags and documents in this branch establish the first verifiable release sequence.