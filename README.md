# GTA III (re3) - Raspberry Pi 5 Port Documentation

Welcome to the GTA III (re3) port for the Raspberry Pi 5. This project uses the reverse-engineered `re3` engine, optimized specifically for the Cortex-A76 cores and the latest Raspian Bookworm OS.

## 1. How it was achieved
This port involves several key optimizations and compatibility fixes for the Raspberry Pi 5 platform:

- **Cortex-A76 Optimization**: Compiled with `-mcpu=cortex-a76 -O3` to leverage the Pi 5's powerful ARMv8.2-A cores.
- **16KB Page Support**: The binary is aligned to **64KB (0x10000)** boundaries during linking. This makes it fully compatible with the 16KB page size kernel used in modern Raspberry Pi OS releases, preventing "Invalid Instruction" or memory mapping crashes.
- **OpenGL ES / LIBRW**: Uses `librw` with the OpenGL 3.0+ backend for high-performance rendering on the VideoCore VII GPU.
- **OpenAL Audio**: Integrated with OpenAL Soft for low-latency, high-fidelity positional audio.

## 2. Prerequisites
**IMPORTANT**: Due to legal reasons, this package does NOT include the game assets (models, textures, sounds). You must own a legal copy of GTA III on PC.

1. Locate your GTA III PC installation folder.
2. Copy all files from that folder (including `models`, `data`, `audio`, etc.) to the following location on your Pi:
   `~/.re3/` or the installation directory `/usr/share/re3-pi5/`.
   *Alternatively, create a folder named `gamefiles` in your home directory and place the game there.*

## 3. Installation
If you have the `.deb` package, install it via terminal:
```bash
sudo apt install ./re3-pi5.deb
```
This will:
- Install the `re3` binary to `/usr/bin/re3-pi5`.
- Add a shortcut to your **Games** menu in the Pi Start Menu.
- Register all necessary dependencies.

## 4. Usage
- **Launch**: Open the Start Menu -> Games -> **GTA III**.
- **Configuration**: Settings are stored in `re3.ini`. You can also open the Debug Menu in-game using `Ctrl + M`.
- **Controllers**: Xbox and PlayStation controllers are supported via SDL2.

## 5. Removal
To completely remove the game and its menu entry:
```bash
sudo apt remove re3-pi5
```
*Note: This will not delete your save files or the game assets you copied manually.*

---
*Created with <3 for the Raspberry Pi Community.*
