# ╔═══════════════════════════════════════════════════════════════════════════╗
# ║  PIXEL Engine — Static Library                                           ║
# ╚═══════════════════════════════════════════════════════════════════════════╝

# Collect every .cpp / .c file under src/ (recursively across all modules)
file(GLOB_RECURSE PIXEL_ENGINE_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/*.c
)

# Collect every header for IDEs (optional but helpful in VS / CLion)
file(GLOB_RECURSE PIXEL_ENGINE_HEADERS
    ${CMAKE_CURRENT_SOURCE_DIR}/*.h
    ${CMAKE_CURRENT_SOURCE_DIR}/*.hpp
    ${PROJECT_SOURCE_DIR}/include/*.h
    ${PROJECT_SOURCE_DIR}/include/*.hpp
)

add_library(PixelEngine STATIC
    ${PIXEL_ENGINE_SOURCES}
    ${PIXEL_ENGINE_HEADERS}
)

# ── Include Paths ─────────────────────────────────────────────────────────────
# PUBLIC  — consumers (game) also get these include paths
# PRIVATE — only the engine itself sees these
target_include_directories(PixelEngine
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include      # engine.h  (public API)
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}        # internal headers within src/
)

# ── Link Vendor Libraries ────────────────────────────────────────────────────
# PUBLIC so the game executable transitively inherits includes & link libs
target_link_libraries(PixelEngine
    PUBLIC
        glad
        glfw
        glm
        miniaudio
        stb
)

# ── Platform-specific Libraries ──────────────────────────────────────────────
if(WIN32)
    target_link_libraries(PixelEngine PUBLIC opengl32)
elseif(UNIX AND NOT APPLE)
    find_package(OpenGL REQUIRED)
    target_link_libraries(PixelEngine PUBLIC OpenGL::GL)
elseif(APPLE)
    find_library(OPENGL_FRAMEWORK OpenGL)
    target_link_libraries(PixelEngine PUBLIC ${OPENGL_FRAMEWORK})
endif()
