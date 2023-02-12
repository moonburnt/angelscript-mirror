cmake_minimum_required(VERSION 3.5)

set(ANGELSCRIPT_INCLUDE_DIR
    ${CMAKE_SOURCE_DIR} CACHE STRING
    "Path to the angelscript's 'include' directory"
)

project(debugger)

add_library(debugger STATIC
    debugger.cpp
    debugger.h
)

target_include_directories(debugger PRIVATE
    ${ANGELSCRIPT_INCLUDE_DIR}/include/
)

target_include_directories(debugger PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


