# Contributing

Thanks for helping. This tap packages Tenjin's command-line tools for Homebrew.

## Where things go

- **A package fails to install, upgrade or uninstall:** [open an issue here](https://github.com/tenjin/homebrew-tap/issues/new/choose).
- **A problem with a tool once it is installed:** open an issue in that tool's repository, such as [tenjin-cli](https://github.com/tenjin/tenjin-cli/issues).
- **A security problem:** report it privately; see [SECURITY.md](SECURITY.md).
- **Your Tenjin account or SDK integration:** [support@tenjin.com](mailto:support@tenjin.com).

## Changing a package

The files under `Casks/` and `Formula/` are written by each tool's release pipeline, and the next release replaces any hand edit. To change a package, change the tool's release configuration (for the Tenjin CLI, `homebrew_casks` in its `.goreleaser.yaml`) in the tool's repository.

Changes to this repository itself (the README, CI, templates) are welcome as pull requests. CI style-checks and audits the packages a pull request changes, and installs every package on macOS and Linux; see [the README](README.md#maintaining-the-tap).

## Pull requests

- Keep each pull request to one change.
- Write commits and the pull request's title as [Conventional Commits](https://www.conventionalcommits.org/): `feat:`, `fix:`, `docs:`, `ci:` or `chore:`.
- A maintainer reviews every pull request, release pull requests included, before it is merged.

By contributing, you agree that your contribution is licensed under the [MIT License](LICENSE).
