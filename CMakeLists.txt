cmake_minimum_required(VERSION 3.10)
project(OpenGLApp)

set(CMAKE_CXX_STANDARD 17)

# Find OpenGL and GLFW
find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED PATHS /opt/homebrew/opt/glfw)

# GLAD
add_library(glad src/glad/src/glad.c)
target_include_directories(glad PUBLIC src/glad/include)

# Main executable
add_executable(OpenGLApp src/main.cpp)
target_include_directories(OpenGLApp PRIVATE src/glad/include)

# Link everything
target_link_libraries(OpenGLApp PRIVATE glad glfw OpenGL::GL)