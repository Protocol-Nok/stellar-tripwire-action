# stellar-tripwire-action

[![test](https://github.com/Protocol-Nok/stellar-tripwire-action/actions/workflows/test.yml/badge.svg)](https://github.com/Protocol-Nok/stellar-tripwire-action/actions/workflows/test.yml)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)

**Run the [stellar-tripwire](https://github.com/Protocol-Nok/stellar-tripwire) ledger conformance corpus against your SDK or indexer adapter, in CI.**

Downloads the `tripwire` binary and the published
[corpus](https://github.com/Protocol-Nok/stellar-tripwire-corpus), runs your adapter
against it, and fails the job if anything disagrees with the network.

## Usage

Write an adapter for your SDK or indexer first — see
[stellar-tripwire's adapter protocol](https://github.com/Protocol-Nok/stellar-tripwire/blob/main/docs/adapter-protocol.md).
The [JS adapter](https://github.com/Protocol-Nok/stellar-tripwire/tree/main/adapters/js)
is a working example.

```yaml
- uses: actions/checkout@v4
- uses: Protocol-Nok/stellar-tripwire-action@v1
  with:
    adapter: "node ./my-adapter.mjs"
```

## Inputs

| Input | Default | Meaning |
|---|---|---|
| `adapter` | *(required)* | Command that runs your adapter. The corpus directory is appended as its last argument. |
| `tripwire-version` | `v0.1.5` | Release tag of `stellar-tripwire` to run. |
| `corpus-ref` | `main` | Git ref of `stellar-tripwire-corpus` to test against. |
| `fail-on-unsupported` | `false` | Also fail the job if any check comes back `unsupported`. |

### Path separators

`adapter` runs through Git Bash even on Windows, and this action inserts it
*unquoted* into that shell's command line on purpose, so e.g. `"node ./x.mjs"`
becomes two separate arguments rather than one. Bash strips backslashes from
unquoted text, treating them as escapes — so a Windows-style path (anything
built from `github.workspace` on a Windows runner, for example) gets corrupted.
**Use forward slashes and relative paths in `adapter`**, e.g. `node
ref-adapter/adapter.mjs`, which work on all three platforms; this is also what
`.github/workflows/test.yml` does.

## Outputs

`pass`, `fail`, `unsupported` — the counts from the run.

## How this is tested

`.github/workflows/test.yml` runs this action on Linux, macOS and Windows against
the real JS adapter cloned from `stellar-tripwire`, not a stub, and requires zero
failures against the current `@stellar/stellar-sdk`. A second job points it at a
pre-fix SDK release and requires the action to report exactly the three known
failures, proving it can actually catch something, not just pass by default.

## License

Apache-2.0.
