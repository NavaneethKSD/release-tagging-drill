# Versioning Convention

This project uses Semantic Versioning with a required `v` prefix.

- **MAJOR** increments for an incompatible or breaking change. Example: `v1.4.2` -> `v2.0.0` when an API contract changes.
- **MINOR** increments for backwards-compatible functionality. Example: `v1.4.2` -> `v1.5.0` when a new optional checkout capability is added.
- **PATCH** increments for backwards-compatible bug fixes. Example: `v1.4.2` -> `v1.4.3` when a checkout timeout is fixed.

## Tag format

Production releases use exactly `vMAJOR.MINOR.PATCH`, for example `v1.1.1`. Versions are immutable: a release tag must never be moved to another commit.

## Annotated release tags

All production releases use annotated tags because the tag stores a release message, tagger, and timestamp in addition to identifying the commit. Create one with:

```sh
git tag -a v1.1.1 -m "Release 1.1.1: refine checkout service startup output"
```

Push release tags explicitly with `git push origin --tags`.

## Pre-releases

Release candidates and betas use the same version followed by a dot-separated identifier, such as `v1.5.0-rc.1` or `v1.5.0-beta.1`. Pre-releases sort before their final version, so `v1.5.0-rc.1` is tested before `v1.5.0`; the final tag is created only after acceptance.