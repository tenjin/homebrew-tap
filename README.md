# Tenjin Homebrew Tap

[Homebrew](https://brew.sh) packages for [Tenjin](https://tenjin.com)'s command-line tools, on macOS and Linux.

## Install

```sh
brew install tenjin/tap/<name>
```

The first install adds the tap. You can also add it yourself and then use short names:

```sh
brew tap tenjin/tap
brew install <name>
```

## Packages

| Name | Kind | What it is |
|---|---|---|
| `tenjin` | cask | The [Tenjin CLI](https://github.com/tenjin/tenjin-cli): integrate and verify the Tenjin SDK from your terminal. |

## Update and remove

```sh
brew update && brew upgrade <name>
brew uninstall <name>
brew untap tenjin/tap   # once nothing from the tap is installed
```

## What you are installing

- Each package downloads its tool's release archives from that tool's GitHub releases, and pins their SHA-256 checksums. Homebrew refuses a download that does not match.
- Packages are written by each tool's release pipeline, from the same release, and proposed here as a pull request that CI tests and a person reviews before it is merged.
- The Tenjin CLI's macOS binaries are not notarized yet, so its cask removes macOS's quarantine attribute from the `tenjin` binary after install; otherwise macOS would refuse to run it. The step is the `postflight_steps` block in `Casks/tenjin.rb`.

## Problems

- **With a tool itself:** open an issue in that tool's repository, linked above.
- **With installing from this tap** (a failed download, a checksum mismatch, an upgrade that breaks): [open an issue here](https://github.com/tenjin/homebrew-tap/issues/new/choose), with the output of `brew config` and `brew doctor`.
- **A security problem:** see [SECURITY.md](SECURITY.md). Please do not open a public issue.

## Maintaining the tap

Packages are generated. Each tool's release proposes its own file here, and the next release overwrites a hand edit, so change the tool's release configuration instead.

```
Casks/     prebuilt binaries (GoReleaser's homebrew_casks)
Formula/   tools built from source, if one ever needs it
```

To add a tool:

1. Pick a name that Homebrew's own taps do not use (`brew search <name>`), so the short name stays unambiguous.
2. Release to this repository from the tool's pipeline as a pull request, for example with GoReleaser's `homebrew_casks`, `repository.pull_request.enabled: true` and a token from Tenjin's Code Ops GitHub App limited to this repository (`actions/create-github-app-token` with `repositories: homebrew-tap`). Keep pre-releases out (`skip_upload: auto`).
3. Install the generated package in the tool's own CI before it is released, as the Tenjin CLI does with a snapshot on macOS and Linux.
4. Add the tool to the table above.

Merge a release's pull request once CI passes: `brew upgrade` finds the new version only after that.

CI ([`tests.yml`](.github/workflows/tests.yml)) style-checks and audits the packages a pull request adds or changes (`brew style`, `brew audit --strict --online`), releases included. On every change, and weekly, it also installs and removes every package on macOS and Linux, with Homebrew in developer mode, so a deprecated stanza fails there before it warns users.

## License

The files in this repository are under the [MIT License](LICENSE). Each tool has its own license; see its repository.
