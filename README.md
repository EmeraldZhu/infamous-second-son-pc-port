# inFAMOUS Second Son PC port: EmeraldZhu's playtest build

This is a fork of **[Castlesea's inFAMOUS Second Son PC port](https://github.com/Castlesea/infamous-second-son-pc-port)**, maintained by **[Emerald Zhu (EmeraldZhu)](https://github.com/EmeraldZhu)**, a contributor to the project.

It's the build I play and test: Castlesea's latest code, plus a few controller improvements that are proposed upstream but not merged yet. **All of the port itself is Castlesea's work**; see [the original project](#the-original-project-by-castlesea) below.

> **You need your own copy of the game.** No game files, keys or copyrighted assets are part of this repository or its releases.

> **Unofficial pre-release.** For the official version, use [Castlesea's releases](https://github.com/Castlesea/infamous-second-son-pc-port/releases).

---

## Install and run (no coding needed)

### What you need
- A Windows 10 or 11 PC (64-bit) with a graphics card that supports **Vulkan 1.3** (most cards from the last few years do).
- **Your own copy of inFAMOUS Second Son** (PS4, version 1.07, `CUSA00004` Europe or `CUSA00223` North America), as a folder that contains `eboot.bin`, `sce_sys` and `sce_module`.
- About 2 GB of free disk space.

### Steps
1. **Download.** Open the [**Releases** page](https://github.com/EmeraldZhu/infamous-second-son-pc-port/releases), find the newest release, and under **Assets** click the `.zip` file.
2. **Extract.** Right-click the zip, choose **Extract All…**, and pick a folder you own, for example `D:\Games\inFAMOUS Second Son`. Don't use `Program Files`.
3. **Start.** In the extracted folder, double-click **`inFAMOUS Second Son Launcher.exe`**.
   - If Windows shows *"Windows protected your PC"*, click **More info → Run anyway**. The program isn't code-signed, which is normal for community projects.
4. **Pick your game folder** when the launcher asks. It prepares the game in a few seconds, and your game folder is only read, never changed.
5. **Press PLAY.** The **first** start prepares the shaders for your graphics card (*"Preparing shaders (first run only)"*, about 2 minutes). Later starts take a few seconds.

### Keep your saves when you switch or update
Each copy of the port keeps its own saves in its **`user\saves`** folder.
1. Close the game and the launcher.
2. Copy **`user\saves`** from your old folder into the new folder's `user` folder. Optionally copy **`user\launcher.ini`** too, to keep your settings.
3. Start the new launcher; **Continue** loads your latest save.

Copy, don't move: then the old version still works as a fallback.

### Something went wrong?
- In the launcher, go to **ADVANCED**, turn on **Freeze and crash reports**, play until it happens again, then click **Open logs folder**.
- Open an [issue on this fork](https://github.com/EmeraldZhu/infamous-second-son-pc-port/issues) and attach that session's folder. Say which release you used.

---

## What's different from the official release

This build is Castlesea's latest official release, **`v2026.11.05`** (5 November), plus the changes below.

**Merged into Castlesea's code, not in an official release yet:** DLSS ([#65](https://github.com/Castlesea/infamous-second-son-pc-port/pull/65)) and DualSense support ([#69](https://github.com/Castlesea/infamous-second-son-pc-port/pull/69)), both described below.

**Proposed to Castlesea (open pull requests)**

| Feature | What it does | Upstream |
|---|---|---|
| Spray can on **L3 + R3** | Turns the controller on its side and shakes it; the right stick aims, R2 sprays. It ends by itself when you walk away, or 8 s after you stop spraying. B also ends it. | [#58](https://github.com/Castlesea/infamous-second-son-pc-port/pull/58) |
| New default layout | **Menu = pause**, **View = touchpad (both sides)**. View + D-pad left / right presses just that side. | [#59](https://github.com/Castlesea/infamous-second-son-pc-port/pull/59) |
| Command Center cores | Hold **View + right stick up** and the finger stays at the top of the touchpad, then press or hold **R2**. | [#60](https://github.com/Castlesea/infamous-second-son-pc-port/pull/60) |
| DualSense speaker fix | Sets the DualSense's speaker volume and routing itself, so the controller speaker is clearly audible after a fresh power-on. | [#73](https://github.com/Castlesea/infamous-second-son-pc-port/pull/73) |

If Castlesea changes or declines any of these, this build will follow his decision.

**DualSense (PS5 controller)**
- **Launcher menus and the save menu** now work with a DualSense or DualShock 4, with ✕ / ○ button hints.
- **Controller speaker:** the sounds the PS4 played on the controller (the spray can's rattle, the phone, the end of a drain) play on the DualSense's own speaker. As on a PS4, some of them also play on your PC speakers, on purpose.
  - It works when Windows lists the controller as a sound device: on a **USB cable**, through a **USB dongle** such as [DS5Dongle](https://github.com/awalol/DS5Dongle), or through [DSZ](https://github.com/MaximumFreak/dsz)'s virtual controller over Bluetooth.
  - **One-time setup:** Windows Settings → System → Sound → More sound settings → select **Speakers (DualSense Wireless Controller)** (or **Wireless Controller**) → **Configure** → **Quadraphonic**. Without it, the sounds play on your PC speakers as before.
- **Stronger rumble:** the game only uses the controller's small motor, which feels like a faint buzz on a DualSense. Now the big motor joins in, and PlayStation controllers get 1.5× strength.
- **Louder game sound on stereo speakers and headphones:** the game's 7.1 mix is folded to stereo the way a PS4 does it. Before, the game was much quieter than other ports.

**DLSS (NVIDIA RTX cards)**
- **Upscaling, in the launcher under GRAPHICS:**
  - **Upscaling:** Off / FSR 1 / DLSS.
  - **Upscaling quality:** Native / Quality / Balanced / Performance, i.e. the game renders at 100 / 67 / 58 / 50 % of your resolution and the upscaler fills the rest. With DLSS, **Native = DLAA** (anti-aliasing only).
  - At 4K, fights are limited by the graphics card: **DLSS Quality** or **Balanced** keeps them much closer to 60 FPS than native 4K.
- **DLSS needs NVIDIA's own files**, which this build can't include:
  1. Download the **Streamline SDK 2.14.16** zip from [NVIDIA's Streamline releases](https://github.com/NVIDIA-RTX/Streamline/releases).
  2. From its `bin\x64` folder, copy `sl.interposer.dll`, `sl.common.dll`, `sl.dlss.dll`, `sl.pcl.dll` and `nvngx_dlss.dll` into a folder named **`dlss`** next to `inFAMOUS Second Son Launcher.exe`.
  3. Without them, DLSS stays off and the game's own picture is used.
- In game, **Home** (Fn+End on keyboards without it) switches DLSS on and off, and **F9** shows whether it is running.
- **Stuck at 30 FPS with DLSS?** NVIDIA's *Max Frame Rate* setting fights with DLSS. In NVIDIA Control Panel → Manage 3D settings → Program Settings, add `bin\iss-probe.exe` and set **Max Frame Rate: Off** (use the launcher's frame rate limit instead). If the change doesn't apply, remove the program from the list and add it again.

### Tested on
- Ryzen 7 7800X3D + RTX 5070 Ti, Windows 11, Xbox-style controller and a DualSense (USB dongle and DSZ).
- A full 56-minute session with no crash and no freeze over a second, about 55 FPS average at the settings I play. Results are on [issue #53](https://github.com/Castlesea/infamous-second-son-pc-port/issues/53).

### Controls in this build
Everything in [Controls](#controls) below applies, **except on controllers without a touchpad** (Xbox pads and similar):

| Button | Does |
|---|---|
| **Menu** | Pause (Options) |
| **View** | Touchpad, both sides at once (covers left, right, middle and both-sides prompts) |
| **View + D-pad left / right** | Touchpad, that side only |
| **View + right stick** | Touchpad swipes |
| **View + right stick up, held** | Holds the swipe for the Command Center cores; then press or hold R2 |
| **L3 + R3** | Spray can: turn and shake; again to shake again; B or walking ends it |

You can change any of this in the launcher under **CONTROLS** and the **GAME** tab.

---

## Credits

- **[Castlesea](https://github.com/Castlesea)**: author and maintainer of the port. Everything below is his project.
- **[AMV1909](https://github.com/AMV1909)**, **[NotLeaning](https://github.com/NotLeaning)**, **[De-Os](https://github.com/De-Os)**, **[hosglial](https://github.com/hosglial)** and the other contributors to the original repository.
- **[Emerald Zhu (EmeraldZhu)](https://github.com/EmeraldZhu)**: playtesting, the fixes in #54–#57 and the proposals in #58–#60.

---

> The rest of this page is the original README from [Castlesea/infamous-second-son-pc-port](https://github.com/Castlesea/infamous-second-son-pc-port). Where the controls differ, the [Controls in this build](#controls-in-this-build) section above applies.

## The original project, by Castlesea

![Delsin at a D.U.P. checkpoint in the forest, 123 FPS](docs/media/forest-checkpoint.jpg)
*Ryzen 7 7800X3D + Radeon RX 9070 XT, Vulkan, VSync off: 123 FPS (7.5 ms a frame).*

| | |
|---|---|
| ![Seattle street in the rain, 91 FPS](docs/media/city-street.jpg) | ![Seattle rooftops at 74 FPS on a 75 Hz display](docs/media/city-rooftop.jpg) |
| *Seattle in the rain, VSync off: 91 FPS.* | *Rooftops on a 75 Hz display, VSync on: 74 FPS.* |

An experimental native Windows port of the PS4 game *inFAMOUS Second Son*.

> **You need your own copy of the game.** No game files, keys or copyrighted assets are part of this repository or its releases.

### Video showcase

#### [▶ Watch the video showcase on YouTube](https://youtu.be/V8LJlxHLb_Q)

### The idea

Most ways of playing a console game on PC emulate the console: they translate its CPU code and re-interpret, command by command, everything it asks of the GPU. This project goes the other way, and moves the game onto the PC natively, piece by piece:

- **CPU: already native.** The game's own x86-64 code runs directly on the host processor. A custom runtime replaces the PS4 system libraries (memory, threads, files, saves, audio, the controller), so no CPU emulation is involved.
- **GPU: becoming native.** The renderer started from [shadPS4](https://github.com/shadps4-emu/shadPS4)'s video core, which reads the PS4 GPU command stream and translates it to Vulkan. Step by step, the engine's rendering is taken off that translation: its draws and dispatches are recorded straight into Vulkan command buffers when the game submits them ("native passes"), and its shaders are compiled ahead of time instead of while playing.
- **The goal:** stop depending on emulation and translation altogether, so the game answers like a PC game. Less work per frame means higher frame rates, lower input latency and fewer stutters, and room for PC options (frame rate limits, unlocked frame rates, mouse and keyboard).

What is still translated today is the rest of the GPU command processor; moving it to native is the next step (see [Roadmap](#roadmap)).

### Status

- Playable: story saves, free roam, menus, pause and saving work.
- Reference machine: Ryzen 7 7800X3D + Radeon RX 9070 XT. With VSync off:
  - **Smaller scenes run above 100 FPS**: 123 FPS at the forest checkpoint.
  - **The open city runs at about 80–95 FPS**: 91 FPS in the street above.
  - **The densest city views drop to about 60–70 FPS**: there the command processor (still translated) is the limit, and it is the next thing to move to native.
- On a 75 Hz display with VSync on, the city holds 75 FPS: frames over 25 ms were cut from ~17 to ~1.4 a minute (10-minute scripted run).
- Shaders ahead of time: the game's compute shaders are compiled from the player's own game files before the first session ("Preparing shaders (first run only)", about 2 minutes). Graphics pipelines come from shader recipes (pipeline states and hashes, no shader code), rebuilt from the same files.
- Known open issues:
  - Late appearance or pop-in of some buildings and map structures.
  - Shader compiles in areas no cache has seen yet (a new player's first session).
  - Lower frame rate in the densest views (command processor bound).

### Controls

- **Controllers:** Xbox pads, PlayStation pads and Steam Input / Steam Deck. The keyboard works too.
- **Motion controls:** controllers with a gyro and an accelerometer (PlayStation pads, the Steam Controller, Steam Deck) are the spray can of the graffiti missions, as on a PS4: hold them sideways, shake, and aim by moving them. The Steam Controller and Steam Deck measure only up to 2 G, so their shake is scaled to what a DualShock 4 reports (`ISS_PAD_ACCEL_GAIN` changes it).
- **The mouse cursor** is hidden over the game window while you play with a controller, and comes back as soon as you use the keyboard or the mouse; in mouse-as-touchpad mode (F6) it stays visible. With a Steam Controller, start the game from Steam (as a non-Steam game, with Steam Input disabled for it), or Steam's desktop layout keeps using the trackpad as a mouse.
- **Other keys:** F9 shows the frame rate, Alt+Enter toggles fullscreen.
- **The ? at the top right of the launcher** lists the in-game keys below.

#### Controllers without a touchpad

The game asks for the PS4 touchpad in fast moments of gameplay (absorbing powers, finishers, prompts). On a controller without one, **View and Menu press the left and right side of the touchpad** by default, so it stays under your thumbs. **CONTROLS** in the launcher changes what each button does; PlayStation controllers use their own touchpad and keep their layout.

- **Swipes:** hold a button that presses the touchpad (View by default) and push the right stick up, down, left or right. The stick does not turn the camera while that button is held, and the touch of the button is let go after a swipe until you release it.
- **Spray can without a gyro:** at a graffiti spot, press **L3 and R3 together**. The controller is held on its side like a spray can (a short rumble confirms it) and the mouse's spray mode (F7) starts with it, so the stick and the mouse aim the same can: the right stick aims, **R2** sprays, **A** (cross on other controllers) shakes and **RB** recenters. Press L3 and R3 together again to end both. `ISS_STICK_SPRAY_SPEED` changes how fast the stick turns the can.
- Both can be turned off in the launcher's GAME tab.

![The launcher's CONTROLS page](docs/media/launcher-controls.png)

#### F5: the Touchpad & Spray window

A small window that stays on top of the game **without taking the focus**: the game keeps the keyboard and the controller while you click it. F5 shows or hides it, and each tab has its own guide.

| TOUCHPAD tab | SPRAY tab | Spray mode on |
|---|---|---|
| ![TOUCHPAD tab](docs/media/ui-touchpad.png) | ![SPRAY tab](docs/media/ui-spray.png) | ![Spray mode on](docs/media/ui-spray-on.png) |

**TOUCHPAD tab:**
- **Touchpad:** press and drag on it with the mouse, and the game sees a finger there. Right button: a touchpad click. Shift: two fingers, mirrored.
- **Left / Both / Right / Click:** press that side of the touchpad (Click: the middle), for the game's "press the touchpad" prompts.
- **Swipes:** a finger swipe up, down, left or right, for the swipe prompts.
- **Mouse as touchpad (F6):** in the game window, the left button is a finger at the cursor and the right button clicks.

**SPRAY tab: the spray can of the graffiti missions (F7).** On a PS4 you hold the controller like a spray can and move it. Here:
1. At a graffiti spot, press **START SPRAY MODE** (or F7). The virtual controller is held on its side like a can, and the cursor is hidden in the game window.
2. **Shake the can:** hold the right mouse button.
3. **Spray:** hold the left mouse button and move the mouse to paint. The mouse turns the can using its raw movement, without Windows' pointer acceleration, so the same hand movement always paints the same stroke. Shift aims finely, the middle button recenters, and **Speed** changes how far the can turns.
4. Press **F7** to end spray mode and get the cursor back. While spray mode is on, the window lets the clicks through to the game.

#### Keyboard

The whole controller is on the keyboard too, while the game window has the focus:

| Controller | Keys |
|---|---|
| Left stick (move) | W A S D |
| Right stick (camera) | I J K L (I up, K down, J left, L right) |
| Cross / Circle / Square / Triangle | N / B / V / C (or numpad 2 / 6 / 4 / 8) |
| L1 / R1 | Q / U |
| L2 / R2 | E / O |
| L3 / R3 (stick press) | X / M |
| D-pad | Arrow keys |
| Options (pause) | Esc |
| Touchpad: left side / right side / both / middle | Space or Tab / Backspace / F8 / T |
| Touchpad swipes: up / down / left / right | 1 / 2 / 3 / 4 |

| Hotkey | What it does |
|---|---|
| F5 | Shows or hides the Touchpad & Spray window |
| F6 | Mouse as touchpad on / off |
| F7 | Spray mode on / off |
| F9 | Frame rate overlay |
| Alt+Enter | Fullscreen / windowed |

### Launcher

![The launcher's main page with the in-game key guide](docs/media/launcher-help.png)

- Pick your game folder once; the launcher prepares it (your game folder is only read, never modified). With a game folder set, the launcher shows the game's own art from your files.
- DLC: your own DLC packages are read in place (costumes, Cole's Legacy).
- **Display:**
  - window mode and VSync;
  - frame rate limit: Unlimited, or 30 to 240;
  - FSR 1 upscaling.
- **Graphics:**
  - resolution: 16:9 up to 4K, 21:9 (2560x1080, 3440x1440), 24:10 (3840x1600), 32:9 (3840x1080, 5120x1440), or Desktop (your monitor's);
  - field of view: 90% to 130% of the game's;
  - HUD width: on screens wider than 16:9 the HUD edges stay in a centred 16:9 or 21:9 area, or go to the full width.
  - GPU memory: Auto reads the game's memory from copies in video memory on NVIDIA (`ISS_UNIFIED_MEMORY=0`) and in place elsewhere. On an RTX 5070 Ti the in-place reads went over PCIe: the tiled lighting shader took 33-50 ms per frame, 22 FPS instead of 117 at 1080p.

  Wider than 16:9 keeps the game's vertical view and shows more to the sides (Hor+); the menus and HUD keep their size. See [Ultrawide](#ultrawide).
- **Game:** the language, from those your edition ships (both run the same `eboot.bin`):
  - CUSA00004 (Europe), 14: English, French, Italian, German, Spanish, Dutch, Portuguese, Russian, Polish and Turkish (text and voices), Danish, Finnish, Norwegian and Swedish (subtitles, English voices);
  - CUSA00223 (North America), 4: English, French, Spanish (Latin America) and Portuguese (Brazil), all with text and voices.
- **CONTROLS:** the controller layout described above.
- **Shader cache:** it builds up from session to session. A session that crashes is rolled back, so a bad cache never sticks.
- **Advanced:** the diagnostics below, and folders (DLC, game, saves, logs) and clearing the shader cache.
  - *Command processor core:* Dedicated (default) gives the GPU command processor the last physical core alone; Shared leaves every core to the game.
  - *Pause menu acceleration:* On (default) keeps the fast native paths in the pause menu; Off draws it through the slower original path, as earlier builds did, should a menu hang the GPU.

#### Diagnostics

Each session writes `stdout.log`, `stderr.log` and `frames.csv` (the time of every frame) to `user\logs\<date-time>\`; the launcher keeps the last five sessions. Three switches on the ADVANCED page add more, all off except the first:

| Setting | What it writes | Cost |
|---|---|---|
| GPU crash diagnostics (on) | `gpu-stall-<n>.txt` when the GPU stops for over 1 s, `gpu-crash.txt` when the device is lost (`.txt` and `.json`) | GPU breadcrumbs on every submission |
| Performance log | the GPU time of each frame, `gpu_completed_work_ms` in `frames.csv` | GPU timestamps on every submission |
| Freeze and crash reports | `freeze-<n>.txt` when no frame was shown for 3 s (again at 9 s), `crash-threads.txt` on a crash: every thread's name, CPU time and stack (module+offset with the nearest export, `eboot+offset` in game code) | none until a freeze or a crash |

For a bug report: turn on *Freeze and crash reports*, play until it happens, and attach the session's folder (Open logs folder). Frames in `iss-gpu.dll` are named with `iss-gpu.map` of the same build.
### Ultrawide

`pc-port/native/ultrawide.cpp` patches the game before it starts (each patched function is checked against the 1.07 eboot first):
- `ISS_RESOLUTION=WxH`: the renderer's output and render size, which the game otherwise sets to 1920x1080. Every render target is derived from it.
- The cameras take their aspect from the UI screen size: it becomes (1080 x W/H) x 1080, so the vertical field of view stays and the view widens. The UI is laid out from the centre in units of the screen height, so it keeps its size.
- `ISS_HUD_ASPECT=a` (0: full width): the left and right HUD anchors follow the safe area margins, which are moved in to a centred a:1 area. Subtitles wrap inside it too.
- `ISS_FOV=p`: the cameras' tan(fov/2) times p/100.
- Render size limit: the forward shaders walk per-tile light lists (16x16 pixel tiles) until a terminator, and the lists live in a buffer of fixed size. With too many tiles the last lists are never written and the GPU hangs (on NVIDIA and AMD alike): the title screen at 5120x1440, a cutscene at 4984x1400. The picture is rendered with at most as many tiles as the game uses on PS4 Pro (3200x1800, 22600 tiles; `ISS_RENDER_MAX_TILES`), in the same aspect, and the window scales it up: 5120x1440 renders at 4520x1264, 3440x1440 and smaller at their own size.
- Above 1080p the game gets 5.5 GiB of direct memory instead of 4.5 (`ISS_DIRECT_MEMORY_MB`): its main heap, where the render targets live too, ran out at 5120x1440.
- Cutscenes are rendered by the engine at the full width, without black bars. Full-screen UI backdrops made for 16:9 (the title screen's black background, the opening text) cover only the centre.

The launcher sets all three from **SETTINGS > GRAPHICS**. The window keeps the picture's aspect; in fullscreen on a monitor of the same aspect the picture fills it.

### Repository layout

| Path | What it holds |
|---|---|
| `pc-port/src/` | Loader and PS4 runtime (C): memory, threads, files, controller and touchpad window (SDL3, Win32), audio, saves, video glue |
| `pc-port/gpu/` | Renderer: shadPS4 video core overrides (`overrides/`), shims (`shim/`), native renderer (`native_*`) |
| `pc-port/native/` | Native C++ reimplementations of selected engine routines |
| `pc-port/scripts/` | Game preparation, build, play launcher and analysis scripts |
| `pc-port/tests/` | Runtime, controller and renderer unit tests |
| `pc-port/launcher/` | The release launcher (C++, `scripts/build_release.py` packages it) |
| `pc-port/third_party/` | `shadPS4-perf-local.patch`: the changes this port makes to its shadPS4 base |
| `launcher/` | Older PowerShell launcher (development) |

Local-only folders (git-ignored):
- `research/`: the shadPS4 sources the renderer is built from.
- `build-opt/`, `build-sdl/`: CMake builds that supply flags, SDL3 and zydis.
- `tools/`: the LLVM toolchain.
- `pc-port/out/`: builds, runs, caches and saves.

### Building

Requirements:
- Windows 11.
- Visual Studio 2022 or 2026 with "Desktop development with C++" (MSVC, Windows SDK); found with vswhere, or `ISS_VCVARS`.
- LLVM `clang-cl` in `tools/llvm/`, or Visual Studio's "C++ Clang Compiler for Windows" component, or `ISS_CLANG`.
- Python 3.12.
- Python package `iced-x86` for the guarded linked-image compatibility patch: `py -3.12 -m pip install iced-x86`.
- shadPS4 sources in `research/shadPS4-perf`: [weshayoub92/shadPS4-perf](https://github.com/weshayoub92/shadPS4-perf) at commit `584374867d6a`, with `pc-port/third_party/shadPS4-perf-local.patch` applied (`git apply`). Configure it with CMake into `build-opt/` (renderer flags and zydis) and `build-sdl/` (SDL3).

```bat
cd pc-port\scripts
python prepare.py --game "<your game folder>"         & rem reads eboot/modules/param.sfo only
python link_modules.py --game "<your game folder>"
python build.py                                       & rem iss-probe.exe (loader + runtime) and its tests
python build_gpu.py --jobs 12                         & rem iss-gpu.dll (renderer)
python build_release.py --name <folder>               & rem the release folder (launcher included)
```

### Running

- Release: extract the zip, run `inFAMOUS Second Son Launcher.exe` and pick your game folder.
- Development: `python pc-port/scripts/play_porte.py` starts the current development build.
- The first start prepares the shaders. Later starts load the cache in about a second.

Most behaviour is controlled with `ISS_*` environment variables, set by the launcher and the scripts. `pc-port/scripts/play_porte.py` lists the ones the current build turns on, with the reason and the measurement behind each.

### Roadmap

1. **Finish moving the GPU command processor to native.** This is the last big translated part. It means cheaper native pass execution, no waiting on the recording pool, asynchronous readbacks and the remaining non-native draws. It is the limit in the densest views today.
2. **Small fixes in the same pass:**
   - shader recipe coverage, for fewer compiles in a new player's first session;
   - the remaining streaming-burst frames.
3. **A full code review** and clean-up pass.

### Contributors

- **[Castlesea](https://github.com/Castlesea)**: author and maintainer.
- **Claude** (Anthropic): AI pair programmer. Engineering, profiling and code across the runtime, the renderer and the launcher.

### License and credits

GPL-2.0-or-later (see `pc-port/LICENSE` and `pc-port/THIRD_PARTY.md`). The project builds on:
- the shadPS4 video core and shader recompiler;
- the native-port approach of bloodborne_pc;
- SDL3, Vulkan, Xbyak, zydis and the other libraries listed in `THIRD_PARTY.md`.

*inFAMOUS* is a trademark of Sony Interactive Entertainment. This project is not affiliated with Sony or Sucker Punch Productions.
