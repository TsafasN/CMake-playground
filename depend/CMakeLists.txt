cmake_minimum_required(VERSION 3.20)

project(mylib-proj)

add_library(mylib mylib.cpp)

target_include_directories(mylib 
    PUBLIC 
    $<INSTALL_INTERFACE:include>
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)

export(TARGETS mylib FILE mylibTargets.cmake)

install(TARGETS mylib EXPORT mylibExportSet)
install(DIRECTORY include/ 
        DESTINATION include
)
install(EXPORT mylibExportSet
        FILE mylibTargets.cmake
        DESTINATION lib/cmake/mylib
)

include(CMakePackageConfigHelpers)
configure_package_config_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/mylibConfig.cmake.in
    ${CMAKE_CURRENT_BINARY_DIR}/mylibConfig.cmake
    INSTALL_DESTINATION ${CMAKE_BINARY_DIR}
)

install(FILES ${CMAKE_CURRENT_BINARY_DIR}/mylibConfig.cmake
        DESTINATION lib/cmake/mylib
)

set(CPACK_GENERATOR "DEB")
set(CPACK_DEBIAN_PACKAGE_DESCRIPTION "My Library")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "ntsafas")
include(CPack)
