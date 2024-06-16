cmake_minimum_required(VERSION 3.10)

project(ChitraGL)

set(CMAKE_CXX_STANDARD 17)

# Specify the path to GLFW
# set(CMAKE_PREFIX_PATH "/usr/local/lib/cmake/glfw3")
set(CMAKE_PREFIX_PATH "/opt/homebrew/lib/cmake/glfw3")

# Add GLFW
find_package(glfw3 CONFIG REQUIRED)

# Add GLAD
add_library(glad src/glad.c)
target_include_directories(glad PRIVATE include)

# Explicitly list source files
set(SOURCES src/main.cpp)

# Add source files
# file(GLOB_RECURSE SOURCE "src/*.cpp")
# file(GLOB_RECURSE HEADERS "include/*.h")

add_executable(ChitraGL ${SOURCES})

target_include_directories(ChitraGL PRIVATE include)

# Link GLFW and GLAD
target_link_libraries(ChitraGL glfw glad "-framework OpenGL")
