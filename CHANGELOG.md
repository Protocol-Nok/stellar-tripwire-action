# Changelog

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added
- Composite action: downloads `tripwire` and the published corpus, runs an
  adapter, reports pass/fail/unsupported counts.
- Cross-platform self-test (Linux, macOS, Windows) against the real JS adapter.
- A second self-test proving detection: fails correctly against a pre-fix SDK.

## Note

- Bumped the default `tripwire-version` to `v0.1.2`: `v0.1.1` had a real bug
  in `tripwire run`'s `--adapter`/`--json` flag parsing that this action's own
  first CI run against a real release caught (it's fixed upstream in
  stellar-tripwire's changelog). `v0.1.0` was never published at all. The
  action's interface hasn't changed.
