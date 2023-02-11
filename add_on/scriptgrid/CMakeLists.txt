cmake_minimum_required(VERSION 3.5)

project(scriptgrid)

add_library(scriptgrid STATIC
    scriptgrid.cpp
    scriptgrid.h
)

target_include_directories(scriptgrid PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scriptgrid PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


