# agents deck — web flasher

Flash [agents deck](https://github.com/brushknight/agents-deck) firmware to a supported board from a
browser, over USB. No tools to install.

**Open the flasher:** https://k19gmc.github.io/agents-deck-flasher/

## Boards

| Board | Chip | Flash | Connection | Firmware |
|---|---|---|---|---|
| M5Stack StickS3 | ESP32-S3 | 8 MB | USB only | 0.1.0 |

## Where the firmware comes from

`firmware/agents-deck-m5stick-s3-0.1.0.bin` is the merged image (bootloader + partition table +
`boot_app0` + app) built from the **M5Stack StickS3 port** of agents deck, written at `0x0`. The
`.manifest.json` next to it is an [ESP Web Tools](https://esphome.github.io/esp-web-tools/) manifest;
`firmware-manifest.json` is the list the page reads to draw the board cards.

To add a board, drop its merged `.bin` and manifest into `firmware/` and add an entry to
`firmware-manifest.json` (`name`, `chipFamily`, `manifest`, `board`, `version`, `file`, `size`,
`sha256`, `flash_size`, `wifi`, `picture`). No build step; the page is plain static HTML.

## How to flash

1. Chrome or Edge, on desktop, on the computer the board is plugged into.
2. Plug the board in with a USB-C **data** cable.
3. Click **Install agents deck** and pick the board's USB port.
4. Wait about a minute for it to write and verify.

## What's here

```
index.html                     the flasher page (static)
firmware-manifest.json         the board list the page reads
firmware/
  agents-deck-m5stick-s3-0.1.0.bin           merged image, flashed at 0x0
  agents-deck-m5stick-s3-0.1.0.manifest.json ESP Web Tools manifest
img/                           board picture
```

Served straight from the repository root by GitHub Pages. `.nojekyll` keeps Jekyll out of the way.

## Licensing

The firmware is from agents deck, under its own licence. This flasher page and the manifests are
provided as-is.
