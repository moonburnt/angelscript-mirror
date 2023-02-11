cmake_minimum_required(VERSION 3.5)

project(scriptfile)

add_library(scriptfile STATIC
    scriptfile.cpp
    scriptfile.h
    scriptfilesystem.cpp
    scriptfilesystem.h
)

target_include_directories(scriptfile PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scriptfile PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


