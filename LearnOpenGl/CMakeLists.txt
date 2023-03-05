cmake_minimum_required(VERSION 3.22)
project(LearnOpenGl)

set(CMAKE_CXX_STANDARD 23)

add_executable(LearnOpenGl main.cpp)

set(GLFW_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libraries/glfw/include)
set(GLEW_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libraries/glew/include)
set(GLAD_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libraries/glad/include)

include_directories(
        ${GLFW_INCLUDE_DIR}
        ${GLEW_INCLUDE_DIR}
        ${GLAD_INCLUDE_DIR}

)

find_package(OpenGL REQUIRED)

add_library(glad ${CMAKE_CURRENT_SOURCE_DIR}/libraries/glad/src/glad.c)
target_include_directories(glad PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/libraries/glad/include)


target_link_libraries(${CMAKE_PROJECT_NAME}
        OpenGL::GL
        OpenGL::GLU
        ${CMAKE_CURRENT_SOURCE_DIR}/libraries/glfw/lib/glfw3.lib
        ${CMAKE_CURRENT_SOURCE_DIR}/libraries/glew/lib/glew32.lib
        glad
        )
