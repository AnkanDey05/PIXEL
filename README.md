<p align="center">
  <h1 align="center">🎮 PIXEL Engine</h1>
  <p align="center">
    **A lightweight 2D game engine built from scratch in C++ with OpenGL**
    <br/>
    <img src="https://img.shields.io/badge/status-Work%20In%20Progress-orange?style=for-the-badge" alt="Status: WIP"/>
    <img src="https://img.shields.io/badge/c%2B%2B-17-blue?style=for-the-badge&logo=cplusplus" alt="C++17"/>
    <img src="https://img.shields.io/badge/OpenGL-3.3-green?style=for-the-badge&logo=opengl" alt="OpenGL 3.3"/>
    <img src="https://img.shields.io/badge/build-CMake-red?style=for-the-badge&logo=cmake" alt="CMake"/>
  </p>
</p>

---

> ⚠️ **This project is currently under active development.** Features, APIs, and architecture are subject to change.

## 🏗️ Architecture

```
PIXEL/
├── include/            # Public engine API (engine.h)
├── src/                # Engine source code
│   ├── core/           # Engine core (window, app lifecycle)
│   ├── renderer/       # OpenGL rendering pipeline
│   ├── ecs/            # Entity Component System
│   ├── physics/        # Physics & collision
│   ├── audio/          # Audio playback (miniaudio)
│   ├── lighting/       # 2D lighting system
│   ├── events/         # Event dispatcher
│   ├── debug/          # Debug tools & logging
│   └── assets/         # Asset loading & management
├── game/               # Game executable (user code)
│   ├── main.cpp
│   ├── entities/
│   └── scenes/
├── vendor/             # Third-party dependencies
│   ├── glad/           # OpenGL loader
│   ├── glfw/           # Windowing & input
│   ├── glm/            # Math library
│   ├── miniaudio/      # Audio library
│   └── stb/            # Image loading
└── assets/             # Game assets
    ├── shaders/
    ├── textures/
    ├── fonts/
    └── audio/
```

## 🛠️ Tech Stack

| Library | Purpose |
|---------|---------|
| **GLFW** | Window creation, input handling, OpenGL context |
| **GLAD** | OpenGL 3.3 Core function loader |
| **GLM** | Mathematics (vectors, matrices, transforms) |
| **miniaudio** | Cross-platform audio playback |
| **stb_image** | Image loading (PNG, JPG, BMP) |

## 📦 Prerequisites

- **C++ Compiler**: GCC (MinGW-w64 recommended on Windows)
- **CMake**: Version 3.20 or higher
- **Git**: For cloning the repository

## 🚀 Building

### Clone
```bash
git clone https://github.com/YOUR_USERNAME/PIXEL.git
cd PIXEL
```

### Configure (first time only)
```bash
cmake -S . -B build -G "MinGW Makefiles" \
  -DCMAKE_C_COMPILER=gcc \
  -DCMAKE_CXX_COMPILER=g++
```

### Build
```bash
cmake --build build
```

### Run
```bash
./build/bin/PixelGame.exe
```

> 💡 You only need to run the configure step once. After that, just use `cmake --build build` — it will detect changed files and recompile only what's needed.


## 📄 License

This project is currently unlicensed. A license will be added as the project matures.
