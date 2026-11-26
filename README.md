<div align="center">

# homebrew-tap

**Homebrew formulae and casks for ChordSketch and jamuru.**

[![CodeQL](https://github.com/koedame/homebrew-tap/actions/workflows/codeql.yml/badge.svg)](https://github.com/koedame/homebrew-tap/actions/workflows/codeql.yml)
![License: MIT](https://img.shields.io/badge/license-MIT-0f7b6c)
![Platform: macOS and Linux](https://img.shields.io/badge/platform-macOS%20%7C%20Linux-0f7b6c)

[What you can install](#what-you-can-install) · [Install](#install) · [Update and remove](#update-and-remove) · [License](#license)

</div>

This tap installs [ChordSketch](https://github.com/koedame/chordsketch) (a ChordPro parser and renderer, as a command-line tool and as a desktop app) and the [jamuru](https://github.com/koedame/jamuru-client) pre-release (low-latency P2P audio for musicians). The software itself lives in those repositories; this one only holds the Homebrew definitions.

## What you can install

| Name | What you get |
|---|---|
| `chordsketch` (formula) | The `chordsketch` command-line tool, prebuilt. macOS (Apple silicon, Intel) and Linux (arm64, x86_64) |
| `chordsketch` (cask) | The ChordSketch desktop app: live preview, transpose, PDF export. Prebuilt, not yet signed by Apple. macOS 12 or later |
| `chordsketch-desktop` (formula) | The same desktop app, built from source on your machine (Homebrew installs the build tools it needs). macOS |
| `jamuru@beta` (cask) | The jamuru pre-release, not notarized by Apple yet. macOS 11 or later |

`chordsketch` is both a formula and a cask, so the commands below say which one with `--formula` or `--cask`.

## Install

Name the tap in full. Homebrew 6.0.0 and later refuse to load anything from a third-party tap you have not trusted, and the full name taps `koedame/tap` and trusts just that one formula or cask.

```sh
# ChordSketch command-line tool
brew install --formula koedame/tap/chordsketch

# ChordSketch desktop app (prebuilt)
brew install --cask koedame/tap/chordsketch

# ChordSketch desktop app (built from source)
brew install koedame/tap/chordsketch-desktop

# jamuru pre-release
brew install --cask koedame/tap/jamuru@beta
```

To install by short name instead, tap and trust it once:

```sh
brew tap koedame/tap
brew trust koedame/tap
brew install --formula chordsketch
```

The prebuilt ChordSketch desktop app is not signed or notarized yet, so macOS blocks its first launch. After installing the cask, run this once, or choose "Open Anyway" in System Settings → Privacy & Security:

```sh
xattr -dr com.apple.quarantine /Applications/ChordSketch.app
```

`jamuru@beta` clears that flag for you when you install it with `brew install --cask`. It cannot be installed together with a `jamuru` cask.

## Update and remove

```sh
brew update
brew upgrade --formula chordsketch      # or: brew upgrade --cask chordsketch
brew uninstall --formula chordsketch    # or: brew uninstall --cask chordsketch
```

The definitions are updated after each release of the software they install, so `brew upgrade` follows the releases.

## Security

To report a problem with a definition in this repository (a wrong download URL or checksum, or a definition that runs unexpected commands), see [SECURITY.md](SECURITY.md). Problems in the applications themselves belong in their own repositories.

## Trademarks

Homebrew, macOS, and Linux are trademarks of their respective owners. This tap is not affiliated with or endorsed by them.

## License

The MIT License in [LICENSE](LICENSE) applies to the formula and cask definition files in this repository.
It does not apply to the software those files install. Each application is distributed under its own license, which is stated in its own repository (and in the `license` field of a formula, where the format has one).
