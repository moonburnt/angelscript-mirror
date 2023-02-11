cmake_minimum_required(VERSION 3.5)

project(debugger)

add_library(debugger STATIC
    debugger.cpp
    debugger.h
)

target_include_directories(debugger PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(debugger PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


