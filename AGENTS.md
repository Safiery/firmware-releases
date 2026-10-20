# Safiery firmware releases - contributor rulebook

| Field | Value |
|---|---|
| Status | Active |
| Version | v0.1 |
| Owner | Adam |
| Last updated | 2026-10-20 |
| ISO-affected | yes (control of changes and documented information: ISO 9001 8.5.6 / 7.5) |
| Applies to | every change by anyone: people, Claude Code, Codex |

The one rulebook for this repository. Codex reads it directly; Claude Code loads it
through `CLAUDE.md`.

- Company standards: https://github.com/Safiery/safiery-engineering-standards
- Adopted standards revision: `c0d8d67` (README v0.15; documentation-control v0.7,
  changelog-and-versioning v0.4, security-baseline v0.3, ways-of-working v0.6).
- Human approvers: Adam, Jonathan.
- Engineering project ID: TO BE CONFIRMED BY ADAM
- Engineering task key prefix: TO BE CONFIRMED BY ADAM

The two Engineering lines above are deliberately unresolved. The standard requires the
real project UUID and the prefix its server actually allocates, and inventing either
would put a false identifier into an ISO record. Until Adam confirms them, a work item
for this repository sits under Quasar HQ with an `HQ-####` key.

## What this repository is

The firmware the Safiery Connect app downloads and installs onto hardware in the field.
One folder per product line. **It is public**, because the app fetches from it with no
credentials and a mobile app cannot hold one: anything inside an APK can be extracted by
whoever downloads it.

It holds **built binaries and customer-facing notes only**. The source lives in its own
private repository.

## The flow

1. **Work on a branch, land through a pull request.** `<person>/<key>-short-slug` where a
   work item exists, `<person>/short-slug` where it does not; agent branches as
   `claude/...` or `codex/...`. Nobody pushes to `main` directly.
2. **Every published binary gets a changelog line.** `CHANGELOG.md` at the root, newest
   block on top. Publishing firmware is a controlled change: the file, its notes and this
   changelog are the ISO 9001 record (8.5.6 / 7.5).
3. **Verify before publishing, do not trust the upload.** For an ESP32 product, confirm
   the image begins with `0xE9` and contains the version string its release claims, and
   record the SHA-256 in the release notes. A binary that cannot be verified is not
   published. These files are flashed onto customer hardware and several products have no
   rollback, so a wrong file is not a bug report, it is a dead unit.
4. **Customer notes only.** Release notes carry the customer changelog and compatibility.
   Engineering notes stay in the private source repository.

## Never

- **No secrets, ever.** This repository is public. Treat everything committed here as
  published, because it is. No keys, tokens, customer data, or internal discussion.
- No engineering notes, commit hashes, private branch names or named internal discussion
  in release notes.
- No firmware for a product line published into another line's folder.
- No special or customer-specific build published here. The app refuses to update units
  running one, and publishing a standard build they could match would defeat that.
- No em or en dashes in documents. Plain hyphens.

## Read before the task

| Before you... | Read |
|---|---|
| publish any firmware | this file, then the product folder's `README.md` |
| publish Scotty firmware | [`scotty/README.md`](scotty/README.md) - the lines are not interchangeable |
| change how the app finds firmware | `scottyOTA.md` and `startankOTA.md` in `Safiery/Safiery-Connect` |
