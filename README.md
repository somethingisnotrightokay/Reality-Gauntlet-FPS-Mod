# 🟣 Thanos Gauntlet FPS v3
### *Six Stones. One Snap. Infinite FPS.*

[![Minecraft 1.21.1](https://img.shields.io/badge/Minecraft-1.21.1-brightgreen)](https://minecraft.net/)
[![Fabric Loader](https://img.shields.io/badge/Fabric%20Loader-0.15.11+-blue)](https://fabricmc.net/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Modrinth](https://img.shields.io/badge/Modrinth-Available-green)](https://modrinth.com/mod/thanos-gauntlet-fps)
[![GitHub](https://img.shields.io/badge/GitHub-Source-black)](https://github.com/thanosmod/thanos-gauntlet-fps)

> *The ultimate Fabric performance optimizer. Fully audited and bug-fixed. Auto-tunes FPS, entities, chunks, redstone, and shaders. Works alongside Sodium + Iris for the smoothest Minecraft experience.*

---

## 🎮 What Does This Mod Do?

If Minecraft runs slowly, this mod fixes it automatically.  
It reads your CPU, RAM, and GPU, applies optimal settings, monitors FPS live, and adjusts things in real-time — no restarts needed. Think of it as a smart assistant keeping Minecraft smooth without you lifting a finger.

---

## 🖥️ Minecraft Version

| Minecraft Version | Supported |
|------------------|-----------|
| **1.21.1**        | ✅ Yes — v3 target version |
| 1.21.2 / 1.21.3 / 1.21.4 | ⚠️ May work but untested |
| 1.20.x and below | ❌ No |
| Forge / NeoForge | ❌ No — Fabric only |

> **Requires Fabric, not Forge.**

---

## ⬡ The Six Infinity Stones (Features)

| Stone | Feature |
|-------|---------|
| 🔴 Reality Stone | Auto-adjusts render distance based on hardware and FPS |
| 🟣 Power Stone | Skips AI updates for distant mobs to improve performance |
| 🔵 Space Stone | Cleans memory dynamically to prevent slowdowns |
| 🟢 Time Stone | Skips faraway redstone and particles |
| 🟡 Mind Stone | Auto-tunes settings live based on FPS and hardware |
| 🟠 Soul Stone | HUD overlay with FPS and drop warnings |
| ⚪ Chaos Stone | Optional debug tools and “Dream Mode” for max FPS |

---

## 🚀 Installation

**Required:**
1. Install [Fabric Loader 0.15.11+](https://fabricmc.net/use/installer/) for MC 1.21.1
2. Place [Fabric API](https://modrinth.com/mod/fabric-api) in your `mods` folder
3. Place `thanos-gauntlet-fps-3.0.0.jar` in `mods`
4. Launch Minecraft with the Fabric profile

**Optional:**
- [Sodium](https://modrinth.com/mod/sodium) — faster rendering  
- [Iris](https://modrinth.com/mod/iris) — shader support  
- [Cloth Config](https://modrinth.com/mod/cloth-config) — in-game settings GUI  
- [ModMenu](https://modrinth.com/mod/modmenu) — access settings via Mods menu

> Mods folder: `%appdata%\.minecraft\mods`

---

## ⚙️ Settings & Configuration

**In-game GUI (recommended)**: ModMenu + Cloth Config: sliders & toggles for each Stone.  

**Manual config file:**  

.minecraft/config/thanos-gauntlet-fps.json

---

## 🎮 Performance Modes

Press **K** to cycle modes:

| Mode | Best for | Effect |
|------|----------|-------|
| 🔴 Low-End | Old/slow PCs | Render 6, particles 30%, AI stops >16 blocks |
| 🟡 Balanced | Most PCs | Render 10, particles 70%, AI stops >32 blocks |
| 🟢 Ultra | High-end PCs | Render 16, full particles, minimal restrictions |
| ⚙️ Custom | Power users | Manual control of all settings |

> Auto-switching adjusts settings live based on FPS.

---

## ❓ FAQ

**Optifine compatible?** ❌ No — use Sodium + Iris  
**Redstone farms affected?** ❌ Only distant redstone skipped  
**Server compatibility?** ✅ Client works anywhere; server optimizations active on any server  
**Sources jar needed?** ❌ Only for developers

---

## 📦 Files

| File | Purpose |
|------|--------|
| `thanos-gauntlet-fps-3.0.0.jar` | Main mod — everyone |
| `thanos-gauntlet-fps-3.0.0-sources.jar` | Source code — developers only |

---

## 🛠️ Building from Source

**Requirements:** Java 21 + Gradle

```bash
git clone https://github.com/thanosmod/thanos-gauntlet-fps.git
cd thanos-gauntlet-fps

# Windows
gradlew.bat build

# Mac / Linux
./gradlew build

Built jar: build/libs/thanos-gauntlet-fps-3.0.0.jar
Run directly in IDE: Gradle task runClient
```
#🔬 Auto-Tune Logic

On world load:

Detect CPU, RAM, GPU → classify LOW / MID / HIGH
Detect Sodium/Iris → apply shader budget
Apply preset (Low / Balanced / Ultra)

Every 5 seconds:

Sample FPS
If FPS < 80% target → reduce particles → AI → render distance
If FPS > 120% target → restore settings
Save to config

## 🤝 Mod Compatibility

| Mod           | Compatible?           |
|---------------|---------------------|
| Sodium        | ✅ Auto-detected     |
| Iris Shaders  | ✅ Auto-budgeted     |
| ModMenu       | ✅ Config screen visible |
| Cloth Config  | ✅ Optional          |
| Lithium       | ✅ Compatible        |
| FerriteCore   | ✅ Compatible        |
| EntityCulling | ✅ Compatible        |
| Optifine      | ❌ Not compatible   |
| Forge mods    | ❌ Not compatible   |



## 📂 Project Structure

| Path | Description |
|------|-------------|
| `src/main/java/com/thanosmod/ThanosGauntletFPS.java` | Common entry point for the mod |
| `src/main/java/com/thanosmod/ThanosGauntletFPSClient.java` | Client-side entry point |
| `src/main/java/com/thanosmod/config/` | Configuration files and manager |
| `src/main/java/com/thanosmod/modules/` | Infinity Stone modules (features) |
| `src/main/java/com/thanosmod/mixin/` | Mixins hooking into Minecraft internals |
| `src/main/java/com/thanosmod/autotune/` | FPS monitoring and auto-tuning logic |
| `src/main/java/com/thanosmod/shader/` | Sodium/Iris shader detection |
| `src/main/java/com/thanosmod/gui/` | ModMenu integration and settings screens |





📜 License
MIT — free to use, modify, redistribute. Don’t claim as your own.
"Fine. I'll do it myself." — and then FPS went from 12 to 144.
