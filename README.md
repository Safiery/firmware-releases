# Safiery firmware releases

| Field | Value |
|---|---|
| Status | Active |
| Version | v0.2 |
| Owner | Adam |
| Last updated | 2026-10-20 |
| ISO-affected | yes (firmware change control: ISO 9001 8.5.6) |

Firmware binaries that the **Safiery Connect** app downloads and installs onto hardware in the
field, one folder per product line.

This repository is deliberately **public**. The app fetches from it with no credentials, because a
mobile app cannot hold one: anything shipped inside an APK can be extracted by anyone who downloads
it, and a token with access to Safiery's private source would be a poor thing to hand out. Keeping
only built binaries here means the source stays private while the app still works on a customer's
phone with nothing configured.

**Do not put source, keys, or customer data in this repository.** Treat everything committed here
as published, because it is.

## Layout

| Folder | Product |
|---|---|
| [`scotty/`](scotty) | Scotty AI |
| [`startank/`](startank) | STAR-Tank |
| [`starpower/`](starpower) | StarPower |
| [`starlight/`](starlight) | StarLight |
| [`starrover/`](starrover) | StarRover |
| [`starcustom/`](starcustom) | StarCustom |

Folder names are lower case because they appear in the URLs the app fetches, and
`raw.githubusercontent.com` is case-sensitive - `Startank` and `startank` are different paths, and
the difference is invisible until a download 404s on a customer's phone.

## Why folders rather than branches

Branches suit source that diverges and later merges. These are built artefacts that never merge, and
the app reads them over plain HTTPS, so what matters is a stable path:

```
https://raw.githubusercontent.com/Safiery/firmware-releases/main/scotty/<file>
```

A branch per product would mean the app knowing branch names, and a single manifest could not point
across them. One branch with folders keeps every product reachable from one place.

Note the firmware **source** repositories do use a branch per product line - `Safiery/scotty_repos`
splits Scotty V2, V3, V4 and IdleX that way. That is the right choice there and the wrong one here,
for the reason above.

## Adding a release

1. Put the binary in its product's folder.
2. Name it so the version is readable from the filename.
3. Update that folder's manifest so the app can find it.

Each product's folder has its own README with the conventions for that line.
