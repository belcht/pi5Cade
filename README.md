# pi5Cade

A one-command build for a 3D-printed **Raspberry Pi 5 arcade cabinet**. Takes a freshly-flashed
Raspberry Pi OS box to a fully-configured RetroPie arcade — RetroPie install, system hardening,
audio setup, and the [RetroLED](https://github.com/belcht/RetroLED) marquee LED software — in one
script.

## Quick start

Flash Raspberry Pi OS (64-bit), boot, SSH in, then:

```bash
git clone https://github.com/belcht/pi5Cade.git
cd pi5Cade
sudo ./picadeinstall.sh --leds <N>      # N = number of LEDs in your marquee
```

- **[docs/QUICKSTART.md](docs/QUICKSTART.md)** — copy-paste version
- **[docs/MANUAL-INSTALL.md](docs/MANUAL-INSTALL.md)** — do every step by hand
- **[docs/BUILD.md](docs/BUILD.md)** — full walkthrough from a blank SD card
- **[docs/WHY.md](docs/WHY.md)** — the reasoning behind each hardening choice

## What it does

1. Updates the OS and installs **RetroPie** (Core + Main).
2. Applies **system hardening** — self-disabling WiFi watchdog, persistent journald,
   volatile-storage tmpfs, `brcmfmac` tuning.
3. Sets up **audio** — auto-selects a USB sound card if present, else HDMI; handles PipeWire for
   dual desktop/arcade boxes.
4. Installs **[RetroLED](https://github.com/belcht/RetroLED)** (cloned automatically) to drive the
   marquee LEDs with per-game reactions.
5. Flips the box to boot straight into **EmulationStation**.

Common flags: `--leds <N>`, `--auto` (non-interactive), `--update`, `--no-watchdog`,
`--keep-pipewire`. Run `sudo ./picadeinstall.sh --help` for the full list.

## Hardware

This is a **generic** Pi 5 arcade build — not tied to any specific panel, audio device, or network.
The `setup/` files are the proven reference configuration; adapt them to your hardware (e.g. the
USB-audio udev rule targets a reference dongle's VID:PID — change it for a different card). The
marquee uses a WS2812B strip; see RetroLED for LED wiring/specifics.

## Related

- **[RetroLED](https://github.com/belcht/RetroLED)** — the LED marquee controller this project installs.

## License

GPL-3.0 — see [LICENSE](LICENSE). Free to use, study, modify, and share; derivatives must remain
open-source under the GPL.
