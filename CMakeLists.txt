cmake_minimum_required(VERSION 3.15)
project(imgui_sdl2_sdlrenderer2)

set(IMGUI_DIR "${PROJECT_SOURCE_DIR}") # Set the relative path to imgui directory
message("IMGUI_DIR = ${IMGUI_DIR}")

set(SRC
    ${IMGUI_DIR}/imgui.cpp 
    ${IMGUI_DIR}/imgui_demo.cpp 
    ${IMGUI_DIR}/imgui_draw.cpp 
    ${IMGUI_DIR}/imgui_tables.cpp 
    ${IMGUI_DIR}/imgui_widgets.cpp
    ${IMGUI_DIR}/backends/imgui_impl_sdl2.cpp 
    ${IMGUI_DIR}/backends/imgui_impl_sdlrenderer2.cpp
)

add_library(${PROJECT_NAME} STATIC ${SRC})

target_include_directories(
    ${PROJECT_NAME}
    PUBLIC
    ${IMGUI_DIR}
    PUBLIC
    ${IMGUI_DIR}/backends
)


find_package(SDL2 REQUIRED)
target_link_libraries(${PROJECT_NAME} PRIVATE SDL2::SDL2)