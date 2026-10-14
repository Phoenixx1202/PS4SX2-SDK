# PS4SX2 SDK

Prebuilt development dependencies used to compile [PS4SX2](https://github.com/Phoenixx1202/PS4SX2), an experimental PlayStation 2 emulator for PlayStation 4.

This repository hosts SDK snapshots for the project's GitHub Actions workflow. It allows application builds to run on GitHub-hosted runners without requiring the maintainer's development PC.

## Included components

- Selected OpenOrbis tools, headers, libraries and import stubs.
- PS4-adapted Mesa/RADV static libraries.
- PS4 libc++ and libc++abi runtimes, headers and compatibility overlays.
- Prebuilt image and compression dependencies.
- Windows packaging tools and required packaging resources.
- Available license notices and a per-file SHA-256 manifest.

**BIOS files, games, saves and console keys are not included.**

## Download

Open [Releases](https://github.com/Phoenixx1202/PS4SX2-SDK/releases) and download:

- `ps4sx2-sdk-v1.tar.gz` — SDK archive.
- `ps4sx2-sdk-v1.tar.gz.sha256` — archive checksum.

These are build dependencies. To download the emulator itself, visit [PS4SX2 Releases](https://github.com/Phoenixx1202/PS4SX2/releases).

## GitHub Actions setup

In your PS4SX2 source repository, open:

**Settings → Secrets and variables → Actions → Variables**

Create the following repository variables:

| Variable | Value |
|---|---|
| `PS4_SDK_URL` | Direct HTTPS download URL of the SDK archive |
| `PS4_SDK_SHA256` | The 64-character SHA-256 checksum from the accompanying checksum file |

For the `sdk-v1` release, the download URL is:

```text
https://github.com/Phoenixx1202/PS4SX2-SDK/releases/download/sdk-v1/ps4sx2-sdk-v1.tar.gz
```

Then run **Actions → Build PS4SX2 → Run workflow** in the source repository.

The workflow verifies the archive checksum, compiles the emulator on Ubuntu and creates the installable PKG on Windows.

## Updating the SDK

The PS4SX2 source repository includes `tools/ci/export-sdk.py` to export a snapshot from a prepared development environment.

For each update:

1. Export a new archive.
2. Publish it under a new release tag.
3. Include its matching checksum file.
4. Update both Actions variables in the source repository.

Keep previous release assets unchanged so older builds can continue using their pinned SDK.

See the [PS4SX2 build instructions](https://github.com/Phoenixx1202/PS4SX2#building) for details.

## Status

This SDK supports an **experimental alpha project**. It contains prebuilt dependencies adapted for the current PS4SX2 build and is not a general-purpose PS4 SDK.

A successful build does not guarantee game compatibility, stability or full-speed emulation.

## Credits and licenses

Thanks to the contributors behind:

- [OpenOrbis](https://github.com/OpenOrbis/OpenOrbis-PS4-Toolchain)
- [Mesa](https://www.mesa3d.org/)
- [LLVM and libc++](https://github.com/llvm/llvm-project)
- [DolphinPS4](https://github.com/iHaiDeeZ/DolphinPS4)
- [LibOrbisPkg](https://github.com/maxton/LibOrbisPkg)
- The other bundled open-source dependencies.

Each component retains its respective license. Consult the notices included in the archive and the upstream projects for license terms and source availability. Redistribution must satisfy the applicable licenses, including source-distribution requirements where relevant.

This is a community project and is not affiliated with or endorsed by Sony Interactive Entertainment.
