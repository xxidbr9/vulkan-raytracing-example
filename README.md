
# Learning Vulkan

# Table of Contents

1. [Introduction](#introduction)
1. [Setup](#setup)
1. [Examples](#examples)
    - [Hello World c++](examples/hello_world/)
    - [Triangle](examples/triangle)
    - [Demo ImGui](examples/hello_imgui)



# Introduction
Vulkan is a low-overhead, cross-platform 3D graphics and computing API. It provides high-efficiency, cross-platform access to modern GPUs used in a wide variety of devices from PCs and consoles to mobile phones and embedded platforms.

# Setup

## Installing Clang/LLVM and Vulkan on Windows

### Clang/LLVM Installation

1. Download the installer from the [official LLVM website](https://releases.llvm.org/download.html).
2. Run the installer and follow the on-screen instructions.
3. Add LLVM to your system PATH:
      - Open the Start Menu and search for "Environment Variables".
      - Click on "Edit the system environment variables".
      - In the System Properties window, click on the "Environment Variables" button.
      - In the Environment Variables window, find the "Path" variable in the "System variables" section and click "Edit".
      - Click "New" and add the path to the LLVM bin directory (e.g., `C:\Program Files\LLVM\bin`).
      - Click "OK" to close all windows.

### Vulkan SDK Installation

1. Download the Vulkan SDK from the [LunarG Vulkan SDK website](https://vulkan.lunarg.com/sdk/home).
2. Run the installer and follow the on-screen instructions.
3. Add Vulkan SDK to your system PATH:
      - Open the Start Menu and search for "Environment Variables".
      - Click on "Edit the system environment variables".
      - In the System Properties window, click on the "Environment Variables" button.
      - In the Environment Variables window, find the "Path" variable in the "System variables" section and click "Edit".
      - Click "New" and add the path to the Vulkan SDK bin directory (e.g., `C:\VulkanSDK\<version>\Bin`).
      - Click "OK" to close all windows.

### Running the Project using CMake

1. Open a terminal (Command Prompt or PowerShell).
1. Navigate to the project directory:
3. Create a build directory and navigate into it:
  ```sh
  mkdir build
  cd build
  ```
4. Run CMake to configure the project:
  ```sh
  cmake ..
  ```
5. Build the project using CMake:
  ```sh
  cmake --build .
  ```
6. Run the executable:
  ```sh
  ./executable/<example_name>.exe
  ```

