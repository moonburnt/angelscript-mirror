cmake_minimum_required(VERSION 3.5)

project(scriptarray)

add_library(scriptarray STATIC
    scriptarray.cpp
    scriptarray.h
)

target_include_directories(scriptarray PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scriptarray PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


