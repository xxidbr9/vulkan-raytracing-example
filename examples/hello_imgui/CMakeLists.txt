cmake_minimum_required(VERSION 3.15)
project(hello_imgui)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Ensure the imgui and glfw targets are defined in the externals directory
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../../externals externals_build)

# Find Vulkan
find_package(Vulkan REQUIRED)

add_executable(hello_imgui main.cpp)

# Specify output directory
set_target_properties(hello_imgui PROPERTIES
    # RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/exe
    RUNTIME_OUTPUT_DIRECTORY ${EXECUTABLE_DIR}
)

# Link against the existing imgui, glfw, OpenGL, and Vulkan targets
find_package(OpenGL REQUIRED)
target_link_libraries(hello_imgui PRIVATE imgui glfw OpenGL::GL Vulkan::Vulkan)

# Include directories for the hello_imgui target
target_include_directories(hello_imgui PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/../../externals/imgui)
target_include_directories(hello_imgui PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/../../externals/imgui/backends)
target_include_directories(hello_imgui PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/../../externals/glfw/include)
target_include_directories(hello_imgui PRIVATE ${Vulkan_INCLUDE_DIRS})
