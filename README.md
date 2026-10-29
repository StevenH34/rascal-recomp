# Rascal

<!-- retcomm-readme-metrics -->
[![GitHub downloads (all assets, all releases)](https://img.shields.io/github/downloads/StevenH34/rascal-recomp/total)](https://github.com/StevenH34/rascal-recomp/releases)
[![GitHub downloads (latest release)](https://img.shields.io/github/downloads/StevenH34/rascal-recomp/latest/total)](https://github.com/StevenH34/rascal-recomp/releases/latest)
[![GitHub release](https://img.shields.io/github/v/release/StevenH34/rascal-recomp)](https://github.com/StevenH34/rascal-recomp/releases/latest)
<!-- /retcomm-readme-metrics -->

Static recompilation of **Rascal** built on
[psxrecomp](https://github.com/mstan/psxrecomp) and
[recomp-ui](https://github.com/RetroPortingToolKit/recomp-ui).

Traveller's Tales' 1998 3D platformer, running natively on PC with no
emulator. Rascal jumps through time with his bubble gun to rescue his father,
the Professor, from the villainous Chronon.

| | |
|---|---|
| Players | 1 |
| Region | USA |
| Developer |	Traveller's Tales|
| Publisher | Psygnosis |
| Year | 1998 |

Scaffolded with the New Project Layout. See
`psxrecomp/docs/GAME_PROJECT_SETUP.md` for the full flow.

## Status

No current release yet, but the game does run.

| Area | Status |
|---|---|
| BIOS boot | Yes |
| Intro FMV | Yes |
| Title / menus | Yes |
| Gameplay | Yes |
| Audio / music | Yes |
| Memory card saves | TBD |
| Save states | TBD |
| Controllers | TBD |
| Full playthrough | TBD |

## Modern enhancements

_None yet._

## Disc requirements

You need your own dump of the **USA** release, serial **SLUS-00542**, as a
`.cue` with all of its tracks:

- `Rascal (USA).cue`
- `Rascal (USA) (Track 01).bin` (data) through `Track 10` (audio). All 10
  tracks are required.

Data track (Track 01) checksums:

| | |
|---|---|
| Size | 133,471,296 bytes |
| SHA-1 | `f3987e30ec1530ad88952719cd0d24daa8a262af` |
| MD5 | `a26b29b0951b606479c26a970602c299` |
| CRC32 | `f4696a11` |

Other regions and modified or re-encoded images are not supported.

## Playing

1. Download the release zip for your platform from
   [Releases](https://github.com/StevenH34/rascal-recomp/releases)
   and extract it anywhere.
2. Run the executable. The launcher opens.
3. Point it at your `Rascal (USA).cue` (see [Disc requirements](#disc-requirements)).
   Releases boot on the bundled OpenBIOS, so a retail BIOS is optional.
4. Adjust video, controls, and mods in the launcher if needed, then launch.

Or install and update it through [Retro Launcher](#retro-launcher).

## Controls

Default bindings. Rebind keyboard and gamepad in the launcher's Controls page.

| PlayStation | Keyboard | Gamepad (Xbox layout) |
|---|---|---|
| D-pad | Arrow keys | D-pad |
| Left stick | Arrow keys | Left stick |
| Cross | X | A |
| Circle | S | B |
| Square | Z | X |
| Triangle | A | Y |
| L1 / R1 | Q / W | LB / RB |
| L2 / R2 | E / R | LT / RT |
| L3 / R3 | T / Y | Left / right stick click |
| Start | Enter | Start |
| Select | Right Shift | Back |

Keyboard bindings are saved to `keybinds.ini`, and gamepad mappings to
`input.ini`, next to the executable.

## Configuration

`game.toml` holds the shipped defaults, including the OpenGL renderer, 4:3
aspect ratio, and digital controller mode. Anything you change in the launcher
is saved to `settings.toml` next to the executable and takes priority over
`game.toml`. Delete `settings.toml` to go back to the defaults.

## Saves

Memory cards are stored in the `saves/` folder next to the executable, as
`card1.mcd` and `card2.mcd`. They are standard 128 KB raw PS1 memory card
images, so they also work in emulators that use raw `.mcd` cards.

<!-- retcomm-readme-launcher -->
## Retro Launcher

You can run this title **standalone** (download the release zip, point it at
your disc, play), or manage installs, updates, and disc/BIOS wiring with
**[Retro Launcher](https://github.com/RetroPortingToolKit/Retro-Launcher)** —
the Retro Compilation Manager hub for self-compiling recomps.

[Downloads](https://github.com/RetroPortingToolKit/Retro-Launcher/releases) ·
[Full README & features](https://github.com/RetroPortingToolKit/Retro-Launcher#readme)

<p align="center">
  <img src="https://raw.githubusercontent.com/RetroPortingToolKit/Retro-Launcher/main/docs/screenshots/hub-and-game-launcher.png" alt="Retro hub with a background build, next to a title’s recomp-ui launcher" width="720">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/RetroPortingToolKit/Retro-Launcher/main/docs/screenshots/queue-and-background-build.png" alt="Background cmake build with titles queued" width="720">
</p>

Retro checks for updates, installs the prebuilt release zips, and automates
BIOS/ROM/save plumbing so you are not stuck repeating each game’s first run by hand.
<!-- /retcomm-readme-launcher -->

## Legal

You must own the original game. Disc images under `disc/` are gitignored and
must never be committed. Retail BIOS dumps are not redistributed and no C
derived from one may be committed; releases run on the bundled MIT OpenBIOS.

`generated/` (the recompiled game C) is **not committed**, because it is
derived from the copyrighted game executable. Generate it locally from your own
dump (see Quick start) and regenerate whenever seeds or the framework pin change.

Default app icon: `assets/psxrecomp.ico` (and `.png` / `.svg`) — Retro-themed controller mark from `psxrecomp/assets/`. Windows builds embed it via `APP_ICON`.

Optional box art under `launcher_assets/img/` may come from
[libretro-thumbnails](https://github.com/libretro-thumbnails/libretro-thumbnails)
(`Named_Boxarts`); see `BOXART_SOURCE.txt` when present.

## License

The original code in this repository is licensed under the
[PolyForm Noncommercial License 1.0.0](LICENSE). You may use, modify and share
it for personal, hobby, research or other noncommercial purposes. **Commercial
use is not permitted.**

This license covers only the code written for this project. It does not cover:

- the submodules, which carry their own licenses
  ([psxrecomp](psxrecomp/LICENSE): PolyForm Noncommercial 1.0.0;
  [recomp-ui](recomp-ui/LICENSE): MIT);
- the bundled OpenBIOS (MIT, see `psxrecomp/bios/OpenBIOS.LICENSE`);
- Rascal itself, its assets, or anything generated from the game executable,
  which remain the property of their respective copyright holders.

## Quick start (dev)

```bash
git submodule update --init --recursive
./psxrecomp/tools/ci/build_emitters.sh
python3 psxrecomp/psxrecomp_cli.py generate \
  --config game.toml --project-root . --disc disc/<your>.cue
cmake -S . -B build-release -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build-release --target psx-runtime
```

Releases: because `generated/` is not committed, release builds are made
locally from your own disc. Generate and build as above, then package the
compiled game with `scripts/package_release.sh build-release <platform>`
(for example `linux-x64`), which writes `dist/rascal-<version>-<platform>.zip`.
The zip contains only the compiled game, never the generated C.

## Symbols

Progressive map: `symbols.toml` → `python3 tools/sync_symbols.py` →
`psx_symbols.h` (`PSX_FN_*`). See `psxrecomp/docs/SYMBOLS.md`.

## Framework pins

Submodule gitlinks (`psxrecomp`, optional `recomp-ui`, nested `recomp-net`)
are authoritative. `framework_pins.txt` is an optional scaffold snapshot;
release CI logs SHAs with `record_pins.sh` but builds whatever the gitlinks
resolve to. Bump submodules deliberately — do not float on `main`/`master`
in release CI.

## Credits

- [psxrecomp](https://github.com/mstan/psxrecomp) by mstan, the static
  recompilation framework this project is built on.
- [recomp-ui](https://github.com/RetroPortingToolKit/recomp-ui), the launcher
  and in-game UI.
- [OpenBIOS](psxrecomp/bios/OpenBIOS.LICENSE) (MIT), the bundled BIOS.
- _Add testers and contributors here._

Rascal is © 1998 Psygnosis / Traveller's Tales. This is an unofficial fan
project and is not affiliated with or endorsed by the rights holders.

<!-- retcomm-readme-raid -->
---

<p align="center">
  <sub><b>R.A.I.D. — Retro AI Development</b> · a Discord for AI-assisted retro reverse-engineering, decomp &amp; recomp</sub>
</p>

<p align="center">
  <a href="https://discord.gg/Ad9BwSzctP"><img src=".github/raid-discord.png" alt="Join the Retro AI Development (R.A.I.D.) Discord" width="200"></a>
</p>
<!-- /retcomm-readme-raid -->
