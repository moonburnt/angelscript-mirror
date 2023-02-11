cmake_minimum_required(VERSION 3.5)

project(scripthandle)

add_library(scripthandle STATIC
    scripthandle.cpp
    scripthandle.h
)

target_include_directories(scripthandle PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scripthandle PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


