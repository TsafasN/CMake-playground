cmake_minimum_required(VERSION 3.20)

project(mylib-proj)

add_library(mylib mylib.cpp)

target_include_directories(mylib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

export(TARGETS mylib FILE mylibTargets.cmake)
