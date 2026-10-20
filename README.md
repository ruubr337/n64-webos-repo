<p align="center">
  <img src="logo.png" alt="REPO launcher" width="180">
</p>

<h1 align="center">REPO launcher</h1>

<p align="center">
  A simple game launcher for LG webOS TVs.<br>
  Pick a Nintendo 64 or Game Boy Advance ROM with your remote and play it in RetroArch.
</p>

<p align="center">
  <a href="../../releases/latest"><b>Download the latest .ipk</b></a> · English · <a href="README.pt-BR.md">Português</a>
</p>

> **Status: experimental.** The package and its scripts have been tested in a simulated environment, but not on every TV model or webOS version. Expect rough edges, and please report what you find.

## Highlights

- **One screen, all your games.** ROMs appear as cards with a system badge (N64 or GBA), navigated with the remote's arrow keys.
- **Plays from a USB drive or from a link.** No USB drive? Press Blue, type a link to your own ROM, and the app downloads it for you. Dropbox, Google Drive and direct HTTPS links work, and `.zip` files are unpacked.
- **Picks the right core by itself.** N64 ROMs open with Mupen64Plus-Next, GBA ROMs with mGBA.
- **Auto-start.** Turn it on once and the app opens your last game after a 3-second countdown.
- **Remote-friendly.** Everything is mapped to the arrows, OK, Back and the four color keys.

## Legal notice: no ROMs

**This project does not include, host, distribute, or link to ROMs, BIOS files, games, or any other copyrighted material.**

- Use only ROMs you obtained legally, for example dumped from cartridges you own.
- Do not ask for ROMs in issues or discussions, and do not post links to them. Such requests will be ignored or removed.
- Copyright law differs between countries. You are responsible for knowing and following the law where you live.

## Requirements

| Requirement | Notes |
|---|---|
| LG TV with webOS | Rooted. The launcher needs root to find ROMs and to start RetroArch, and it uses the root command service that the webOS homebrew tools install when a TV is rooted |
| [RetroArch for webOS](https://repo.webosbrew.org/apps/com.retroarch.webos) | App id `com.retroarch.webos` |
| Libretro cores | `mupen64plus_next_libretro.so` (N64) and `mgba_libretro.so` (GBA). Install them from RetroArch: **Load Core → Download a Core**. Not included |
| Your ROMs | On a USB drive (FAT32 or exFAT is the safest choice), or downloaded from a link (see below) |

## Install

1. Go to the [Releases page](../../releases/latest) and download the `.ipk` file.
2. Install it on your TV with the [webOS Dev Manager](https://github.com/webosbrew/dev-manager-desktop) (drag the file in and press Install), or from a terminal:

   ```sh
   ares-install com.user.n64usblauncher_1.3.0_all.ipk -d <your-tv>
   ```

3. Open **REPO launcher** from the TV's app list.

## Use

Plug in a USB drive (or download a ROM, see below), open the app, pick a game, and press OK.

| Remote key | Action |
|---|---|
| Arrow keys | Move between games |
| OK | Play |
| Red | Rescan for ROMs |
| Green | Open RetroArch without a ROM |
| Yellow | Turn auto-start on or off |
| Blue | Download a ROM from a link |
| Back | Exit |

### Download a ROM from a link

Press **Blue**, type a public link to **your own** ROM file, and press OK. The progress is shown on screen, and the ROM appears in the list when it finishes.

- **Dropbox:** share the file ("Anyone with the link") and use that link. The app turns it into a direct download automatically.
- **Google Drive:** set the file to "Anyone with the link" and use the share link.
- **Zip files:** a `.zip` is unpacked and the ROM inside is kept (needs `unzip` on the TV).
- **Typing on a TV is slow.** Shorten the link first with a link shortener such as tinyurl, and type the short link instead. Short links are followed automatically.
- Downloads are saved to `/media/developer/roms`. The app checks the file contents to tell N64 and GBA ROMs apart and rejects anything else, including web pages returned by a private link.

The link must start with `https://`.

### Auto-start

Press **Yellow** once to turn it on. Next time you open the app, it starts the last game you played after 3 seconds. Press any key during the countdown to cancel and see the list.

## Configuration

If the launcher cannot find a core on its own, set its path in `n64launcher.conf` inside the app folder:

```sh
CORE_PATH_N64="/path/to/mupen64plus_next_libretro.so"
CORE_PATH_GBA="/path/to/mgba_libretro.so"
```

## Troubleshooting

| Problem | What to try |
|---|---|
| "core not found" message | Install the core from RetroArch (Load Core → Download a Core), or set its path in `n64launcher.conf` |
| No ROMs listed | Check the drive format and that files end in `.z64`, `.n64`, `.v64` or `.gba`. Press Red to rescan |
| "Can't run commands" message | The TV is not rooted, or the root command service is not running. Use the Green key to open RetroArch directly |
| Download fails or says "web page" | The link is not public. Set sharing to "Anyone with the link" |
| Black screen after launching | Read `/tmp/n64-usb-launcher.log` over SSH, and open an issue with its contents |

## Feedback

Test reports are very welcome, especially the TV model and webOS version where it worked or failed. Open an issue and include those details. Please do not include ROMs, BIOS files, or links to them.

REPO launcher runs commands as root on your TV, so only install it from this repository's Releases page.

## Risks of rooting

Rooting a TV may void its warranty, and firmware updates can remove root access. This project does not provide support for the rooting process.

## Credits

Emulation is done by [RetroArch](https://www.retroarch.com/) and the libretro cores Mupen64Plus-Next and mGBA, which are separate projects with their own licenses and are not part of this repository.

## Trademarks and affiliation

This is an independent project. It is **not affiliated with, sponsored by, or endorsed by** Nintendo, LG Electronics, libretro/RetroArch, or the webOS Homebrew Project. All names and trademarks belong to their respective owners and are used only to describe compatibility.

## License

Copyright (c) 2026 ruubr337. All rights reserved.

You may install and use this app for personal, non-commercial purposes. You may not redistribute, modify, or sell it without written permission. The software is provided "as is", without warranty of any kind.

This is not open-source software.
