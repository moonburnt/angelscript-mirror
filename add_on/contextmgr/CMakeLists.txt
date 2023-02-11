cmake_minimum_required(VERSION 3.5)

project(contextmgr)

add_library(contextmgr STATIC
    contextmgr.cpp
    contextmgr.h
)

target_include_directories(contextmgr PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(contextmgr PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


