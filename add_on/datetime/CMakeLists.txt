cmake_minimum_required(VERSION 3.5)

set(ANGELSCRIPT_INCLUDE_DIR
    ${CMAKE_SOURCE_DIR} CACHE STRING
    "Path to the angelscript's 'include' directory"
)

project(datetime)

add_library(datetime STATIC
    datetime.cpp
    datetime.h
)

target_include_directories(datetime PRIVATE
    ${ANGELSCRIPT_INCLUDE_DIR}/include/
)

target_include_directories(datetime PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


