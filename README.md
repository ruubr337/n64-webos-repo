# N64 USB Launcher for webOS

[Português](README.pt-BR.md) · English

A small launcher app for LG webOS TVs. It finds Nintendo 64 (`.z64`, `.n64`, `.v64`) and Game Boy Advance (`.gba`) ROMs on a USB drive or in the TV's storage, lets you pick one with the TV remote, and starts [RetroArch](https://www.retroarch.com/) with that ROM already loaded. If you have no USB drive, it can also download your own ROM from a link (Dropbox, Google Drive or a direct HTTPS link).

> **Status: experimental.** The package has been checked, but the app has not been validated on every TV model or webOS version. Expect rough edges and please report what you find.

## Legal notice: no ROMs

**This project does not include, host, distribute, or link to ROMs, BIOS files, games, or any other copyrighted material.**

- Use only ROMs you obtained legally, for example dumped from cartridges you own.
- Do not ask for ROMs in issues or discussions, and do not post links to them. Such requests will be ignored or removed.
- Copyright law differs between countries. You are responsible for knowing and following the law where you live.

## What it does

1. Looks for `.z64`, `.n64`, `.v64` and `.gba` files on the USB drive (`/tmp/usb`), in `/media/internal` and in `/media/developer/roms` (where downloads are saved).
2. Shows the results in a list you can browse with the remote. The last ROM you played is preselected.
3. Runs RetroArch with the right core for the system (N64 or GBA) and the selected ROM.

This app is **not an emulator**. It is only a shortcut. The emulation is done by RetroArch and libretro cores such as Mupen64Plus-Next (N64) and mGBA (GBA).

## Requirements

| Requirement | Notes |
|---|---|
| LG TV with webOS | Rooted, with the [Homebrew Channel](https://www.webosbrew.org/) installed |
| RetroArch for webOS | App id `com.retroarch.webos`, available from the Homebrew Channel |
| Libretro cores | Built for ARM/webOS: `mupen64plus_next_libretro.so` for N64 and `mgba_libretro.so` for GBA. Install them from RetroArch (Load Core → Download a Core). **Not included** |
| Your ROMs | On a USB drive (FAT32 or exFAT is the safest choice), or download them from a link (see below) |

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
| Yellow | Toggle auto-start: next time the app opens the last ROM after 3 seconds (any key cancels) |
| Blue | Download a ROM from a link |
| Back | Exit |

### Download a ROM from a link

No USB drive? Press **Blue**, type a public link to **your own** ROM file, and press OK.

- **Dropbox:** share the file ("Anyone with the link") and use that link. The app switches it to a direct download automatically.
- **Google Drive:** set the file to "Anyone with the link" and use the share link.
- **Zip files:** a `.zip` is unpacked, and the ROM inside is kept (requires `unzip` on the TV).
- **Typing on a TV is slow.** Shorten the link first with a link shortener such as tinyurl and type the short link instead. Short links are followed automatically.
- Files are saved to `/media/developer/roms` and show up in the list. The app checks the file contents to tell N64 and GBA ROMs apart, and rejects anything else (including web pages returned by a private link).

The link must start with `https://`. Only download files you have the right to use.

## Configuration

If the launcher cannot find a core on its own, set its path in `n64launcher.conf` inside the app folder:

```sh
CORE_PATH_N64="/path/to/mupen64plus_next_libretro.so"
CORE_PATH_GBA="/path/to/mgba_libretro.so"
```

## Troubleshooting

| Problem | What to try |
|---|---|
| "core not found" message | Install the core from RetroArch (Load Core → Download a Core), or set its path in `n64launcher.conf` (see above) |
| Download fails or says "web page" | The link is not public. Set sharing to "Anyone with the link" |
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
