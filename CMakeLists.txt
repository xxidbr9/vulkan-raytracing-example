# CMakeLists.txt in the root folder
cmake_minimum_required(VERSION 3.15)
project(VulkanLearn)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Define the hello_world example
add_subdirectory(examples/hello_world)
