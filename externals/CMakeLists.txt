# Add Vulkan library
find_package(Vulkan REQUIRED)

# Check if the imgui target already exists
if (NOT TARGET imgui)
  add_library(imgui
    imgui/imgui.cpp
    imgui/imgui_demo.cpp
    imgui/imgui_draw.cpp
    imgui/imgui_tables.cpp
    imgui/imgui_widgets.cpp
    imgui/backends/imgui_impl_glfw.cpp
    imgui/backends/imgui_impl_vulkan.cpp
  )
  target_include_directories(imgui PUBLIC
    "${CMAKE_CURRENT_LIST_DIR}/imgui"
    "${CMAKE_CURRENT_LIST_DIR}/imgui/backends"
    "${CMAKE_CURRENT_LIST_DIR}/glfw/include"
    "${Vulkan_INCLUDE_DIRS}"
  )
endif()

# Add glfw library
if (NOT TARGET glfw)
  add_subdirectory(glfw)
endif()
