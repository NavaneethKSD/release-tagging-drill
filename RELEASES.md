# Release Notes

## v1.1.1 - 2026-06-06

**Added**

- A verified patch release marker for the current checkout service state.

**Changed**

- Formalized the release point as an annotated semantic version tag.

**Fixed**

- Removed ambiguity about the exact commit used for this release by recording it in `RELEASE-MAP.md`.

**Rollback target:** `v1.1.0`, the previous known-good checkout service release.

## v1.1.0 - 2026-06-06

**Added**

- Explicit `checkout-service` naming and service version output.

**Changed**

- Replaced the placeholder startup function with the runnable `run()` entry point.

**Fixed**

- Made startup output identify the service and its reported version.

**Rollback target:** `v1.0.0`, the initial known-good checkout service release.

## v1.0.0 - 2026-06-06

**Added**

- Initial runnable checkout service implementation.

**Changed**

- Established the first release baseline for deployment tracking.

**Rollback target:** No previous release; this is the first known-good version in the new release sequence.