cmake_minimum_required(VERSION 3.20)
project(PIXEL LANGUAGES C CXX)

# ── Global Settings ──────────────────────────────────────────────────────────
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# ── Subdirectories ───────────────────────────────────────────────────────────
add_subdirectory(vendor)
add_subdirectory(src)
add_subdirectory(game)
