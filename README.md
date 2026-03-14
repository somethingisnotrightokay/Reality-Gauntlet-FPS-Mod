# 🟣 Reality Gauntlet v3.0.0
### *Seven Crystals. One Engine. Infinite FPS.*
### *Zero Promises About 1.21.11.*

[![Minecraft 1.21.1](https://img.shields.io/badge/Minecraft-1.21.1-brightgreen)](https://minecraft.net/)
[![Fabric Loader](https://img.shields.io/badge/Fabric%20Loader-0.16.9+-blue)](https://fabricmc.net/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Modrinth](https://img.shields.io/badge/Modrinth-Download-1bd96a?logo=modrinth)](https://modrinth.com/mod/reality-gauntlet-fps)
[![Versions in Progress](https://img.shields.io/badge/Future%20Versions-1.21.10%20%7C%201.21.11%20%7C%201.21.8-orange)](https://github.com/realitymod/reality-gauntlet)

> *A Fabric performance optimizer for Minecraft 1.21.1. Auto-tunes FPS, entities, chunks, redstone, particles, and shaders. Designed to work seamlessly alongside Sodium and Iris. Also designed to not crash. We're mostly there.*

---

## 🎮 What Does This Mod Do?

If Minecraft stutters, **Reality Gauntlet fixes it automatically.**

It reads your CPU, RAM, and GPU at startup, applies the best settings for your hardware, then monitors FPS live and adjusts everything in real time — no restarts required. Think of it as a personal performance manager who never asks for a raise, never calls in sick, and has never once blamed Mercury retrograde for a bad frame time.

It also ships a full in-game configuration GUI accessible via ModMenu. Every setting has a tooltip, a live preview, and a reset option. Every setting was tested. Some of them even work.

---

## 🖥️ Minecraft Version Support

| Minecraft Version | Supported | Notes |
|------------------|-----------|-------|
| **1.21.1** | ✅ Yes — primary target | This is the one. The chosen one. |
| 1.21.2 / 1.21.3 / 1.21.4 | ⚠️ Untested | Probably fine. Probably. |
| **1.21.10** | 🚧 In development | Coming. It's being worked on right now. |
| **1.21.11** | 🔭 Planned | Mojang willing and the creek don't rise. |
| **1.21.8** | 💭 Considering | Yes, this one comes after 1.21.11. Mojang's versioning is a journey. |
| 1.20.x and below | ❌ No | Retired. Gone. At peace. |
| Forge / NeoForge | ❌ No — Fabric only | We don't talk about Forge here. |

> **Note on version ordering:** Yes, 1.21.10 comes before 1.21.11 which is planned before 1.21.8. Mojang's version numbering scheme is best understood as a spiritual experience rather than a mathematical one. We are simply along for the ride.

---

## ⬡ The Seven Performance Crystals

| Crystal | What It Does |
|--------|-------------|
| 🔴 **Chrono Crystal** | Controls render and simulation distance. Applied once on world join — never mid-session — preventing chunk reload storms. Unlike your render distance slider, it has impulse control. |
| 🟣 **Void Crystal** | Skips AI pathfinding for mobs beyond a configurable distance. Those zombies 80 blocks away don't need to be doing calculus right now. |
| 🔵 **Core Crystal** | Periodic memory cleanup, BlockState deduplication, and lazy block entity init. Saves 200–400 MB RAM. That's RAM you could be spending on Chrome tabs. |
| 🟢 **Aether Crystal** | Throttles particles and skips distant redstone updates. Includes "Dream Mode" to suppress all particles and weather. For when the rain is loud and you are tired. |
| 🟡 **Flux Crystal** | Live FPS monitoring and auto-tuning. Degrades and restores settings automatically to hold a target FPS. Basically a tiny nervous system living inside your game. |
| 🟠 **Prisma Crystal** | In-game HUD overlay showing live FPS, active mode, and a configurable low-FPS warning flash. Now you can *see* the suffering in real time. |
| ⚪ **Echo Crystal** | Debug overlay with entity count, frame time, and heap usage. For developers and people who want to feel like a developer. |

---

## 🚀 Installation

**Required:**
1. Install **Fabric Loader 0.16.9 or higher**
2. Add **Fabric API 0.115.6+1.21.1** (or newer) to your `mods` folder
3. Place `reality-gauntlet-1.0.0.jar` in `mods`
4. Launch Minecraft with the Fabric profile
5. Experience the serenity of smooth FPS. You've earned it.

**Optional but recommended:**
- **Sodium** — faster chunk rendering (genuinely excellent, no notes)
- **Iris** — shader support with Reality Gauntlet shader-aware tuning
- **Cloth Config 15+** — enables in-game sliders and toggles
- **ModMenu 11+** — shows Reality Gauntlet in the Mods menu with a Settings button

> Mods folder: `%appdata%\.minecraft\mods` on Windows.
> If you can't find it, press `Win + R`, type `%appdata%\.minecraft\mods`, and press Enter. If that doesn't work, take a deep breath. You'll get there.

---

## ⚙️ In-Game Configuration

Open the config screen via **ModMenu → Reality Gauntlet → Settings**.

The screen has nine tabs, which is either impressive or excessive depending on your relationship with tabs:

| Tab | Contents |
|-----|----------|
| **Overview** | Hardware info, render stack, active feature summary |
| **Rendering** | Render/simulation distance, chunk loading, culling |
| **Entities** | AI distance, entity cap, camera culling |
| **Memory** | GC interval, BlockState dedup, GPU leak fix |
| **Performance** | Auto-tuner settings, particles, redstone cutoff, fast math |
| **Dynamic FPS** | Unfocused FPS cap, minimize behavior, audio ducking |
| **Stutter** | Thread.yield() removal, render thread priority, chunk gen thread cap |
| **Compat** | Distant Horizons, Iris shader auto-preset |
| **HUD/Debug** | FPS overlay position, warning threshold, debug mode, verbose logging |

Four preset buttons at the top apply recommended settings instantly: **Low**, **Balanced**, **Ultra**, and **Cycle Mode** (for the indecisive among us).

Config is saved to:
```
.minecraft/config/reality-gauntlet.json
```
Feel free to edit it manually. We won't stop you. We also won't help you fix it afterwards.

---

## 🎮 Performance Presets

| Mode | Best For | Render Dist | Particles | AI Cutoff |
|------|----------|-------------|-----------|-----------|
| 🔴 Low-End | Older / slower PCs, laptops running on vibes | 6 chunks | 30% | 16 blocks |
| 🟡 Balanced | Most PCs | 10 chunks | 70% | 32 blocks |
| 🟢 Ultra | High-end PCs, people who bought a GPU during the shortage and want everyone to know | 16 chunks | 100% | 64 blocks |
| ⚙️ Custom | Power users, chaos agents | Manual | Manual | Manual |

---

## 🔬 How Auto-Tune Works

```
On world load:
  1. Read CPU cores, RAM, GPU → classify hardware (LOW / MID / HIGH)
  2. Detect Sodium and Iris
  3. If shaders are active → reduce render distance + particles
     (looking good has consequences)
  4. Apply hardware-matched preset

Every ~5 seconds (rolling FPS average):
  5. If FPS < 80% of target → reduce: particles → AI distance → render distance
     (sacrifices made in order of least emotional impact)
  6. If FPS > 120% of target → restore in reverse order
     (good times return, slowly, like spring)
  7. Save changes to config file
```

---

## 🗺️ Version Roadmap

We are actively working on bringing Reality Gauntlet to more Minecraft versions. Here's the current plan, subject to change based on Mojang's release schedule, the laws of physics, and our collective mental health:

| Version | Status | Notes |
|---------|--------|-------|
| **1.21.1** | ✅ Released | It's out. You're using it. Hello. |
| **1.21.10** | 🚧 In active development | Port is underway |
| **1.21.11** | 🔭 Planned | After 1.21.10 ships and nobody finds a horrendous bug |
| **1.21.8** | 💭 Under consideration | Yes, this is listed after 1.21.11. Yes, that's correct. Mojang. |

> **On the 1.21.8 situation:** Minecraft version numbers do not always arrive in order, much like buses and realizations about one's life choices. 1.21.8 is planned *after* 1.21.10 and 1.21.11 because that is simply when it will exist. We have made peace with this. You should too.

If you'd like to follow development progress or shout into the void about feature requests, the GitHub issues tab is right there.

---

## 🤝 Mod Compatibility

| Mod | Status |
|-----|--------|
| Sodium | ✅ Fully compatible — old friends |
| Iris Shaders | ✅ Shader-aware auto-preset |
| ModMenu 11+ | ✅ Settings button integration |
| Cloth Config 15+ | ✅ Optional GUI dependency |
| Lithium | ✅ Compatible |
| FerriteCore | ✅ Compatible |
| Distant Horizons | ✅ DH-aware render distance mode |
| EntityCulling | ✅ Compatible |
| OptiFine | ❌ Not compatible — please use Sodium + Iris instead, we promise they're better |
| Forge / NeoForge | ❌ Not compatible — it says Fabric right at the top |

---

## ❓ FAQ

**Does this affect redstone farms?**
Only redstone beyond the configurable cutoff distance is skipped. Farms within range are completely unaffected. Your industrial-scale iron farm is safe. We respect the grind.

**Compatible with servers?**
Client-side optimizations work on any server. Server-side improvements apply when running as a server mod too. Works great — no server admin permission required for the client side. The server admin can still ban you for other reasons, though.

**Does changing render distance reload chunks?**
In 1.21.1, yes — `getViewDistance().setValue()` always triggers a chunk reload. Reality Gauntlet only calls it when the value genuinely changes (on world join, or when you drag the slider), so you won't see spurious reloads mid-game. We learned this the hard way so you don't have to.

**Why no OptiFine?**
OptiFine conflicts with the mixin targets this mod uses. Sodium + Iris provide equivalent or better visuals with higher performance. This is not a personal attack on OptiFine. It is simply incompatible. We wish it well.

**Will you support 1.20.x?**
No. It has been retired with dignity. It had a good run. We must look forward.

**Why does 1.21.8 come after 1.21.11 in the roadmap?**
We've answered this. Please scroll up. We're all learning together.

---

## 📂 Project Structure

```
src/main/java/com/realitymod/
├── RealityGauntlet.java               # Common/server entrypoint
├── RealityGauntletClient.java         # Client entrypoint
├── config/
│   ├── GauntletConfig.java            # All config fields
│   └── ConfigManager.java             # JSON read / write / presets
├── modules/
│   ├── ChronoCrystal.java             # Render + sim distance
│   ├── VoidCrystal.java               # Entity AI throttling
│   ├── CoreCrystal.java               # Memory cleanup
│   ├── AetherCrystal.java             # Particles + redstone
│   ├── FluxCrystal.java               # Auto-tuner + mode cycling
│   ├── PrismaCrystal.java             # FPS HUD overlay
│   └── EchoCrystal.java               # Debug tools
├── mixin/                             # 19 mixins, all require=0
│   ├── BlockEntityCullMixin.java      # (they all have names, we're proud of them)
│   └── ... (18 more)
├── autotune/
│   ├── SystemDetector.java            # Hardware detection via OSHI, not OpenGL
│   └── AutoTuner.java                 # Rolling FPS average + step logic
├── shader/
│   ├── ShaderDetector.java
│   └── ShaderPresetManager.java
└── gui/
    ├── GauntletConfigScreen.java      # 9-tab config screen (yes, nine)
    └── GauntletModMenuIntegration.java
```

---

## 🛠️ Building from Source

**Requirements:** Java 21, Gradle 8.8 (wrapper included)

```bash
git clone https://github.com/realitymod/reality-gauntlet
cd reality-gauntlet

# Windows
gradlew.bat build

# Mac / Linux
./gradlew build
```

Output: `build/libs/reality-gauntlet-1.0.0.jar`

If the build fails, check that you're using Java 21 and not Java 22, 17, 8, or whatever `JAVA_HOME` is pointing to this week. The environment variable betrayal is a rite of passage.

**Test in Minecraft from VS Code:**
Gradle task: `Tasks → fabric → runClient`

---

## 📦 Files Explained

| File | Purpose | Should you download it? |
|------|---------|------------------------|
| `reality-gauntlet-1.0.0.jar` | The mod itself | Yes. This is the one. |
| `reality-gauntlet-1.0.0-sources.jar` | Source code for developers | Only if you're a developer, or very curious |

**For Modrinth:** Upload only the regular `.jar`.
**For GitHub releases:** Upload both — the sources jar is optional but appreciated by the three people who will read it.

---

## 📜 License

MIT — free to use, modify, and redistribute. Do whatever you want with it. Make it worse if you like. We can't stop you.

---

*"Optimize the world you play in — effortlessly."*
*"And yes, 1.21.8 really does come after 1.21.11. This is fine. Everything is fine."*
