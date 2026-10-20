# Changelog

Newest block on top. One block per publishing change. Each line names its work item key
where one exists; a small correction is just described. This file, the pull request and
the published release notes together are the ISO 9001 change record for firmware
published from this repository (see `AGENTS.md`).

## [Unreleased]

### Added

- Scotty AI 3Q 2026 builds for all four lines: V2 2.6.3.2, V3 3.2.1.7, V4 4.0.0.6 and
  IdleX 4.0.1.2-IdelX, each with its customer changelog and compatibility notes. Every
  binary was verified before publishing: ESP32 image magic `0xE9`, the version string
  present inside the image, and the SHA-256 recorded in its release notes.
- One folder per product line: `scotty/`, `startank/`, `starpower/`, `starlight/`,
  `starrover/`, `starcustom/`. Folders rather than branches, because the app reads these
  over plain HTTPS and needs a stable path; lower case, because
  `raw.githubusercontent.com` is case-sensitive and the difference between `Startank` and
  `startank` stays invisible until a download fails on a customer's phone.
- Contributor rulebook, Claude entry point and this changelog, adopting
  `Safiery/safiery-engineering-standards` at `c0d8d67`.

### Changed

- The IdleX build is named `4.0.1.2-IdelX` in both its version and its filename, matching
  what the device reports, so version matching compares like for like instead of
  reconciling a suffix.

### Excluded deliberately

- Engineering notes from the source repository's releases are not reproduced here. They
  carry build configuration, commits, branch names and named internal discussion, none of
  which belongs on a public page.
