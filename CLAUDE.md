# Safiery firmware releases - Claude Code entry point

| Field | Value |
|---|---|
| Status | Active |
| Version | v0.1 |
| Owner | Adam |
| Last updated | 2026-10-20 |
| ISO-affected | yes (shared contributor instructions) |

@AGENTS.md

`AGENTS.md` is the shared rulebook for this repository. Edit shared rules there; this
file adds only Claude-specific setup.

This repository is **public** and holds firmware that gets flashed onto customer
hardware. Two consequences for an agent working here:

- Everything written here is published the moment it is pushed. There is no private
  area and no way to unpublish what has been fetched.
- Verify a binary before publishing it rather than trusting where it came from: the
  image magic, the version string inside the image, and the SHA-256 recorded in the
  notes. Several products have no rollback, so an unverified file risks a dead unit
  rather than a failed download.
