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

## Note (2)

- Bumped the default `tripwire-version` to `v0.1.3`: `v0.1.2`'s Windows
  release asset had a bad `.sha256` sidecar (CRLF line ending) that this
  action's own first real Windows CI run caught. Fixed upstream; see
  stellar-tripwire's changelog.

## Note (3)

- Bumped the default `tripwire-version` to `v0.1.4`. No action-interface change
  needed: v0.1.4 only changed the corpus content (adds a captured entry), and
  this action always pulls the corpus from stellar-tripwire-corpus@main
  independently of the pinned binary version.
