# GitExtensionsMac

<img width="1371" height="832" alt="GitExtensionsMac repository browser" src="https://github.com/user-attachments/assets/25df1d74-6fc9-47d6-b240-d760a6c6f5da" />

An unofficial, native macOS port of [Git Extensions](https://github.com/gitextensions/gitextensions), built with Swift and AppKit.

The goal is parity with Git Extensions: the same workflows, Git semantics, and layout, adapted to macOS conventions where Windows-only integrations do not apply.

> [!NOTE]
> GitExtensionsMac is an independent project and is not affiliated with or endorsed by the Git Extensions team. Please report issues with this port [here](https://github.com/norgera/GitExtensionsMac/issues), not to the upstream project.

## Status

Beta. Expect bugs, incomplete features, and UI differences from Git Extensions while development continues.

## Requirements

- macOS 13 or later
- Git available on your `PATH`
- Xcode 27 to build from source

## Building

```sh
git clone https://github.com/norgera/GitExtensionsMac.git
cd GitExtensionsMac
open GitExtensionsMac.xcodeproj
```

Select the `GitExtensionsMac` scheme and run.

## Testing

```sh
Scripts/test.sh          # all suites
Scripts/test.sh unit     # unit tests only
Scripts/test.sh git      # Git integration tests
Scripts/test.sh ui       # UI integration tests
```

The tests create disposable repositories in a temporary directory and drive the real Git executable.

## Plugins

See [PLUGINS.md](PLUGINS.md) for the native plugin contract.

## License and credits

GitExtensionsMac is licensed under the [GNU General Public License v3.0](LICENSE), the same license as Git Extensions.

Git Extensions, its name, logo, and icon resources are the work of the [Git Extensions team and contributors](https://github.com/gitextensions/gitextensions/graphs/contributors). Some icons are by [Yusuke Kamiyamane](http://p.yusukekamiyamane.com/) (CC BY 3.0).
