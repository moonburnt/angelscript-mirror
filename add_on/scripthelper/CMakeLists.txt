cmake_minimum_required(VERSION 3.5)

project(scripthelper)

add_library(scripthelper STATIC
    scripthelper.cpp
    scripthelper.h
)

target_include_directories(scripthelper PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scripthelper PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


