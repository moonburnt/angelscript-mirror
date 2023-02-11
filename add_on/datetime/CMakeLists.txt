cmake_minimum_required(VERSION 3.5)

project(datetime)

add_library(datetime STATIC
    datetime.cpp
    datetime.h
)

target_include_directories(datetime PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(datetime PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


