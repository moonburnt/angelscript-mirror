add_library(scriptarray STATIC
    scriptarray.cpp
    scriptarray.h
)

target_include_directories(scriptarray PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
