# Set the path to the glm package configuration file
set(glm_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../../externals/glm/cmake)

find_package(Vulkan REQUIRED)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../../externals externals_build)

add_executable(triangle triangle.cpp)

set_target_properties(triangle PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${EXECUTABLE_DIR}
)

# Determine the build type directory
if(CMAKE_BUILD_TYPE STREQUAL "Release")
    set(BUILD_TYPE_DIR "Release")
else()
    set(BUILD_TYPE_DIR "Debug")
endif()

file(GLOB SHADERS "${CMAKE_CURRENT_SOURCE_DIR}/shader/*.vert" "${CMAKE_CURRENT_SOURCE_DIR}/shader/*.frag")
foreach(SHADER ${SHADERS})
    get_filename_component(FILE_NAME ${SHADER} NAME)
    add_custom_command(
        OUTPUT ${EXECUTABLE_DIR}/${BUILD_TYPE_DIR}/shader/${FILE_NAME}.spv
        COMMAND glslc ${SHADER} -o ${EXECUTABLE_DIR}/${BUILD_TYPE_DIR}/shader/${FILE_NAME}.spv
        DEPENDS ${SHADER}
    )
    list(APPEND SPIRV_SHADERS ${EXECUTABLE_DIR}/${BUILD_TYPE_DIR}/shader/${FILE_NAME}.spv)
endforeach()

add_custom_target(compile_shaders ALL DEPENDS ${SPIRV_SHADERS})
add_dependencies(triangle compile_shaders)

target_link_libraries(triangle PRIVATE imgui glfw glm::glm Vulkan::Vulkan)
target_include_directories(triangle PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/../../externals/imgui)
target_include_directories(triangle PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/../../externals/imgui/backends)
target_include_directories(triangle PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/../../externals/glfw/include)
target_include_directories(triangle PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/../../externals/glm)
target_include_directories(triangle PRIVATE ${Vulkan_INCLUDE_DIRS})
