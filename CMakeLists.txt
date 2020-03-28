cmake_minimum_required(VERSION 3.15)
project(VulkanStudy)

set(CMAKE_CXX_STANDARD 14)

set(EXECUTABLE_OUTPUT_PATH ouput)

# seek for vulkan
find_package(Vulkan REQUIRED)

# seek for glfw
# version: 3.3.32
set(GLFW_DIR C:/Users/drong/Tools/glfw-3.3.2)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

add_subdirectory(${GLFW_DIR} ${EXECUTABLE_OUTPUT_PATH}/glfw)

# seek for glm
# version: 0.9.9.7
set(GLM_DIR C:/Users/drong/Tools/glm)

add_subdirectory(${GLM_DIR} ${EXECUTABLE_OUTPUT_PATH}/glm)

# add include directories
include_directories(${GLFW_INCLUDE_DIR} ${GLM_INCLUDE_DIR})
include_directories(${GLM_DIR})

add_executable(VulkanStudy src/main.cpp)

target_link_libraries(VulkanStudy glfw Vulkan::Vulkan glm::glm)