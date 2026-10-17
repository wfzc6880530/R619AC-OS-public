# DualWeb on P&W R619AC 128M NAND (test branch)

This branch adds the DualWeb web UI/API to the existing R619AC OpenWrt build. It does not modify `main`.

## Target
- OpenWrt 25.12.5
- `ipq40xx/generic`
- `p2w_r619ac-128m`
- ARMv7 API binary built with `GOOS=linux GOARCH=arm GOARM=7 CGO_ENABLED=0`

## Changes
- The build workflow downloads DualWeb from `wfzc6880530/dualweb` branch `test/openbox-artifacts`.
- Builds `src/main.go` for ARMv7 and copies the DualWeb overlay into OpenWrt's `files/` root overlay.
- Enables nginx and required LuCI/RPC support.
- Preserves the R619AC-specific DTS, NAND layout and device profile from this repository.

## Build and validation
A push to this test branch starts the existing firmware workflow. The output must be reviewed for image-size limits and tested on real hardware before use. Build success alone does not prove Wi-Fi calibration, NAND write safety, or recovery behavior.

The DualWeb homepage initially uses password `root`; change it immediately after first login.

Open-Box proprietary runtime is not bundled.