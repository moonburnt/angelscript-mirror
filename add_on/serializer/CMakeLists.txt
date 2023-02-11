cmake_minimum_required(VERSION 3.5)

project(serializer)

add_library(serializer STATIC
    serializer.cpp
    serializer.h
)

target_include_directories(serializer PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(serializer PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


