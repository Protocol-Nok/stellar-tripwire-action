# Changelog

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added
- Composite action: downloads `tripwire` and the published corpus, runs an
  adapter, reports pass/fail/unsupported counts.
- Cross-platform self-test (Linux, macOS, Windows) against the real JS adapter.
- A second self-test proving detection: fails correctly against a pre-fix SDK.
