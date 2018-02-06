cmake_minimum_required(VERSION 3.9)
project(OpenGL_test)

set(CMAKE_CXX_STANDARD 14)

#use GLFW
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory(dependencies/glfw)

#use GLEW
add_subdirectory(dependencies/glew/build/cmake)

find_library(cocoa_lib Cocoa)
find_library(iokit_lib IOKit)
find_library(opengl_lib OpenGL)

set(frameworks
        ${cocoa_lib}
        ${iokit_lib}
        ${opengl_lib})

add_executable(OpenGL_test main.cpp)
target_link_libraries(OpenGL_test glfw glew ${frameworks})