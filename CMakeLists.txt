# CMakeLists.txt in the root folder
cmake_minimum_required(VERSION 3.15)
project(VulkanLearn)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# External
add_subdirectory(externals)

# Define the hello_world example
set(EXECUTABLE_DIR ${CMAKE_BINARY_DIR}/executable)
add_subdirectory(examples/hello_world)
add_subdirectory(examples/hello_imgui)
add_subdirectory(examples/triangle)

