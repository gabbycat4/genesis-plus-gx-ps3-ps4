# Genesis Plus GX with PS3/PS4 controller support

An **unofficial** build of [Genesis Plus GX](https://github.com/ekeeke/Genesis-Plus-GX) 1.7.5 for the Wii that adds one thing: **wired PlayStation 3 and PlayStation 4 controllers** on the Wii's USB ports, for 2 players (one in each port). Everything else is the original Genesis Plus GX.

**All the credit for Genesis Plus GX goes to its creators.** Genesis Plus GX is made by Eke-Eke, based on Genesis Plus by Charles MacDonald, with portions from Nicola Salmoria and the MAME team and many other contributors (see the [Credits](https://github.com/ekeeke/Genesis-Plus-GX/blob/master/wiki/Credits.md) page). This build only adds the controller support. For the official Genesis Plus GX, go to [github.com/ekeeke/Genesis-Plus-GX](https://github.com/ekeeke/Genesis-Plus-GX).

> Please don't report problems with this build to the Genesis Plus GX developers. Open an issue here instead.

## Download and install

1. Go to **[Releases](../../releases)** and download **`GenesisPlusGX-PS3-PS4-Wii-SD-card.zip`**.
2. Unzip it and copy the `apps` folder onto your Wii's SD card. If you already have Genesis Plus GX in `apps/genplus`, it replaces the program and keeps your settings and saves. You may want to copy your old `boot.dol` somewhere first, as a backup.
3. Start Genesis Plus GX from the Homebrew Channel. The menu title shows **Genesis Plus GX 1.7.5 PS3/PS4 v4**.

## Controllers

Plug the controllers into the USB ports on the back of the Wii with their USB cables. You can plug them in or unplug them at any time, in the menu or during a game.

| Controller | Model |
| --- | --- |
| PS3 DualShock 3 / Sixaxis | |
| PS4 DualShock 4, original | CUH-ZCT1 |
| PS4 DualShock 4, newer (light bar on the touchpad) | CUH-ZCT2 |

Official Sony controllers only. Clones may not be detected.

- **2 players, any mix** of PS3 and PS4 controllers: the first one found is player 1, the next player 2. Each one plays alongside whatever controller is set up for that player in the emulator.
- PS3 controllers show their **player number light**. PS4 controllers show a **light bar colour**: player 1 red, player 2 blue.
- The code handles up to 4 controllers, so more may work through a USB hub, but that hasn't been tested.

| PS3 / PS4 | Genesis 3-button | Genesis 6-button | Master System / Game Gear |
| --- | --- | --- | --- |
| Square | A | A | |
| Cross (X) | B | B | 1 |
| Circle | C | C | 2 |
| L1 | | X | |
| Triangle | | Y | |
| R1 | | Z | |
| Start (PS3) / Options (PS4) | Start | Start | Start / Pause |
| Select (PS3) / Share (PS4) | | Mode | |
| D-pad or left stick | D-pad | D-pad | D-pad |
| R2 | Fast-forward on/off | Fast-forward on/off | Fast-forward on/off |
| PS button | Opens the menu | Opens the menu | Opens the menu |

In the emulator's menus: D-pad or left stick to move, Cross to select, Circle to go back, PS to leave the menu.

## What's changed from Genesis Plus GX 1.7.5

- Wired PS3 and PS4 controller support (new file `gx/utils/ds3.c`, plus small changes in `gx/gx_input.c` and `gx/main.c`).
- The menu title shows the build version.
- Small fixes so it builds with the newest devkitPPC/libogc: `gx/osd.h` (the `DEC`, `TBL` and `TBU` names), `gx/gui/menu.c` ("Exit to loader" uses `exit()` when `ogc/lwp_threads.h` doesn't exist) and `gx/utils/vi_encoder.c` (its own short delay instead of `udelay()`).

## Source code

The full source code of each version is attached to its release (`genesis-plus-gx-1.7.5-ps3-ps4-v4.zip`), as the license requires, along with `gpgx-ps3-ps4.patch`: all the changes as one patch against the official source. The PS3 controller protocol is based on xerpi's SickSaxis library.

To build it yourself with Docker or Podman, from the unzipped `Genesis-Plus-GX` folder:

```
podman run --rm -it -v "$PWD":/src -w /src docker.io/devkitpro/devkitppc:latest make -f Makefile.wii -j4
```

The result is `genplus_wii.dol`.

## Also see

- [Snes9x RX PS3/PS4](https://github.com/gabbycat4/snes9xrx-ps3-ps4): the SNES emulator with the same controllers.
- [VBAGX PS3/PS4](https://github.com/gabbycat4/vbagx-ps3-ps4): the Game Boy / GBA emulator with the same controllers.
- [Wii Menu PS3/PS4 Controller](https://github.com/gabbycat4/wii-menu-ps3-ps4-controller): a Priiloader hack that lets the same controllers work as the pointer on the Wii Menu (4.3U).

## License

Genesis Plus GX has its own non-commercial license, and this build is under the same one: see [`LICENSE.txt`](LICENSE.txt). In short, it may be shared and changed but never sold or used commercially, the full source code must come with any build, and the copyright notice must be kept.
