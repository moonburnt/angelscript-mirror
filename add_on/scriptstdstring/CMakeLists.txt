cmake_minimum_required(VERSION 3.5)

project(scriptstdstring)

add_library(scriptstdstring STATIC
    scriptstdstring_utils.cpp
    scriptstdstring.cpp
    scriptstdstring.h
)

target_include_directories(scriptstdstring PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scriptstdstring PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


