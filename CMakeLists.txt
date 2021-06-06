cmake_minimum_required(VERSION 3.0.0)
project(GLSL-Practice VERSION 0.1.0)

# Use C++ 11
set(CMAKE_CXX_STANDARD 11)

# Headers
set(GLAD_H ${PROJECT_SOURCE_DIR}/include)
set(GLFW_H /usr/local/include)
include_directories(${GLAD_H} ${GLFW_H})

# Library Link
set(GLFW_LIB /usr/local/lib/libglfw.3.dylib)
link_libraries(${GLFW_LIB})

# Compile
set(SOURCES src/glad.c main.cpp)
add_executable(GLSL-Practice ${SOURCES})

# Link System OpenGL framework
if (APPLE)
  target_link_libraries(GLSL-Practice "-framework OpenGL")
endif()

# Include Test
include(CTest)
enable_testing()

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
