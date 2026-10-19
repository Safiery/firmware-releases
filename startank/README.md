# STAR-Tank firmware

Builds for STAR-Tank level sensors, which update over Bluetooth LE using MCUmgr/SMP against
MCUboot — a different mechanism entirely from Scotty's Wi-Fi upload.

STAR-Tank firmware is **variant-specific**: a sensor runs either the fuel or the water build, and
nothing in the advertisement says which. Converting between them is legitimate and the app supports
it, but it is a deliberate act and the app confirms it first.

The app currently reads its STAR-Tank manifest from a separate host. Moving it here is a change to
`FIRMWARE_MANIFEST_URL` in the app build, not a code change — see `startankOTA.md` in
`Safiery/Safiery-Connect`.
