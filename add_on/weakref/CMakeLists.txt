cmake_minimum_required(VERSION 3.5)

set(ANGELSCRIPT_INCLUDE_DIR
    ${CMAKE_SOURCE_DIR} CACHE STRING
    "Path to the angelscript's 'include' directory"
)

project(weakref)

add_library(weakref STATIC
    weakref.cpp
    weakref.h
)

target_include_directories(weakref PRIVATE
    ${ANGELSCRIPT_INCLUDE_DIR}/include/
)

target_include_directories(weakref PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


