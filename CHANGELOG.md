# Changelog

All notable changes to this extension will be documented here.

## [0.1.2] - 2026-03-04

### Added
- Highlight separator lines (`---`, `===`, `***`, `___`, `--- Title ---`) inside triple-quoted strings

## [0.1.1] - 2026-03-04

### Changed
- Updated README with screenshot and improved installation instructions

## [0.1.0] - 2026-03-04

### Added
- Initial release
- Syntax highlighting for all Modelfile instructions: `FROM`, `PARAMETER`, `TEMPLATE`, `SYSTEM`, `ADAPTER`, `LICENSE`, `MESSAGE`, `REQUIRES`
- Highlighting for known `PARAMETER` names (e.g. `temperature`, `num_ctx`, `top_k`)
- Highlighting for `MESSAGE` roles (`system`, `user`, `assistant`)
- Triple-quoted string support `"""..."""` for multiline blocks
- Nested single-quoted strings inside double/triple-quoted strings
- Go template expression highlighting `{{ }}` inside `TEMPLATE` blocks
- Line comment support with `#`
- File detection for `Modelfile`, `Modelfile.*`, `Modelfile-*`, `Modelfile_*`
