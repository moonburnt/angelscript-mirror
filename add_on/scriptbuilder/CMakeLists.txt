cmake_minimum_required(VERSION 3.5)

project(scriptbuilder)

add_library(scriptbuilder STATIC
    scriptbuilder.cpp
    scriptbuilder.h
)

target_include_directories(scriptbuilder PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scriptbuilder PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


