cmake_minimum_required(VERSION 3.5)

set(ANGELSCRIPT_INCLUDE_DIR
    ${CMAKE_SOURCE_DIR} CACHE STRING
    "Path to the angelscript's 'include' directory"
)

project(scripthandle)

add_library(scripthandle STATIC
    scripthandle.cpp
    scripthandle.h
)

target_include_directories(scripthandle PRIVATE
    ${ANGELSCRIPT_INCLUDE_DIR}/include/
)

target_include_directories(scripthandle PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


