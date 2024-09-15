cmake_minimum_required(VERSION 3.20)

project(mylib-proj)

add_library(mylib mylib.cpp)

target_include_directories(mylib PUBLIC include)

export(TARGETS mylib FILE mylibTargets.cmake)

set(CMAKE_EXPORT_PACKAGE_REGISTRY ON)
export(PACKAGE mylib)

include(CMakePackageConfigHelpers)
configure_package_config_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/mylibConfig.cmake.in
    ${CMAKE_CURRENT_BINARY_DIR}/mylibConfig.cmake
    INSTALL_DESTINATION ${CMAKE_BINARY_DIR}
)