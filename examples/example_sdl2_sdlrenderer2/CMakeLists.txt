cmake_minimum_required(VERSION 3.15)
project(example_sdl2_sdlrenderer2)

set(CMAKE_CXX_STANDARD 20) # Set C++ standard to C++20
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(IMGUI_DIR "../..") # Set the relative path to imgui directory

set(SOURCES 
    main.cpp
    ${IMGUI_DIR}/imgui.cpp 
    ${IMGUI_DIR}/imgui_demo.cpp 
    ${IMGUI_DIR}/imgui_draw.cpp 
    ${IMGUI_DIR}/imgui_tables.cpp 
    ${IMGUI_DIR}/imgui_widgets.cpp
    ${IMGUI_DIR}/backends/imgui_impl_sdl2.cpp 
    ${IMGUI_DIR}/backends/imgui_impl_sdlrenderer2.cpp
)

include_directories(
    ${IMGUI_DIR}
    ${IMGUI_DIR}/backends
)

add_executable(example_sdl2_sdlrenderer2 ${SOURCES})

# I only work on OS X and Windows
if(APPLE)
    find_package(SDL2 REQUIRED)
    target_link_libraries(example_sdl2_sdlrenderer2 ${SDL2_LIBRARIES})
endif(APPLE)


# Not tested yet
if(WIN32)
    target_link_libraries(example_sdl2_sdlrenderer2 gdi32 opengl32 imm32)
    find_package(SDL2 REQUIRED)
    target_link_libraries(example_sdl2_sdlrenderer2 ${SDL2_LIBRARIES})
endif(WIN32)
