cmake_minimum_required(VERSION 3.5)

project(weakref)

add_library(weakref STATIC
    weakref.cpp
    weakref.h
)

target_include_directories(weakref PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(weakref PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


