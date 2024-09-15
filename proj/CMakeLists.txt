cmake_minimum_required(VERSION 3.20)
project(myprog)

include(${PATH_TO_MYLIB_TARGETS}/mylibTargets.cmake)

add_executable(main main.cpp)

target_link_libraries(main PRIVATE mylib)
