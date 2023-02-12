cmake_minimum_required(VERSION 3.5)

set(ANGELSCRIPT_INCLUDE_DIR
    ${CMAKE_SOURCE_DIR} CACHE STRING
    "Path to the angelscript's 'include' directory"
)

project(scriptfile)

add_library(scriptfile STATIC
    scriptfile.cpp
    scriptfile.h
    scriptfilesystem.cpp
    scriptfilesystem.h
)

target_include_directories(scriptfile PRIVATE
    ${ANGELSCRIPT_INCLUDE_DIR}/include/
)

target_include_directories(scriptfile PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


