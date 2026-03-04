# 🟣 Thanos Gauntlet FPS
### *Six Stones. One Snap. Infinite FPS.*

[![Fabric 1.21.x](https://img.shields.io/badge/Fabric-1.21.x-blue)](https://fabricmc.net/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Modrinth](https://img.shields.io/badge/Modrinth-Available-green)](https://modrinth.com/mod/thanos-gauntlet-fps)

> "The ultimate Fabric performance optimizer. Auto-tunes FPS, entities, chunks,  
> redstone, and shaders. Works alongside Sodium + Iris for the smoothest Minecraft experience."

---

## ⬡ The Six Infinity Stones

| Stone | Module | What it does |
|---|---|---|
| 🔴 **Reality** | `RealityStone` | Dynamic chunk loading, async lighting, configurable render distance |
| 🟣 **Power** | `PowerStone` | AI tick suppression for distant mobs, entity caps per dimension |
| 🔵 **Space** | `SpaceStone` | Lazy tile entity init, async block updates, scheduled GC cleanup |
| 🟢 **Time** | `TimeStone` | Skip distant redstone, batch scheduled ticks, particle throttling |
| 🟡 **Mind** | `MindStone` + `AutoTuner` | Hardware detection, live FPS monitoring, dynamic setting adjustment |
| 🟠 **Soul** | `SoulStone` | Lightweight FPS HUD, FPS-critical warnings, per-corner HUD position |
| ⚪ **Chaos** | `ChaosStone` | Debug overlay, Dream Mode (no particles), verbose logging |

---

## 🚀 Installation

1. Install [Fabric Loader](https://fabricmc.net/use/installer/) for Minecraft **1.21.1**
2. Install [Fabric API](https://modrinth.com/mod/fabric-api)
3. **Optionally** install [Sodium](https://modrinth.com/mod/sodium) + [Iris](https://modrinth.com/mod/iris) (detected automatically)
4. **Optionally** install [Cloth Config](https://modrinth.com/mod/cloth-config) (for the in-game GUI)
5. **Optionally** install [ModMenu](https://modrinth.com/mod/modmenu) (to open settings from the main menu)
6. Drop `thanos-gauntlet-fps-1.0.0.jar` into your `mods/` folder
7. Launch the game — the mod auto-detects your hardware and suggests a mode on first world load

---

## ⚙️ Configuration

### In-game GUI
Open **Mod Menu → Thanos Gauntlet FPS → Configure** (requires Cloth Config + ModMenu).  
Seven colour-coded tabs, one per stone. Sliders, toggles, and an Apply button.

### JSON config file
Located at:
```
<minecraft dir>/config/thanos-gauntlet-fps.json
```

Example (Balanced defaults):
```json
{
  "renderDistance": 10,
  "simulationDistance": 8,
  "asyncLighting": true,
  "entityTickDistance": 32,
  "entityCap": 200,
  "skipDistantAI": true,
  "lazyTileEntities": true,
  "memoryCleanupInterval": 60,
  "skipDistantRedstone": true,
  "redstoneCutoffDist": 48,
  "particleDensity": 80,
  "autoTuneEnabled": true,
  "performanceMode": "balanced",
  "targetFPS": 60,
  "showHUD": true,
  "hudPosition": "TOP_LEFT",
  "fpsWarning": true,
  "fpsWarningThreshold": 30,
  "debugMode": false,
  "dreamMode": false
}
```

---

## 🎮 Performance Modes

| Mode | Render Dist | Entity AI Dist | Particles | Target |
|---|---|---|---|---|
| **Low-End** | 6 chunks | 16 blocks | 30% | Max FPS on 4-core / 4 GB |
| **Balanced** | 10 chunks | 32 blocks | 70% | Smooth 60 FPS on mid-range |
| **Ultra** | 16 chunks | 64 blocks | 100% | 144+ FPS on high-end |
| **Custom** | User-defined | User-defined | User-defined | Manual control |

Switch modes with **K** (configurable) or via the in-game GUI.

---

## 🔬 Auto-Tune Algorithm

```
On world load:
  1. Read CPU cores, RAM, GPU string → classify LOW / MID / HIGH tier
  2. Detect Sodium + Iris presence
  3. If Iris shaders active → reduce render dist by 2, particles by 30%
  4. Apply hardware-suggested preset

Every 5 seconds (100 ticks):
  5. Sample current FPS into a 5-frame rolling average
  6. If avgFPS < target * 0.80 → degrade one setting step:
       particles first → entity AI dist → render distance
  7. If avgFPS > target * 1.20 → restore one setting step (inverse order)
  8. Save config to disk
```

---

## 🛠️ Building from Source

```bash
git clone https://github.com/thanosmod/thanos-gauntlet-fps
cd thanos-gauntlet-fps
./gradlew build
# Output: build/libs/thanos-gauntlet-fps-1.0.0.jar
```

**Requirements:** Java 21, Gradle 8+

---

## 📂 Project Structure

```
src/main/java/com/thanosmod/
├── ThanosGauntletFPS.java          # Common initializer
├── ThanosGauntletFPSClient.java    # Client initializer
├── config/
│   ├── ThanosConfig.java           # Settings POJO
│   └── ConfigManager.java          # JSON save/load + presets
├── modules/
│   ├── RealityStone.java           # Chunk & render
│   ├── PowerStone.java             # Entity AI throttle
│   ├── SpaceStone.java             # Memory management
│   ├── TimeStone.java              # Tick & redstone skip
│   ├── MindStone.java              # Mode manager
│   ├── SoulStone.java              # HUD & warnings
│   └── ChaosStone.java             # Debug & extras
├── mixin/
│   ├── EntityTickMixin.java        # → skip distant mob AI
│   ├── WorldTickMixin.java         # → batch flush + cache prune
│   ├── RedstoneMixin.java          # → skip distant redstone
│   ├── ParticleClientMixin.java    # → particle density gate
│   ├── ClientTickMixin.java        # → apply Reality Stone each tick
│   ├── WorldRendererMixin.java     # → frame-time debug hook
│   ├── ServerChunkManagerMixin.java # → async lighting gate
│   └── GameRendererMixin.java      # → render budget (future)
├── autotune/
│   ├── SystemDetector.java         # CPU / RAM / GPU fingerprint
│   └── AutoTuner.java              # Live FPS → setting adjuster
├── shader/
│   └── ShaderDetector.java         # Sodium + Iris presence check
└── gui/
    ├── ThanosConfigScreen.java     # Cloth Config GUI builder
    └── ThanosModMenuIntegration.java # ModMenu hook
```

---

## 🤝 Compatibility

| Mod | Status |
|---|---|
| Sodium | ✅ Detected, shader budget applied |
| Iris | ✅ Detected, active-shader check via reflection |
| ModMenu | ✅ Config screen registered |
| Cloth Config | ✅ Optional — falls back to JSON without it |
| Lithium | ✅ Compatible (no overlapping mixins) |
| FerriteCore | ✅ Compatible |
| EntityCulling | ✅ Compatible |

---

## 📜 License

MIT — do whatever you want, just don't claim you snapped the gauntlet yourself.

---

*"Fine. I'll do it myself."*
