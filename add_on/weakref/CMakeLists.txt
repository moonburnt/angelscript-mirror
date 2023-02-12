add_library(weakref STATIC
    weakref.cpp
    weakref.h
)

target_include_directories(weakref PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
