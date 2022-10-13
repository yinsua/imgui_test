cmake_minimum_required(VERSION 3.22)
project(imgui_test)

set(CMAKE_CXX_STANDARD 20)

include_directories(imgui)
include_directories(${PROJECT_SOURCE_DIR})

# 包含了什么头文件，这里就应该添加相应的cpp文件，否则报错找不到函数定义
file(GLOB SOURCE
        imgui/*.cpp
        imgui/*.h
        imgui/backends/imgui_impl_glfw.*
        imgui/backends/imgui_impl_opengl3.*
        imgui/backends/imgui_impl_win32.*)

# glfw
set(glfw3_DIR "C:\\Program Files (x86)\\GLFW\\lib\\cmake\\glfw3")
find_package(glfw3 REQUIRED)
include_directories(${GLFW_INCLUDE_DIRS})
link_libraries(${GLFW_LIBRARY_DIRS})

# opengl
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

# glew
set(glew_DIR "C:\\Program Files (x86)\\glew\\lib\\cmake\\glew")
find_package(GLEW REQUIRED)
include_directories(${GLEW_INCLUDE_DIRS})

add_executable(imgui_test main.cpp ${SOURCE})
target_link_libraries(imgui_test
        glfw
        ${OPENGL_LIBRARIES}
        GLEW::GLEW )