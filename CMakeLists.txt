cmake_minimum_required(VERSION 3.26)
project(ejemplocu03 CUDA)

set(CMAKE_CUDA_STANDARD 17)
enable_language(CXX CUDA)

find_package(fmt)
find_package(SFML)

add_executable(ejemplocu03
        main.cpp
        glad.cpp
        kernel.cu)

target_include_directories(ejemplocu03
        PRIVATE
        ${CMAKE_CUDA_TOOLKIT_INCLUDE_DIRECTORIES}
)

target_link_libraries(
        ejemplocu03 fmt::fmt sfml::sfml
        ${CUDART_LIBRARY}
)

set_target_properties(ejemplocu03 PROPERTIES
        CUDA_SEPARABLE_COMPILATION ON)
