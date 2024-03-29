cmake_minimum_required(VERSION 3.15)
project(Basic_Tests)

set(CMAKE_CXX_STANDARD 17)

# Find Vulkan
find_package(Vulkan REQUIRED)

# Find GLFW
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

add_subdirectory(libs/glfw)

# Find spdlog
add_subdirectory(libs/spdlog)

# Find Boost
find_package(Boost 1.66 REQUIRED COMPONENTS system container)

# Find GLM
include_directories(libs/glm)

add_executable(Basic_Tests src/main.cpp)

target_link_libraries(Basic_Tests PUBLIC Vulkan::Vulkan)
target_link_libraries(Basic_Tests PUBLIC glfw)
target_link_libraries(Basic_Tests PRIVATE spdlog::spdlog)
