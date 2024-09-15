cmake_minimum_required(VERSION 3.20)

project(mylib-proj)

add_library(mylib mylib.cpp)

target_include_directories(mylib PUBLIC include)

export(TARGETS mylib FILE mylibTargets.cmake)
