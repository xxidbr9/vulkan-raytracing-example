# examples/hello_world/CMakeLists.txt
# Define the target
add_executable(hello_world main.cpp)

# Specify output directory
set_target_properties(hello_world PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${EXECUTABLE_DIR}
    
    # ignore Debug and Release subdirectories
    # RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/exe
    # # merge the pdb with the exe file
    # RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/exe
)

# Include directories (if needed for third_party dependencies)
include_directories(${CMAKE_SOURCE_DIR}/externals)
