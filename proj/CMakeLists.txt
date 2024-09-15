cmake_minimum_required(VERSION 3.20)
project(myprog)

find_package(mylib REQUIRED)

add_executable(main main.cpp)

target_link_libraries(main PRIVATE mylib)
