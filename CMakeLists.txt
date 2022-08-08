cmake_minimum_required(VERSION 3.16)

project(imgui)

set(CMAKE_CXX_STANDARD 17)

find_package(PkgConfig REQUIRED)
find_package(OpenGL REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)

add_library(imgui STATIC
    imgui.cpp
    imgui_demo.cpp
    imgui_draw.cpp
    
    imgui_tables.cpp
    imgui_widgets.cpp

    backends/imgui_impl_glfw.cpp
    backends/imgui_impl_opengl3.cpp
)

add_compile_definitions(IMGUI_IMPL_OPENGL_LOADER_GLAD)


target_include_directories(imgui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/backends ${GLFW_INCLUDE_DIRS})

target_link_directories(imgui PUBLIC ${GLFW_LIBRARY_DIRS})

target_link_libraries(imgui PUBLIC glfw3 opengl32.lib)
