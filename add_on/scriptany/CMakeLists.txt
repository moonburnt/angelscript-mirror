cmake_minimum_required(VERSION 3.5)

project(scriptany)

add_library(scriptany STATIC
    scriptany.cpp
    scriptany.h
)

target_include_directories(scriptany PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scriptany PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


