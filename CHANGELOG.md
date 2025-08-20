# Changelog

All notable changes to this project will be documented in this file.

This project adheres to [Semantic Versioning](https://semver.org) and follows the spirit of [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Planned

* Special‑case well‑known files without extensions (e.g., `Dockerfile`, `Makefile`, `.gitignore`).
* Configurable output template (header/separators/language tag behavior).
* Optional keybindings and settings.

---

## [0.1.0] — 2025-08-20

### Added

* **Triple backticks** for Markdown fences (replaces previous 6‑backtick style).
* **Language tag** appended to the opening fence, inferred from file extension (e.g., `.dart` → `dart`).
* `extToMarkdownLang` helper and `node:path` import to resolve language from file extensions.
* Per‑file separator line: `------ <relative-path> ------`.
* Updated command titles in the UI to reflect "(Fences + Lang)" behavior.

### Changed

* Clipboard/output **format** now uses triple‑backtick code blocks with optional language identifiers.
* `package.json` metadata tailored for the fork: new `name` (`copy-fences-lang`), new `displayName`, `publisher`, `license`, `keywords`, `homepage`, and `bugs`.
* Reset version to `0.1.0` for the forked line.

### Notes

* This release **may be breaking** for users relying on the old 6‑backtick format. If you require the old behavior, consider pinning the original extension or opening an issue for a compatibility toggle.

---

[Unreleased]: https://github.com/SewaraDev/vscode-copy-fences-lang/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/SewaraDev/vscode-copy-fences-lang/releases/tag/v0.1.0
