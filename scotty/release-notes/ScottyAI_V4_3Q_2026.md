# Scotty AI V4 - 3Q 2026 (4.0.0.6)

File: `scotty_repos.v4.0.0.6.bin`  
SHA-256: `cb9abb88bf2ab34ef434ed94dbf59bd80b8f96549878b43fb566d0a98735dbf8`

## Customer changelog

- Scotty now appears on the Victron Cerbo GX.
- Two or more Scotty units on the same CAN bus can now be told apart - each shows its own name (Scotty_XX:XX).
- Scotty ID is now shown on the Tune, Advanced and Update pages.
- Smart alternator support: with Feature In switched on, Scotty keeps charging from the low side to the high side so a smart alternator does not go to sleep, and no longer discharges from the high side back to the low side.
- Firmware updates over Wi-Fi now correctly report when an update has failed.
- Various reliability improvements.

## Compatibility

- Applies to Scotty AI V4 and Scotty AI Solid-State only.
- Do not install on Scotty AI V2 or V3 - different hardware; the wrong firmware can permanently damage the unit.
- After updating, check your settings on the Tune and Advanced pages are still correct before using the unit.
- If you are unsure which Scotty you have, contact Safiery Support before updating.

---

Engineering notes for this release are kept in the private source repository and are
deliberately not reproduced here.
