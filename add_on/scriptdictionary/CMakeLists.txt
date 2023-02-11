cmake_minimum_required(VERSION 3.5)

project(scriptdictionary)

add_library(scriptdictionary STATIC
    scriptdictionary.cpp
    scriptdictionary.h
)

target_include_directories(scriptdictionary PRIVATE
    ${CMAKE_SOURCE_DIR}/include/
)

target_include_directories(scriptdictionary PUBLIC
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>"
    "$<INSTALL_INTERFACE:${PROJECT_SOURCE_DIR}>"
)


