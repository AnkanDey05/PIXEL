# ╔═══════════════════════════════════════════════════════════════════════════╗
# ║  PIXEL Game — Executable                                                 ║
# ╚═══════════════════════════════════════════════════════════════════════════╝

# Collect all game source files (main.cpp, entities/, scenes/, etc.)
file(GLOB_RECURSE PIXEL_GAME_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/*.c
)

add_executable(PixelGame ${PIXEL_GAME_SOURCES})

# Link the engine — this transitively brings in all vendor libs + includes
target_link_libraries(PixelGame PRIVATE PixelEngine)

# Set the working directory to the assets folder for convenient loading
set_target_properties(PixelGame PROPERTIES
    VS_DEBUGGER_WORKING_DIRECTORY "${PROJECT_SOURCE_DIR}/assets"
    RUNTIME_OUTPUT_DIRECTORY      "${CMAKE_BINARY_DIR}/bin"
)
