# N64 USB Launcher for webOS

[Português](README.pt-BR.md) · English

A small launcher app for LG webOS TVs. It scans a USB drive for Nintendo 64 ROMs (`.z64`, `.n64`, `.v64`), lets you pick one with the TV remote, and starts [RetroArch](https://www.retroarch.com/) with that ROM already loaded.

> **Status: experimental.** The package has been checked, but the app has not been validated on every TV model or webOS version. Expect rough edges and please report what you find.

## Legal notice: no ROMs

**This project does not include, host, distribute, or link to ROMs, BIOS files, games, or any other copyrighted material.**

- Use only ROMs you obtained legally, for example dumped from cartridges you own.
- Do not ask for ROMs in issues or discussions, and do not post links to them. Such requests will be ignored or removed.
- Copyright law differs between countries. You are responsible for knowing and following the law where you live.

## What it does

1. Looks for `.z64`, `.n64` and `.v64` files on the USB drive (`/tmp/usb`) and in `/media/internal`.
2. Shows the results in a list you can browse with the remote. The last ROM you played is preselected.
3. Runs RetroArch with an N64 core and the selected ROM.

This app is **not an emulator**. It is only a shortcut. The emulation is done by RetroArch and a libretro N64 core such as Mupen64Plus-Next.

## Requirements

| Requirement | Notes |
|---|---|
| LG TV with webOS | Rooted, with the [Homebrew Channel](https://www.webosbrew.org/) installed |
| RetroArch for webOS | App id `com.retroarch.webos`, available from the Homebrew Channel |
| An N64 libretro core | Built for ARM/webOS, for example `mupen64plus_next_libretro.so`. **Not included** |
| A USB drive with your ROMs | FAT32 or exFAT is the safest choice |

Root is required because the launcher runs a shell command through the Homebrew Channel service. Without root, only the "open RetroArch" button works.

## Installation

1. On the TV, open the Homebrew Channel.
2. Go to **Settings → Add repository**.
3. Enter:

   ```
   https://ruubr337.github.io/n64-webos-repo/api/apps.json
   ```

4. Find **N64 USB Launcher** in the app list and install it.

You can also download the `.ipk` from the `ipks/` folder and install it with the [webOS Dev Manager](https://github.com/webosbrew/dev-manager-desktop) or `ares-install`.

## Usage

Plug in the USB drive, open **N64 USB Launcher**, pick a ROM, and press OK.

| Remote key | Action |
|---|---|
| Up / Down | Choose a ROM |
| OK | Play |
| Red | Rescan for ROMs |
| Green | Open RetroArch without a ROM |
| Back | Exit |

## Configuration

If the launcher cannot find your core on its own, set its path in `n64launcher.conf` inside the app folder:

```sh
CORE_PATH="/path/to/mupen64plus_next_libretro.so"
```

## Troubleshooting

| Problem | What to try |
|---|---|
| "N64 core not found" message | Copy a core to the TV and set `CORE_PATH` (see above) |
| No ROMs listed | Check the drive format, and that files end in `.z64`, `.n64` or `.v64`. Press Red to rescan |
| Can't run commands on the TV | The TV is not rooted or the Homebrew Channel is missing. Use the Green key as a fallback |
| Black screen after launching | Check the log at `/tmp/n64-usb-launcher.log` over SSH and send me its contents |

## Feedback

Test reports are welcome, especially the TV model and webOS version where it worked or failed. Open an issue and include those details. Please do not include ROMs, BIOS files, or links to them.

The app runs commands as root through the Homebrew Channel, so only install it from this repository or sources you trust.

## Repository layout

```
api/apps.json    Repository index read by the Homebrew Channel
ipks/            Packaged .ipk files
icon.png         App icon
```

## Trademarks and affiliation

This is an independent project. It is **not affiliated with, sponsored by, or endorsed by** Nintendo, LG Electronics, libretro/RetroArch, or the webOS Homebrew Project. All names and trademarks belong to their respective owners and are used only to describe compatibility.

## Risks of rooting

Rooting a TV may void its warranty, and firmware updates can remove root access. This project does not provide support for the rooting process.

## License

Copyright (c) 2026 ruubr337. All rights reserved.

You may install and use this app for personal, non-commercial purposes. You may not redistribute, modify, or sell it without written permission. The software is provided "as is", without warranty of any kind.

This is not open-source software. RetroArch and the emulator cores are separate projects with their own licenses and are not part of this repository.
