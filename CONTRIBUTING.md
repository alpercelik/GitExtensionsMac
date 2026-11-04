# Contributing to GitExtensionsMac

Thanks for your interest in contributing. GitExtensionsMac is an unofficial native macOS port of [Git Extensions](https://github.com/gitextensions/gitextensions), written in Swift and AppKit.

## The goal is parity

Git Extensions is the reference. Changes should reproduce its behavior, workflows, Git semantics, validation, defaults, and layout as closely as practical on macOS, rather than redesign them.

- Before implementing a feature, read how upstream does it, not only the obvious `Form*.cs` file: follow its entry points, command construction, parsing, settings, and tests.
- Platform translations are expected where Windows integrations do not apply: native AppKit controls, SF Symbols, Finder, Keychain, and OpenSSH. Mention any intentional difference from upstream in your pull request.
- Do not ship enabled placeholder controls for unfinished features.

## Code guidelines

- Module dependencies flow one way: `GitExtensionsCore -> GitCommands -> GitUI -> GitExtensionsMac`.
- GitExtensionsMac runs the real `git` executable through the existing `GitCommand` infrastructure. Pass arguments as arrays; do not build shell command strings or run Git through a shell.
- Keep Git output parsing out of UI code.
- Do not add code comments. Prefer clear names and small, focused changes.
- Avoid unrelated refactoring in feature or bug fix pull requests.

## Building and testing

Requires macOS 14 or later and Xcode 27.

```sh
open GitExtensionsMac.xcodeproj
Scripts/test.sh          # all suites
Scripts/test.sh unit     # unit tests only
Scripts/test.sh git      # Git integration tests
Scripts/test.sh ui       # UI integration tests
```

Tests use Swift Testing and create disposable repositories in a temporary directory. Never point tests or manual experiments that change repository state at a real repository you care about.

For Git workflows, assert the resulting repository state (refs, HEAD, index, working tree, config, stash) rather than only the exit code. New behavior should come with deterministic tests where practical.

## Pull requests

- Keep each pull request focused on one feature or fix.
- Describe what changed, how it compares to Git Extensions, and how you tested it.
- Make sure `Scripts/test.sh` passes and CI is green.

## Reporting issues

Use the [issue templates](https://github.com/norgera/GitExtensionsMac/issues/new/choose). Report problems with this port here, not to the upstream Git Extensions project.

## License

By contributing, you agree that your contributions are licensed under the [GNU General Public License v3.0](LICENSE).
