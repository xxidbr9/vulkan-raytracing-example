# examples/hello_world/CMakeLists.txt
# Define the target
add_executable(hello_world main.cpp)

# Specify output directory
set_target_properties(hello_world PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/hello_world
)

# Include directories (if needed for third_party dependencies)
include_directories(${CMAKE_SOURCE_DIR}/third_party)
