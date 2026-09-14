# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Releases up to and including 1.6.0 are the original FaTTY, by Juho Peltonen ([juho-p/fatty](https://github.com/juho-p/fatty)). This fork continues from 1.6.0; its first release is 1.7.0.

Version headings link to the commit range for that release.

## [1.7.0]

### Added

- OSC 52 clipboard support, backported from mintty 2.6.1: applications such as tmux and neovim can set the clipboard. Gated by the new `AllowSetSelection` option, which defaults to off.
- GUI checkbox for the above under Options > Experimental (security risk), so it can be toggled live, without editing the config file or restarting.

### Changed

- The OSC/DCS string buffer is now grown on demand (up to 1 MiB), backported from mintty 2.6.1, so large OSC 52 payloads are no longer truncated.

### Fixed

- `-V` and the About box truncated the version to `major.minor`; the version text and the executable's ProductVersion now show the full version.
- Clipboard payloads past ~1.5 KB were silently truncated to a partial prefix.

---

Releases below are the original FaTTY, before this fork.

## [1.6.1]

Not a release by the original FaTTY upstream ([juho-p/fatty](https://github.com/juho-p/fatty)); that project never tagged or released anything after 1.6.0, but its master accumulated the 22 commits below before this fork branched from it. (The upstream here is FaTTY; mintty, which FaTTY derives from, is a separate project.) Those commits are the base 1.7.0 builds on, so they are recorded to account for the history between 1.6.0 and 1.7.0. Authors: paolo-sz and Juho Peltonen, with Marc Paquette and jerry.wu.

### Added

- Per-tab titles (`-t`, set before the matching `-b`), a window title that follows the active tab, and a fixed window title via `-T`.
- Prompt to close all terminals or only the active one, when closing the window with several tabs open.
- First launch opens in `$HOME`; new tabs open in the current folder.

### Changed

- Tab rendering: titles vertically centred, a maximum tab width, and spacing between the tab bar and the terminal.
- Callback cleanup on tab removal rewritten.

### Fixed

- Window and tab titles are restored on returning from full-screen applications such as mined or vi.
- The tab title stack is per tab, so pushing and popping from several tabs no longer swaps titles.
- Segfault when closing tabs (Ctrl+Shift+W) too quickly, and when opening several tabs from the command line with some never selected.
- Tab bar drawing: window padding, and tab width scaling.
- Build with newer toolchains: rc files preprocessed by hand for `windres`, `-Werror` dropped, and compilation and linking warnings fixed.
- README: spawning multiple tabs, and a section marker that is now parsed.

## [1.6.0]

### Added

- Switch/move tab entries in the menu.
- Bold font for the active tab.
- Configurable tab colours.

### Fixed

- A case-sensitivity issue.

## [1.5.0]

### Added

- Tab spawning from a shortcut.

### Fixed

- Mouse release events are no longer sent when on the tab bar.

## [1.4.0]

### Fixed

- Segfault and HiDPI scaling.
- AltGr handling.
- Tab create/close shortcuts when `Ctrl+Shift+letter` shortcuts are disabled.

## [1.3.0]

### Fixed

- Closing the window now really closes the program.
- Killing a tab now always removes it.

## [1.2.0]

### Added

- New tabs open in the active tab's directory.

### Fixed

- The tab bar is hidden when only one tab exists.

## [1.1.0]

### Fixed

- Memory leaks.
- Disabling "Bold as font" now really disables it.
- The mouse cursor is an arrow over the tab bar.

## [1.0.1]

### Added

- Installation instructions and a screenshot in the README.

### Fixed

- Incorrect bitblt, which could cause a segfault.
- Tab switching when going past the leftmost tab.
- Tabs are redrawn when a bell arrives for a background tab.

## [1.0.0]

### Added

- First release: a Cygwin terminal emulator with tabs, based on mintty.

[1.7.0]: https://github.com/coralsundy/fatty-legacy/compare/61543c0...HEAD
[1.6.1]: https://github.com/coralsundy/fatty-legacy/compare/a40b22b...61543c0
[1.6.0]: https://github.com/coralsundy/fatty-legacy/compare/15a7b54...a40b22b
[1.5.0]: https://github.com/coralsundy/fatty-legacy/compare/4f9465a...15a7b54
[1.4.0]: https://github.com/coralsundy/fatty-legacy/compare/b31bfc5...4f9465a
[1.3.0]: https://github.com/coralsundy/fatty-legacy/compare/5da6bd0...b31bfc5
[1.2.0]: https://github.com/coralsundy/fatty-legacy/compare/aa0bf1a...5da6bd0
[1.1.0]: https://github.com/coralsundy/fatty-legacy/compare/c7d23ec...aa0bf1a
[1.0.1]: https://github.com/coralsundy/fatty-legacy/compare/8fea750...c7d23ec
[1.0.0]: https://github.com/coralsundy/fatty-legacy/commit/8fea750
