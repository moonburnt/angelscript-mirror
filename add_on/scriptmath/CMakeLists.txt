cmake_minimum_required(VERSION 3.5)

project(scriptmath)

add_library(scriptmath STATIC
    scriptmath.cpp
    scriptmath.h
    scriptmathcomplex.cpp
    scriptmathcomplex.h
)

target_include_directories(scriptmath PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scriptmath PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


