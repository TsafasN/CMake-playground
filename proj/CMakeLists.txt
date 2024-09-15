cmake_minimum_required(VERSION 3.20)
project(myprog)

include(/home/ntsafas/wd/cmake_ws/cmake-depends/depend/build/mylibTargets.cmake)

add_executable(main main.cpp)

target_link_libraries(main PRIVATE mylib)
