# Scotty AI firmware

Builds for Scotty AI units, which update over Wi-Fi: the app joins the Scotty's own access point and
POSTs the binary to `http://172.24.24.1/update`.

## Lines are not interchangeable

A Scotty must only ever be given firmware from **its own line**. There is no rollback on the device
— the update handler commits and reboots — so a cross-line flash bricks the unit until it is
physically reflashed.

| Line | Source branch | Device reports |
|---|---|---|
| V2 | `main_v2.x.x.x` | `V2.6.3.2` |
| V3 | `main` | `V3.2.1.7` |
| V4 | `main_16MPartition` | `4.0.0.6` |
| IdleX | `ScottyIdelX` | `4.0.1.2-IdelX` |

IdleX is a line of its own, not a special build: it updates only from `-IdelX` to `-IdelX`.

## Special builds do not belong here

Units exist in the field running builds made for one product — `V4.0.0.7 400DCDC`,
`4.0.0.6-BatteryNMEA`, and the fire-truck build, which reports a structurally ordinary `4.0.0.5`.
The app refuses to update any of them and refers the customer to support. Publishing a standard
build that one of those units could match would defeat that protection.

## File naming

Keep the version readable in the filename, as the existing builds do:

```
scotty_repos.v4.0.0.6.bin
scotty_repos.v3.2.1.7.bin
scotty_repos.idleX.v4.0.1.2.bin
59_Scotty_V2.6.3.2.ino.bin
```

The version string the app compares against is the one **inside** the binary, not the filename — the
filename is for humans. Every Scotty `.bin` is an ESP32 image and begins with the byte `0xE9`.
