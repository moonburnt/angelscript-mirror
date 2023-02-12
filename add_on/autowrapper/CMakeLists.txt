cmake_minimum_required(VERSION 3.5)

set(ANGELSCRIPT_INCLUDE_DIR
    ${CMAKE_SOURCE_DIR} CACHE STRING
    "Path to the angelscript's 'include' directory"
)

project(autowrapper)

add_library(autowrapper STATIC
    # I assume, this generator is meant to be built separately
    # generator/generateheader.cpp
    aswrappedcall.h
)

set_target_properties(autowrapper PROPERTIES LINKER_LANGUAGE CXX)

target_include_directories(autowrapper PRIVATE
    ${ANGELSCRIPT_INCLUDE_DIR}/include/
)

target_include_directories(autowrapper PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


