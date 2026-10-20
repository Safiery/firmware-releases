# Scotty AI firmware

Builds for Scotty AI units, which update over Wi-Fi: the app joins the Scotty's own access point and
POSTs the binary to `http://172.24.24.1/update`.

## Current releases — 3Q 2026

| Line | Version | File | Notes |
|---|---|---|---|
| V2 | 2.6.3.2 | [`59_Scotty_V2.6.3.2.ino.bin`](59_Scotty_V2.6.3.2.ino.bin) | [notes](release-notes/ScottyAI_V2_3Q_2026.md) |
| V3 | 3.2.1.7 | [`scotty_repos.v3.2.1.7.bin`](scotty_repos.v3.2.1.7.bin) | [notes](release-notes/ScottyAI_V3_3Q_2026.md) |
| V4 | 4.0.0.6 | [`scotty_repos.v4.0.0.6.bin`](scotty_repos.v4.0.0.6.bin) | [notes](release-notes/ScottyAI_V4_3Q_2026.md) |
| IdleX | 4.0.1.2-IdelX | [`scotty_repos.v4.0.1.2-IdelX.bin`](scotty_repos.v4.0.1.2-IdelX.bin) | [notes](release-notes/ScottyAI_IdleX_3Q_2026.md) |

Each file's SHA-256 is recorded in its release notes.

## Lines are not interchangeable

A Scotty must only ever be given firmware from **its own line**. There is no rollback on the device
— the update handler commits and reboots — so a wrong flash bricks the unit until it is physically
reflashed. Each release's Compatibility section says which hardware it applies to; read it before
installing anything.

IdleX is a line of its own, not a special build: it updates only from `-IdelX` to `-IdelX`. Its
version is written here exactly as the device reports it, suffix included, so that what the app
compares against and what the unit says are the same string.

## Special builds do not belong here

Units exist in the field running builds made for one product — `V4.0.0.7 400DCDC`,
`4.0.0.6-BatteryNMEA`, and a fire-truck build that reports a structurally ordinary `4.0.0.5`. The
app refuses to update any of them and refers the customer to Safiery support. Publishing a standard
build that one of those units could match would defeat that protection.

## File naming

Keep the version readable in the filename, as the files above do. The version the app compares
against is the one **inside** the binary, not the filename — the filename is for humans. Every
Scotty `.bin` is an ESP32 image and begins with the byte `0xE9`.

## What is not here

Release notes in this folder carry the **customer changelog** and **compatibility** only.
Engineering notes — build configuration, commits, branches, internal discussion — stay in the
private source repository, because this repository is public.
