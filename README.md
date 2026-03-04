# 🟣 Thanos Gauntlet FPS
### *Six Stones. One Snap. Infinite FPS.*

[![Minecraft 1.21.1](https://img.shields.io/badge/Minecraft-1.21.1-brightgreen)](https://minecraft.net/)
[![Fabric Loader](https://img.shields.io/badge/Fabric%20Loader-0.15.11+-blue)](https://fabricmc.net/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Modrinth](https://img.shields.io/badge/Modrinth-Available-green)](https://modrinth.com/mod/thanos-gauntlet-fps)
[![GitHub](https://img.shields.io/badge/GitHub-Source-black)](https://github.com/thanosmod/thanos-gauntlet-fps)

> *The ultimate Fabric performance optimizer. Auto-tunes FPS, entities, chunks, redstone, and shaders. Works alongside Sodium + Iris for the smoothest Minecraft experience.*

---

## 🎮 What Does This Mod Do?

If Minecraft runs slowly on your computer, this mod fixes that — automatically.

When you load a world, it reads your computer's specs (CPU, RAM, graphics card), figures out what settings your PC can handle, and applies them for you. It also watches your FPS while you play and quietly adjusts things in the background to keep the game smooth — no restarts needed.

Think of it like having a smart assistant that constantly tweaks Minecraft's settings so you get the best performance possible without having to touch anything yourself.

---

## 🖥️ Minecraft Version

| Minecraft Version | Supported |
|---|---|
| **1.21.1** | ✅ Yes — this is the target version |
| 1.21.2 / 1.21.3 / 1.21.4 | ⚠️ May work but not tested |
| 1.20.x and below | ❌ No |
| Forge / NeoForge | ❌ No — Fabric only |

> **This mod requires Fabric, not Forge.** If you use the Fabric launcher, you're good. If you use Forge, this mod won't work.

---

## ⬡ The Six Infinity Stones (Features)

Each feature is named after an Infinity Stone. Here's what each one actually does in plain English:

| Stone | What it does for you |
|---|---|
| 🔴 **Reality Stone** | Controls how far away you can see. Automatically lowers this if your PC is struggling. |
| 🟣 **Power Stone** | Stops mobs that are far away from doing complex AI calculations. You won't notice — they'll still move, just less frantically when they're not near you. |
| 🔵 **Space Stone** | Cleans up memory while you play, so the game doesn't get slower the longer you're in a world. |
| 🟢 **Time Stone** | Skips redstone and particle effects that are too far away for you to see anyway. Big redstone farms won't eat your FPS anymore. |
| 🟡 **Mind Stone** | The brain of the mod. Reads your hardware, watches your FPS every 5 seconds, and adjusts everything automatically. |
| 🟠 **Soul Stone** | Adds a small FPS counter to your screen and flashes a warning if your game drops too low. |
| ⚪ **Chaos Stone** | Optional debug info, a "Dream Mode" that removes all particles for maximum performance, and a hotkey to switch modes on the fly. |

---

## 🚀 Installation (Step by Step)

**Required:**
1. Install [Fabric Loader for Minecraft 1.21.1](https://fabricmc.net/use/installer/)
2. Download and put [Fabric API](https://modrinth.com/mod/fabric-api) in your `mods` folder
3. Download `thanos-gauntlet-fps-1.0.0.jar` from [Modrinth](https://modrinth.com/mod/thanos-gauntlet-fps) and put it in your `mods` folder
4. Launch Minecraft with the Fabric profile — done!

**Optional but recommended:**
- [Sodium](https://modrinth.com/mod/sodium) — makes rendering much faster (the mod detects it and adjusts automatically)
- [Iris](https://modrinth.com/mod/iris) — shader support (the mod detects active shaders and reduces heavy settings to compensate)
- [Cloth Config](https://modrinth.com/mod/cloth-config) — needed for the in-game settings screen
- [ModMenu](https://modrinth.com/mod/modmenu) — adds a "Mods" button to the main menu so you can open settings easily

> **Where is my mods folder?**
> Press `Win + R`, type `%appdata%\.minecraft\mods` and hit Enter.

---

## ⚙️ Settings & Configuration

### Easy way — In-game settings screen
If you have Cloth Config + ModMenu installed:
1. Click **Mods** on the main menu
2. Find **Thanos Gauntlet FPS**
3. Click the settings icon

You'll see seven tabs (one per Stone) with sliders and toggles.

### Manual way — Config file
The mod creates a config file at:
```
.minecraft/config/thanos-gauntlet-fps.json
```
You can open it in any text editor (like Notepad) and change values manually.

---

## 🎮 Performance Modes

Press **K** in-game to cycle through modes, or change it in the settings screen.

| Mode | Best for | What gets changed |
|---|---|---|
| 🔴 **Low-End** | Old/slow PCs, laptops | Render distance 6, particles 30%, mobs stop AI-ing at 16 blocks away |
| 🟡 **Balanced** | Most players | Render distance 10, particles 70%, mobs stop AI-ing at 32 blocks away |
| 🟢 **Ultra** | High-end PCs | Render distance 16, full particles, almost no restrictions |
| ⚙️ **Custom** | Power users | You control everything manually |

The mod will also **auto-switch** between these behind the scenes based on your live FPS — you don't have to do it manually.

---

## ❓ Frequently Asked Questions

**Does this work with Optifine?**
No. Optifine is not compatible with Fabric. Use Sodium + Iris instead — they're better anyway.

**Will this break my redstone farms?**
Only redstone that's very far away from any player gets skipped. If you're standing near your farm, it runs normally. You can also turn this feature off in settings.

**Does this work on servers?**
Yes. The server-side optimisations (entity AI, redstone skipping) work on any server running this mod. The client-side features (HUD, particles) work in singleplayer and on any server.

**Is the sources JAR on GitHub necessary?**
No. The `-sources.jar` file is for developers who want to read the mod's code from inside their IDE. Normal players only need the regular `.jar` file.

---

## 📦 Files Explained (For GitHub / Modrinth)

When you build the mod, you get two files in `build/libs/`:

| File | What it is | Who needs it |
|---|---|---|
| `thanos-gauntlet-fps-1.0.1.jar` | The actual mod | **Everyone** — this is what goes in the mods folder |
| `thanos-gauntlet-fps-1.0.1-sources.jar` | The mod's source code | Developers only — skip this if you just want to play |

**For Modrinth:** Upload only `thanos-gauntlet-fps-1.0.1.jar`

**For GitHub:** You can upload both as release assets. The source code itself is already on GitHub, so the sources jar is optional.

---

## 🛠️ Building from Source (For Developers)

Want to contribute or modify the mod? Here's how to build it yourself.

**Requirements:**
- Java 21 ([download here](https://adoptium.net/))
- The source code (clone or download from GitHub)

**Steps:**
```bash
git clone https://github.com/thanosmod/thanos-gauntlet-fps
cd thanos-gauntlet-fps

# Windows
gradlew.bat build

# Mac / Linux
./gradlew build
```

The built jar will appear at `build/libs/thanos-gauntlet-fps-1.0.0.jar`.

**To test in Minecraft directly from VS Code:**
Run the Gradle task `Tasks → fabric → runClient` — this launches Minecraft with the mod loaded automatically, no copying needed.

---

## 🔬 How the Auto-Tune Works (Technical)

```
On world load:
  1. Read CPU cores, RAM, GPU name → classify hardware as LOW / MID / HIGH
  2. Detect if Sodium and/or Iris are installed
  3. If Iris shaders are active → reduce render distance by 2, particles by 30%
  4. Apply the hardware-appropriate preset (Low-End / Balanced / Ultra)

Every 5 seconds while playing:
  5. Sample current FPS (rolling average of last 5 readings)
  6. If FPS drops below 80% of target → cut one setting:
       first particles, then entity AI distance, then render distance
  7. If FPS is above 120% of target → restore one setting (reverse order)
  8. Save changes to config file
```

---

## 🤝 Mod Compatibility

| Mod | Works with? |
|---|---|
| Sodium | ✅ Fully supported — detected automatically |
| Iris Shaders | ✅ Fully supported — shader budget applied |
| ModMenu | ✅ Config screen shows up in mod list |
| Cloth Config | ✅ Optional — mod works fine without it |
| Lithium | ✅ Compatible |
| FerriteCore | ✅ Compatible |
| EntityCulling | ✅ Compatible |
| Optifine | ❌ Not compatible (Optifine doesn't work with Fabric) |
| Forge mods | ❌ Not compatible |

---

## 📂 Project Structure (For Developers)

```
src/main/java/com/thanosmod/
├── ThanosGauntletFPS.java          # Mod startup (common/server)
├── ThanosGauntletFPSClient.java    # Mod startup (client only)
├── config/
│   ├── ThanosConfig.java           # All settings in one class
│   └── ConfigManager.java          # Reads/writes the JSON config file
├── modules/
│   ├── RealityStone.java           # Render distance control
│   ├── PowerStone.java             # Entity AI throttling
│   ├── SpaceStone.java             # Memory cleanup
│   ├── TimeStone.java              # Redstone + particle throttling
│   ├── MindStone.java              # Mode switching
│   ├── SoulStone.java              # HUD overlay
│   └── ChaosStone.java             # Debug tools + Dream Mode
├── mixin/                          # Hooks into Minecraft's internals
│   ├── EntityTickMixin.java        # Skips distant mob AI
│   ├── WorldTickMixin.java         # Batch update flush
│   ├── RedstoneMixin.java          # Skips distant redstone
│   ├── ParticleClientMixin.java    # Particle density gate
│   ├── ClientTickMixin.java        # Re-applies render distance
│   ├── WorldRendererMixin.java     # Frame time debug hook
│   ├── ServerChunkManagerMixin.java # Async lighting gate
│   └── GameRendererMixin.java      # Render budget (future)
├── autotune/
│   ├── SystemDetector.java         # Reads CPU / RAM / GPU
│   └── AutoTuner.java              # Live FPS monitor + adjuster
├── shader/
│   └── ShaderDetector.java         # Detects Sodium + Iris
└── gui/
    ├── ThanosConfigScreen.java     # In-game settings screen
    └── ThanosModMenuIntegration.java # ModMenu integration
```

---

## 📜 License

MIT — free to use, modify, and redistribute. Just don't claim you built it yourself.

---

*"Fine. I'll do it myself." — and then FPS went from 12 to 144.*
