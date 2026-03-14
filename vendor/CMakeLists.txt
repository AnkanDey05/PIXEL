# ╔═══════════════════════════════════════════════════════════════════════════╗
# ║  PIXEL Engine — Vendor Dependencies                                      ║
# ╚═══════════════════════════════════════════════════════════════════════════╝

# ── GLAD (OpenGL Loader) ─────────────────────────────────────────────────────
# Expects:  vendor/glad/src/glad.c
#           vendor/glad/include/glad/glad.h
#           vendor/glad/include/KHR/khrplatform.h
add_library(glad STATIC
    glad/src/glad.c
)
target_include_directories(glad PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/glad/include
)

# ── GLFW (Windowing / Input) ─────────────────────────────────────────────────
# Expects the full GLFW source tree cloned into vendor/glfw/
set(GLFW_BUILD_DOCS     OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS    OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(GLFW_INSTALL        OFF CACHE BOOL "" FORCE)
add_subdirectory(glfw)

# ── GLM (Math — header-only) ─────────────────────────────────────────────────
# Expects:  vendor/glm/glm/glm.hpp  (standard GLM layout)
add_library(glm INTERFACE)
target_include_directories(glm INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}/glm
)

# ── miniaudio (Audio — header-only / single-file) ────────────────────────────
# Expects:  vendor/miniaudio/miniaudio.h
add_library(miniaudio INTERFACE)
target_include_directories(miniaudio INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}/miniaudio
)

# ── stb (Image loading — header-only / single-file) ──────────────────────────
# Expects:  vendor/stb/stb_image.h  (and any other stb headers you need)
add_library(stb INTERFACE)
target_include_directories(stb INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}/stb
)
