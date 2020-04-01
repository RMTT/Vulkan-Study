cmake_minimum_required(VERSION 3.15)
project(VulkanStudy)

set(CMAKE_CXX_STANDARD 17)

set(EXECUTABLE_OUTPUT_PATH output)
set(SUBMODULE_DIR ${PROJECT_SOURCE_DIR}/submodules)

# seek for vulkan
find_package(Vulkan REQUIRED)

# seek for glfw
set(GLFW_DIR ${SUBMODULE_DIR}/glfw)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

add_subdirectory(${GLFW_DIR} ${EXECUTABLE_OUTPUT_PATH}/glfw)

# seek for glm
set(GLM_DIR ${SUBMODULE_DIR}/glm)

add_subdirectory(${GLM_DIR} ${EXECUTABLE_OUTPUT_PATH}/glm)

# add include directories
include_directories(${GLFW_INCLUDE_DIR} ${GLM_INCLUDE_DIR})
include_directories(${GLM_DIR})

add_executable(VulkanStudy src/main.cpp)

target_link_libraries(VulkanStudy glfw Vulkan::Vulkan glm)