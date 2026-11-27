# Contributing

This repo wraps [stellar-tripwire](https://github.com/Protocol-Nok/stellar-tripwire)'s
CLI as a GitHub Action. Changes to the corpus or the CLI's behavior belong there.
Here, contributions are about the action's interface: inputs, outputs, platform
support, and the self-test in `.github/workflows/test.yml`.

Before a PR:
```sh
# there's no build step; action.yml is read directly by the Actions runner
```
Test changes by pushing to a branch — `test.yml` runs on every push and PR, and
exercises the action against itself (`uses: ./`) on all three platforms.
